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

* Generate a travis token

```shell
bundle install
bundle exec travis login
bundle exec travis token
```

* Add the parameters to your heroku app

```shell
heroku config:add TRAVIS_REPOSITORY=<github-user>/<github-repo>
heroku config:add TRAVIS_TOKEN=`bundle exec travis token`
```

* Test the build by manually running

```shell
heroku run rake build
```
It should restart the latest build

* Add the scheduler to your heroku app

```shell
heroku addons:add scheduler:standard
heroku addons:open scheduler
```

* Add the task ```rake build``` to your heroku scheduler
