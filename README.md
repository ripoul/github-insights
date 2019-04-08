# Why

This repository is a try to get insights on an GitHub organization and its members.

# How

Node11 is required ! Use nvm to change node version easly. Or you can use babel.

create a config.js file like that : 
```
module.exports = {
    'email':{
      'service': 'the email service (gmail)',
      'user': 'the email/user',
      'pass': 'the password'
    }
  }
```

If you are not using docker, you have to add a file named `.env` with the following content : 
```
db_user=my_user
db_host=my_host
db_database=my_db
db_pass=my_pass
db_port=my_port
GITHUB_KEY: your-github-Oauth-key-here
GITHUB_SECRET: your-github-Oauth-secret-here
PORT=the app port
adress=the adress and port of the application (http://localhost:8080)
```
If not, you can set environment variables. The variables has to be named like in the `.env` file.

# Help
## Docker

In the `docker-compose.yml` file, you need to complete the GITHUB_KEY and GITHUB_SECRET environment variable.

```
sudo docker-compose rm --all && sudo  docker-compose pull && sudo  docker-compose build --no-cache && sudo docker-compose up --force-recreate
```

## Gcloud
We may be use gcloud to host our appli : 

You have to uncoment the last line off the `Dockerfile`.

You also need a file name `app.yaml` with the folowing content : 
```
runtime: custom
env: flex
env_variables:
  db_user: 'user'
  db_host: /cloudsql/postgres instance
  db_database: 'db_name'
  db_pass: 'pass'
  adress: 'your app adress'
  GITHUB_KEY: my github prod key
  GITHUB_SECRET: my github prod secret
beta_settings:
  cloud_sql_instances: postgres instance
```

```
sudo gcloud init
sudo gcloud auth login
sudo gcloud config set project github-insights-epsi
sudo gcloud app create
sudo gcloud app deploy -v v0
```

You can find some doc to connect postgresql with node app [Here](https://cloud.google.com/sql/docs/postgres/connect-app-engine).
