# Campo Heroku

Campo Heroku deploy template.

## Usage

Clone this repo:

```console
$ git clone https://github.com/getcampo/campo-heroku.git
$ cd campo-heroku
```

Install heroku-cli, visit: https://devcenter.heroku.com/articles/heroku-cli .

Login:

```console
$ heroku login
```

Create heroku app:

```console
$ heroku create
$ heroku stack:set container
```

Create addon:

```console
$ heroku addons:create heroku-postgresql:hobby-dev
$ heroku addons:create heroku-redis:hobby-dev
```

Set ENV:

```console
$ heroku config:set RAILS_ENV=production
$ heroku config:set SECRET_KEY_BASE=xxx # replace by your secret key!!!
```

Deploy app:

```console
$ git push heroku master
```
