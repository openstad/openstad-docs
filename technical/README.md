#Technical Overview#
There are four main servers: the frontend server, the API, the oAuth server and an image server. Next to that there is an admin panel which allows for managing all the servers & creating new websites.

![Architectural overview](/img/architectural-overview.png)

##Frontend server: ApostropheCMS##
The frontend is build with the ApostropheCMS. ApostropheCMS allows highly flexible pages. Enabling the UX & designers to build complete websites from the ground. Laying the foundation for a flexible system that allows for simple voting websites to complex participatory budgeting websites.  

GIF

On top of the core of ApostropheCMS we have integrated and developed the Openstad (open city) functionality of submitting ideas, voting, participatory budgeting, arguments and more.

The frontend CMS is developed in such a way that it can run multiple sites on one server.

Installation instructions are found in the readme. Mongodb & node are required
https://github.com/Amsterdam/openstad-frontend


##Openstad API##
When the Frontend server gets a visitor it queries the API to get the config needed for the domain visited. Therefore the frontend can’t run without the API. The

Check the readme for installation.

Make sure the correct environment values are in the .env file of the frontend the API and SITE_API_KEY are required. The SITE_API_KEY is set in
The config/local.json
https://github.com/Amsterdam/openstad-api


##Oauth Server##
The oAuth server is required for authenticating & voting users allowing them to submit & manage ideas, arguments & vote.

See readme
https://github.com/Amsterdam/openstad-oauth2-server

Make sure the correct config values are set in the config/local.json.
Every site has it’s own oAuth client. The public clientId and clientSecret should be site in the API sites table in the config.

##Image server##
There is a simple image server required for uploading and saving images when submitting an idea, installation instructions found in readme. Set corresponding values in the .env of the fronted server.
https://github.com/Amsterdam/openstad-image-server

##Admin panel##
![Admin panel screenshot](/img/admin-panel-screenshot.png)

The admin panel is an interface for managing the oAuth, frontend & API. All the server run

It allows creating new sites by copying existing sites, managing users, voting codes, voting setting and more.
(GitHub still empty, in bitbucket for now)
