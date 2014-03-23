daily-travis
============

A dead simple heroku ready travis daily sceduler

Usage
=====

1. Clone this repo locally
```shell
git clone https://github.com/philou/daily-travis.git
```

2. If you don't have it yet, install the [heroku toolbelt](https://devcenter.heroku.com/articles/quickstart)

3. Create an heroku app to deploy to
```shell
heroku apps:create <my-lib>-daily-travis
```

4. Generate a travis token
```shell
bundle install
bundle exec travis login
bundle exec travis token
```

5. Add the parameters to your heroku app
```shell
heroku config:add TRAVIS_REPOSITORY=<github-user>/<github-repo>
heroku config:add TRAVIS_TOKEN=`bundle exec travis token`
```

6. Test the build by manually running
```shell
heroku run rake build
```
It should restart the latest build

7. Add the scheduler to your heroku app
```shell
heroku addons:add scheduler:standard
heroku addons:open scheduler
```

8. Add the task ```rake build``` to your heroku scheduler
