daily-travis
============

A dead simple heroku ready travis daily sceduler

Usage
=====

1. Clone this repo locally
```
git clone https://github.com/philou/daily-travis.git
```
2. If you don't have it yet, install the [heroku toolbelt](https://devcenter.heroku.com/articles/quickstart)
3. Create an heroku app to deploy to
```
heroku apps:create <my-lib>-daily-travis
```
4. Generate a travis token
** Install the depdendencies
```
bundle install
```
** Login to travis
```
bundle exec travis login
```
** generate a command line token
```
bundle exec travis token
```
5. Add the parameters to your heroku app
```
heroku config:add TRAVIS_REPOSITORY=<github-user>/<github-repo>
heroku config:add TRAVIS_TOKEN=`bundle exec travis token`
```
6. Test the build by manually running
```
heroku run rake build
```
It should restart the latest build
7. Add the scheduler to your heroku app
```
heroku addons:add scheduler:standard
```
8. Configure the scheduler
```
heroku addons:open scheduler
```
Add the task ```rake build```
