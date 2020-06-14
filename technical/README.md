# Technical Overview
There are four main servers: the frontend server, the API, the OAuth server and an image server. Next to that there is an admin panel which allows for managing all the servers & creating new websites.

![Architectural overview](/img/architectural-overview.png)

## Frontend server: ApostropheCMS
The frontend is built with the [ApostropheCMS](https://docs.apostrophecms.org/). ApostropheCMS allows for highly flexible pages. Enabling the UX & designers to build complete websites from the ground. Laying the foundation for a flexible system that allows for simple voting websites to complex participatory budgeting websites.  

On top of the core of ApostropheCMS we have integrated and developed the Openstad (open city) functionality of submitting ideas, voting, participatory budgeting, arguments and more.

The frontend CMS is developed in such a way that it can run multiple sites on one server.

Installation instructions are found in the readme. MongoDB & Node.js are required.

https://github.com/Amsterdam/openstad-frontend


## Openstad API
When the Frontend server gets a visitor it queries the API to get the config needed for the domain visited. Therefore the frontend serverr can’t run without the API server.

Check the readme for installation.

Make sure the correct environment values are in the .env file of the frontend the API and SITE_API_KEY are required. The SITE_API_KEY is set in the config/local.json file.

https://github.com/Amsterdam/openstad-api


## OAuth Server
The OAuth server is required for authenticating & voting users allowing them to submit & manage ideas, arguments & vote.

See the readme for installation.

Make sure the correct config values are set in the config/local.json.
Every site has it’s own OAuth client. The public clientId and clientSecret should be site in the API sites table in the config.

https://github.com/Amsterdam/openstad-oauth2-server

## Image server
We run  a simple image server. This is required when uploading and saving images for submitting an idea. Installation instructions found in readme. Set corresponding values in the .env of the fronted server.
https://github.com/Amsterdam/openstad-image-server

## Admin panel
![Admin panel screenshot](/img/admin-panel-screenshot.png)

The admin panel is an interface for managing the OAuth, frontend & API. All the server run without the admin panel, but it makes it a lot easier to manage and create sites. The panel allows for creating new sites by copying existing sites, managing users, voting codes, voting setting and more.
(GitHub still empty, in bitbucket for now)
