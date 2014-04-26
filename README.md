daily-travis
============

A dead simple heroku ready travis daily sceduler

Usage
=====

* Clone this repo locally

```shell
git clone https://github.com/philou/daily-travis.git
```

* If you don't have it yet, install the [heroku toolbelt](https://devcenter.heroku.com/articles/quickstart)

* Create an heroku app to deploy to

```shell
heroku apps:create <my-lib>-daily-travis
```

* Deploy to heroku

```shell
git push heroku master
```

* Generate a github token

Explanations are [here](https://help.github.com/articles/creating-an-access-token-for-command-line-use). Default authorizations are fine.
Note the token somewhere.

* Add the parameters to your heroku app

```shell
heroku config:add TRAVIS_REPOSITORY=<github-user>/<github-repo>
heroku config:add GITHUB_TOKEN=<github-token>
```

* Test that the latest build is restarted by manually running

```shell
heroku run rake build
```

* Add the scheduler to your heroku app

```shell
heroku addons:add scheduler:standard
heroku addons:open scheduler
```

* Add the task ```rake build``` to your heroku scheduler
