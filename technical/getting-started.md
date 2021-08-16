# Getting started 

These instructions are meant for running the openstad servers locally.

The are 5 different node servers working together. To make it easier to get started quickly and not manually configure every server, we made an overlaying git that bundles the 5 servers and added a few node scripts to install and run them with just a few commands.  

Prerequisites:
- NodeJS > v10 (note that on a newer Node-version, some packages - notably 
- Mysql
- Mongodb

## 1. Checkout openstad-app git repo
We've bundled our 5 nodejs servers in one git repo openstad-app with git submodules. Be aware submodules in GIT work a bit different then regular git repositories.

```
git clone https://github.com/Amsterdam/openstad-app
```

After checking out the repo, the git submodules need to be pulled separately, this is one way of doing that:

```
cd openstad-app
git submodule update --init --recursive
```

After this you will see 5 directories, each of which contains an autonomous node server. These servers can be run and managed separately, but it's easier to use the scripts provided in the root level. 

It might however be useful for debugging purposes to run them separately every now and then, in this case the values from app.js should be copied to the .env of the server you are trying to run (the root file in the .env uses different keys).

## 2. Create an .env file

First create the .env before installing everything. There is an .env.example in the root openstad-app repo. Copy it and rename it to .env in the same folder.

Make sure the MySQL credentials are correct. For the rest the defaults don't have to change.

By default this will run the CMS at http://localhost:4444/. 

A login token will be generated following the given value for AUTH_FIRST_CLIENT_LOGIN_CODE. 



## 5. Install the node_modules

There is a script to install all the node_modules for 5 servers at once. It's also possible to run the npm i command separately in every sub git folder.

```
npm i
node npm-install.js
```



## 6. Create the MySQL databases

Make sure both MySQL and MongoDB are running.

Create the MySQL databases manually, by default these are named in the .env file: image, api and auth.

```
mysql
CREATE TABLE image
CREATE TABLE api
CREATE TABLE auth
```



## 7. Create and fill tables for the databases

Install knex globally:

```
npm install knex -g
```

The following script install and fill all 3 databases:

```
node install-databases.js
```

Warning: currently this script is not safe to run twice and will fail. In case you want to run again, easiest is to manually delete all tables. 

In case you get an error that password is not supported:

```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'
```

If you are running a version of MySQL above version 5 then you will most likely get the following error:

```
Unhandled rejection SequelizeDatabaseError: FUNCTION api_test_script.GeomFromText does not exist
```

In this case add following to the .env file:

```
MYSQL_ST_GEO_MODE=on
```



## 8. Run the servers

Make sure Nodemon is installed globally:

```
npm install -g nodemon
```

Now run all servers with:

```
node app.js
```

That should be it :)



## What to expect

By default the CMS is found at http://localhost:4444. Login via http://localhost:4444/login with the login token set in the .env-file under AUTH_FIRST_CLIENT_LOGIN_CODE. Note: this value was only used during the creation of the mysql tables. Changing it afterwards in .env will not change the login token.

The admin panel is found at  http://localhost:7777. It is of limited use locally because it allows for copying sites and managing setting per site and it expects dynamic DNS settings. For a kubernetes cluster it also manages the Ingress host and SSL settings. If you want to run multiple local sites it's easiest to add a few urls that point to 127.0.0.1 in the etc/hosts file of your machine then it's possible to create them in the admin panel, be aware it's needed to at the port number: http://local.budgeting:4444






