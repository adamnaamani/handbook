# Commands

## Table of Contents
1. [Terminal](#terminal)
1. [Rails](#rails)
1. [Rspec](#rspec)
1. [Heroku](#heroku)
1. [SQL](#sql)
1. [MySQL](#mysql)
1. [Postgres](#postgres)
1. [Git](#git)
1. [cURL](#curl)
1. [Ubuntu](#ubuntu)
1. [SSL Certificate](#ssl-certificate)
1. [AWS](#aws)
1. [Docker](#docker)
1. [Cucumber](#cucumber)
1. [npm](#npm)
1. [Chrome](#chrome)
1. [Google Docs](#google-docs)
1. [Wordpress](#wordpress)

## Terminal
### Kill running servers
```bash
lsof -wni tcp:3000
kill -9 PID
```
### Assign last command to variable
```bash
x = _
```
### Search commands
```bash
ctrl+r: (reverse-i-search)
```
### whois
```bash
whois website.com
```

## Rails
### Migrations
```bash
rails db:migrate:status
rails db:migrate:redo
rails db:migrate:down VERSION=<version>
```
### pg_search
```bash
rake pg_search:multisearch:rebuild[Listing]
```
### PostGIS
```bash
rake db:gis:setup
```

## Rspec
### Swagger
```bash
rake rswag:specs:swaggerize
```

## Heroku
```bash
heroku pg:backups:download -a [app]
heroku pg:pull [POSTGRES_ENV] [database_name] --app [app]
heroku pg:backups:restore '<SIGNED URL>' DATABASE_URL
heroku pg:psql --app [app]
heroku pg:credentials:url -a [app]

heroku run rails c --sandbox --app [app]
heroku run rails c -app [app]
heroku run /bin/bash --type worker --app [app]

heroku logs -t --app [app]
heroku logs --ps scheduler.1

heroku labs:enable runtime-dyno-metadata

heroku local

cat /app/services/create.rb
```

## SQL
```bash
DELETE FROM table WHERE id IN ();

BEGIN;
SQL;
COMMIT;

CREATE TABLE table_name AS (SELECT * FROM table WHERE 1 = 2);

ORDER BY 1,2
```

## MySQL
### WordPress
```bash
use wordpress;
show tables;
update wp_options set option_value = x  where option_id = 1;
select * from wp_options where option_value = x;
```

## Postgres
### pg
```bash
pg_dump -Fc db > db.dump
pg_dump --table [table] postgres://<url> > file.sql

pg_restore -d <database> -t <table> -a latest.dump
```
### psql
```bash
psql <database>

\i file.sql
```

## Git
### Initializing
```bash
git init --bare
```

### Squashing
```bash
git log --graph --decorate --pretty=oneline --abbrev-commit
git rebase -i HEAD~<number>
git push origin <branch> --force
```

### Resetting
```bash
git fetch origin
git reset HEAD~
git reset --hard HEAD~1 
git reset --soft HEAD~1
```

### Merging
```bash
git merge
git merge --abort
```

### Conflicts
```bash
git pull origin master
git commit -m “Merge w/ master”
git push -f
```

### Adding
```bash
git add -p
```

## cURL
```bash
curl -ILk website.com

curl "http://localhost:3000/v1/sign_in" -H "accept: application/json" -H "Content-Type: application/json" -d "{ \"user\": { \"email\": \"name@email.com\", \"password\": \"password\" }}" -i
```

## Ubuntu
```bash
ssh root@<ip>

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo reboot

cd /var
mkdir repo && cd repo
mkdir site.git && cd site.git

/var/www/domain.com
/var/repo/site.git

git init --bare
HEAD  branches  config  description  hooks  info  objects  refs
cat > post-receive

#!/bin/sh
git --work-tree=/var/www/html --git-dir=/var/repo/repo.git checkout -f
chmod +x post-receive

scp -r root@138.197.139.140:/var/www .
```

## SSL Certificate
```bash
sudo add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install python-certbot-apache
sudo certbot --apache -d domain.com -d www.domain.com
```

## AWS
```bash
aws-cli

aws s3 ls
aws s3 ls s3://bucket
aws s3 mb s3://bucket
aws s3 rb s3://bucket --force
aws s3 cp file s3://bucket
aws s3 rm --recursive s3://bucket/folder
aws s3 presign s3://bucket/object
aws s3 sync folder s3://bucket/folder
```

## Docker
```bash
docker-compose up
docker-compose run app bundle install
docker-compose run --rm app bash
```

## Cucumber
```bash
brew cask install chromedriver
brew cask upgrade chromedriver

@chrome
```

## npm
```bash
npm list --depth=0
npm outdated --depth=0
```

## Chrome
```
chrome://inspect/#service-workers
```

## Google Docs
### Em-dash
```bash
Option + Shift + -
```

## WordPress
### Defining
```bash
define('FS_METHOD','direct');
```
