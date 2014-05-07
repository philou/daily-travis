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

Alternatives
============

* The travis team seems to be working on a [Build periodically](https://github.com/travis-ci/travis-ci/issues/582) feature. As of the 04/07/14, it is still not there.
* The [travis-cron](http://traviscron.pythonanywhere.com/) web app and [git repo](https://github.com/FiloSottile/travis-cron). Which is manually moderated.
