# Campo Heroku

Campo Heroku deploy template.

## Usage

### Setup

Click this button:

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/getcampo/campo-heroku)

Enter an unique app name, click "Deploy app".

After deploy done, click "View app" to open your website, follow setup wizard to finish deploy.

By default, worker dyno is no running, turn it on in heroku dashboard, or some features like full text search will no work.

### Upgrade

When campo release new version, we can use heroku-cli and git to upgrade.

**Please backup database before every upgrade, visit: https://devcenter.heroku.com/articles/heroku-postgres-backups**

Install heroku-cli, visit: https://devcenter.heroku.com/articles/heroku-cli .

Login heroku:

```console
$ heroku login
```

Clone this repo:

```console
$ git clone https://github.com/getcampo/campo-heroku.git
$ cd campo-heroku
```

Add heroku config, replace your-app-name with real name:

```console
$ heroku git:remote -a your-app-name
```

Push code:

```console
$ git push heroku master
```

After heroku deploy finished, campo will upgrade to new version.

You can use this command for next time:

```console
$ git pull
$ git push heroku master
```
