# Admin panel

The admin panel has the following purposes: creating & deleting sites and managing it's settings and managing users. There is a lot configuration possible and the admin panel makes this easier.

The admin is build in nodejs, and doesn't have it's own database, it connects to the API and the Auth server to manage it's configurations. 

## Creating & importing sites

Creating sites consists of 3 mains steps: copying a mongodb database, creating a row in the sites table in the API with the correct config and creating clients in the Auth Api.

When importing external sites the admin panel als mananges importing external images and certain REST objects.

## Beta version in React-admin
There is an updated version for managing a site's data and settings. This run both in the frontend CMS for the specificsite under /admin and in the admin panel per site. This is build in react-admin, a react framework for creating interface. This will allow for a better UX in the future since it allows for bulk deletes and updates.

Repository here:
https://github.com/Amsterdam/openstad-react-admin 
