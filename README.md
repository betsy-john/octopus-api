# octopus-api
This is the Api for the Octopus

# Idyllwild API

This application is built using nodejs/expressjs. DB is mysql.
To interact with the DB sequelizejs [http://sequelizejs.com/] library is used.

## Before you begin!

Before you begin you might want to read about the basic building blocks that assemble a MEAN application:

MySQL - Go through MySQL Official Website and proceed to their Official Manual, which should help you understand RDBMS and MySQL better.

Express - The best way to understand express is through its Official Website, which has a Getting Started guide, as well as an ExpressJS guide for general express topics. You can also go through this StackOverflow Thread for more resources.

Node.js - Start by going through Node.js Official Website and this StackOverflow Thread, which should get you going with the Node.js platform in no time.

Socket.io - Socket.IO enables real-time bidirectional event-based communication.  Head to docs to learn more about socket.io [https://socket.io/docs/]

## Prerequisites

To run the application on your local machine, make sure you have installed all of the following prerequisites on your development machine:

Git - Download & Install Git. OSX and Linux machines typically have this already installed.

Redis - Install redis server on dev machine (https://redis.io/download) or point your application to remote redis server by updating configuration file.

If you are using Window 10 then you can refer to https://redislabs.com/blog/redis-on-windows-10/ for help on setting up of redis server or you may also try https://www.memurai.com/ (memurai was not used by team but just a alternate suggestion )

Nodenv - Download & Install Nodenv (https://github.com/nodenv/nodenv) with node-build plugin

After you install git and nvm you can then install node - Project requires node version 12.16.0 or above.

```bash
$ nodenv install 12.18.0
$ nodenv local 12.18.0
```

Next update to the latest version of npm (Node Package Manager).

```bash
$ npm i -g npm
```

## Get the source
Find (or create) the folder in which you will downloading the source code. In my case I use ~/projects/idyllwild/idyllwild-api

```bash
$ mkdir ~/projects/idyllwild/idyllwild-api
$ cd ~/projects/idyllwild/idyllwild-api
```

Then clone the repository

```bash
$ git clone git@github.com:v2dev/idyllwild-api.git .
```
Next install all of the npm (package.json)

```bash
$ npm install
```

## Setup system specific configurations

application specific configurations are stored in .env file. A sample file is provided (.env.sample). Copy this and remove the .sample extension and modify the contents to match the system specific values.

Once the configurations is updated, you can create  the db by running the following command

```bash
$ npx sequelize-cli db:create
```

Run the database migration to create all the tables

```bash
$ npx sequelize-cli db:migrate
```

Run the database seed to load the default data required to run the application

```bash
$ npx sequelize-cli db:seed:all
```

## Start the server

```bash
$ npm start
```

## IMPORTANT!! Every time you pull a new version

You will need to update your node and angular packages by running

```bash
$ npm install
```

Update the database schema

```bash
$ npx sequelize-cli db:migrate
```

To add a migration script to the source code - only for developers

```bash
$ npx sequelize-cli migration:generate --name <file-name-withtout-extension>
```

To add a seeder script to the source code - only for developers

```bash
$ npx sequelize-cli seed:generate --name <file-name-withtout-extension>
```

## Api documentation

We use RAML[https://raml.org/] to document the API. Tutorials are available at
  - https://raml.org/developers/raml-100-tutorial
  - https://raml.org/developers/raml-200-tutorial


To build the api documentation files
  - update api.raml file
  - execute  following commands to generate the html files
    ```bash
    $ npm run generate-doc
    ```
  - To see the generated document files
    ```bash
    $ npm run doc-server
    ```


