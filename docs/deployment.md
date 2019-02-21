---
title: "Docs::Deployment"
layout: docs.liquid
data:
  route: deployment
---
## Deployment

### TravisCI

#### Project Site

You can easily deploy a cobalt site to `gh-pages`! To do this with travis is
also very easy.

1. Create your `.travis.yml` file:

```yml
sudo: false
before_script:
  - curl -LSfs https://japaric.github.io/trust/install.sh |
    sh -s --
    --git cobalt-org/cobalt.rs
    --crate cobalt
    --force
    --target x86_64-unknown-linux-gnu
    --tag v0.15.0
  - export PATH="$PATH:~/.cargo/bin"
script:
  - cobalt build

deploy:
  provider: pages
  skip_cleanup: true
  github_token: $GH_TOKEN
  local_dir: _site
  target_branch: master
  on:
    branch: source
```

- `--tag`: update to reflect the desired version of cobalt.
- `local_dir`: update it according to your [`destination`](/docs/config)
- `target_branch`: Update to reflect the branch that you configured as the source for [Github Pages](https://pages.github.com/).
- `on: branch`: Update to reflect the branch your source is kept in.

2. Configure your `GH_TOKEN`

This is a limited access API token for Travis to commit to your page's github repo.  You can create one [here](https://github.com/settings/tokens).

To add it to your `.travis.yml` file, you will need to use the [travis cli
tool](https://github.com/travis-ci/travis.rb#the-travis-client-).  This will
encrypt the token specifically to your repo and branch.

Example:
`travis encrypt GH_TOKEN=... --add env.global`

#### Personal or Organization Site

The main difference with a personal site is that github only allows
the `master` branch to serve the pages.  Instead, you could
keep your source in another branch, like `source` and have
cobalt import your site into the `master` branch.

### GitLab CI

You can also deploy a cobalt site to [Gitlab Pages](http://pages.gitlab.io/)
using GitLab CI.  GitLab CI uses [Docker](https://docs.docker.com), so there
are many ways to accomplish building your cobalt site.

This example `.gitlab-ci.yml` installs and runs cobalt:

```yml
image: debian:latest

variables:
  COBALT_VERSION: "v0.15.0"
pages:
  script:
  - apt-get update && apt-get -y install curl
  - curl -LSfs https://japaric.github.io/trust/install.sh |
    sh -s --
    --git cobalt-org/cobalt.rs
    --crate cobalt
    --force
    --target x86_64-unknown-linux-gnu
    --tag $COBALT_VERSION
  - export PATH="$PATH:~/.cargo/bin"
  - mkdir -p public
  - cobalt build -d public
  artifacts:
    paths:
    - public/
  only:
  - master
```

### Other

To import your site to your `gh-pages` branch you can either
pass a `build --import` flag when you build the site or after
you have build the site with `build` you can run
`import`. There are also some flags that can be found via
`import --help`.

### Self-hosted

If you host your site yourself, for example on a virtual private
server, here are some ideas on how to deploy.

#### Simple uploading

You can use tools such as
[`rsync`](https://en.wikipedia.org/wiki/Rsync/), or other file
synchronization tools to upload your rendered site to a web
server. For example (note that this will delete all extraneous files
on your server):

```
$ rsync --delete -a _site/ YOUR-SERVER:public_html/
```

#### Publishing with git

Note that this section assumes familiarity with
[git](https://git-scm.com/), so if you are not familiar with git, feel
free to ignore it, or take the time to make yourself familiar. It
further assumes you already keep your cobalt project in git, as well
as basic familiarity with Unix-like systems.

Instead of just copying the locally rendered site to your web server,
you can install cobalt and git on the web server, and publish via
pushing to a git repository. This is advantageous especially in a
multi-user setting, where multiple users (or maybe just yourself using
different machines) are maintaining the same site, as git will prevent
users from overwriting each other's changes. Conflicts will have to be
resolved locally by git rebasing and/or merging.

To set this up, you will need to have both cobalt and git installed on
your server. Then, create a bare repository on your server and
configure it as a remote in your local cobalt repository to be able to
push to it. Once that is done, you can set up a `post-update` hook on
the server's git repository to render your site. To make that process
reliable in case cobalt fails to render your site, you can use the
[`cobalt-git-deploy`](https://github.com/cobalt-org/cobalt.rs/blob/master/contrib/cobalt-git-deploy)
script. To learn more about `cobalt-git-deploy`, call it with the
`--help` option. Specifically, you should make sure that the
directories it is invoked with from the git hook are not already
existing.

Assuming you have installed `cobalt-git-deploy` somewhere in your
`PATH`, create a `post-update` hook on the server's git repository
that looks something like this:

```
$ cat homepage.git/hooks/post-update
#!/bin/sh

PATH="$HOME/bin:/usr/local/bin:/usr/bin:/bin"
export PATH

exec cobalt-git-deploy ~/cobalt-stage ~/public_html
```

Make sure that your hook is executable. Now pushing to the repository
should show status information from the hook, e.g.:

```
$ git push
No previous state saved. First run?
Checking out master to /home/foo/cobalt-stage/left
Already on 'master'
HEAD is now at 9ef95c1 New exciting blog post
Building site
[info] Building from "/home/foo/cobalt-stage/left/" into "/home/foo/cobalt-stage/left/_site"
[info] Build successful
Deploying site in /home/foo/public_html
```

You can now enjoy publishing using `git commit` and `git push`!
