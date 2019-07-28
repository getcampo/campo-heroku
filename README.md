# Campo Heroku

Campo Heroku deploy template.

## Usage

### Setup

Click this button:

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/getcampo/campo-heroku)

Enter an unique app name, click "Deploy app".

After deploy done, click "View app" to open website, follow setup wizard to finish deploy.

By default, worker dyno is no running, turn it on in heroku dashboard, or some features like full text search will no work.

Now Campo is up and running.

### Install Heroku CLI

For advanced settings, we need Heroku CLI, visit: https://devcenter.heroku.com/articles/heroku-cli .

Login heroku:

```console
$ heroku login
```

### Config storage

Because Heroku's disk is not persistent, we should config a cloud storage for attachments. Current Campo support AWS S3 and Google Cloud Stroage.

Notice: Changing storage need a lot of migrations, we should decide which cloud service provider to use before publishing the site.

#### AWS S3

Create a S3 Bucket and secret keys, visit: https://aws.amazon.com/cn/premiumsupport/knowledge-center/create-access-key/

Set S3 credentials by Heroku CLI or dashboard:

```console
$ heroku config:set STORAGE_SERVICE=aws -a your-app-name
$ heroku config:set STORAGE_AWS_ACCESS_KEY_ID=your-access-key-id -a your-app-name
$ heroku config:set STORAGE_AWS_SECRET_ACCESS_KEY=your-secret-access-key -a your-app-name
$ heroku config:set STORAGE_AWS_REGION=your-region -a your-app-name
$ heroku config:set STORAGE_AWS_BUCKET=your-bucket -a your-app-name
```

Heroku will auto restart app.

#### Google Cloud Storage

Create a Google Cloud Storage bucket and json keyfile, visit: https://cloud.google.com/iam/docs/creating-managing-service-account-keys

Set GClodu credentials by Heroku Cli or dashboard:

```console
$ heroku config:set STORAGE_SERVICE=gcloud -a your-app-name
$ heroku config:set STORAGE_GCLOUD_PROJECT=your-gcloud-project -a your-app-name
$ heroku config:set STORAGE_GCLOUD_BUCKET=your-gcloud-bucket -a your-app-name
$ heroku config:set STORAGE_GCLOUD_KEYFILE_CONTENT=$(< path/to/keyfile.json) -a your-app-name
```

Heroku will auto restart app.

### Upgrade

**Please backup database before every upgrade, visit: https://devcenter.heroku.com/articles/heroku-postgres-backups**

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
