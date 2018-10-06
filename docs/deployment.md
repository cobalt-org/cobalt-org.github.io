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
    --tag v0.13.0
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
- `local_dir`: update it according to your [`destination`](/docs/config.html)
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

This example `.gitlab-ci.yml` downloads a cobalt release from github, decompresses
the program, and runs it:

```yml
image: debian:latest

variables:
  COBALT_VERSION: "v0.13.2"
pages:
  script:
  - apt-get update && apt-get -y install wget tar
  - wget https://github.com/cobalt-org/cobalt.rs/releases/download/$COBALT_VERSION/cobalt-$COBALT_VERSION-x86_64-unknown-linux-gnu.tar.gz
  - tar -xf cobalt-$COBALT_VERSION-x86_64-unknown-linux-gnu.tar.gz
  - mkdir -p public
  - ./cobalt build -d public
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

