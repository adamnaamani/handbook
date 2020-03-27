# Heroku

## Table of Contents
1. [Postgres](#postgres)
1. [Rails Console](#rails-console)
1. [Logs](#logs)

## Postgres
```bash
heroku pg:backups:download -a [app]
heroku pg:pull [POSTGRES_ENV] [database_name] --app [app]
heroku pg:backups:restore '<SIGNED URL>' DATABASE_URL
heroku pg:psql --app [app]
```

## Rails Console
```bash
heroku run rails c --sandbox --app [app]
heroku run rails c -app [app]
```

## Logs
```bash
heroku logs -t --app [app]
heroku logs --ps scheduler.1
```
