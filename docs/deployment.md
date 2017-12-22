extends: docs.liquid
title: "Cobalt::Docs::Deployment"
route: deployment
---
## Deployment

### Import

To import your site to your `gh-pages` branch you can either
pass a `build --import` flag when you build the site or after
you have build the site with `build` you can run
`import`. There are also some flags that can be found via
`import --help`.

### TravisCI

#### Project Site

You can easily deploy a cobalt site to `gh-pages`! To do
this with travis is also very easy. You will need to have rust available
on travis. In your `travis.yml` you will need to have something
similar to this:

```yml
sudo: false
before_script:
  - curl -LSfs https://japaric.github.io/trust/install.sh | sh -s -- --git cobalt-org/cobalt.rs --crate cobalt --force --target x86_64-unknown-linux-gnu
  - export PATH="$PATH:~/.cargo/bin"
script:
  - cobalt build

deploy:
  provider: pages
  skip_cleanup: true
  github_token: $GH_TOKEN
  local_dir: build
  on:
    branch: master
```

For the `GH_TOKEN` you will need to create a personal access
token, which can be found [here](https://github.com/settings/tokens), then you will need
to use the [travis cli tool](https://github.com/travis-ci/travis.rb#the-travis-client-) to
encrypt your personal access token. You can do this like so `travis encrypt GH_TOKEN=... --add env.global`

#### Personal or Organization Site

The main difference with a personal site is that github only allows
the `master` branch to serve the pages.  Instead, you could
keep your source in another branch, like `source` and have
cobalt import your site into the `master` branch.

### GitLab CI

You can also deploy a cobalt site to [Gitlab Pages](http://pages.gitlab.io/)
using GitLab CI.  GitLab CI uses [Docker](https://docs.docker.com), you can use
[nott/cobalt](https://hub.docker.com/r/nott/cobalt/) or any other image with
`cobalt` in `PATH`.

An example of `.gitlab-ci.yml`:

```yml
image: nott/cobalt:latest

pages:
  script:
  - mkdir -p public
  - cobalt build -d public
  artifacts:
    paths:
    - public/
  only:
  - master
```
