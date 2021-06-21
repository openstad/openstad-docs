# Openstad Components

The Openstad copmponents are widgets to be used by the openstad-frontend or any other frontend.

The main repo is found here: https://github.com/Amsterdam/openstad-components.

## React

The components are created using React. Build versions are created using webpack.

## Use

To use a component it needs to be loaded in your page. The examples directory contains more information on how to do that


## Automagic publishing of openstad-components

For every push to the development, release or master branch some automated steps are done by Travis: setup a version number and publish to npm.

The version number is created as folows:
- take the version number from the package.json file
- use tags: alpha for the development branch, beta for releaase, and latest for master.
- ask npm what the most recently published version is for that tag and the current version
- add one to the minor version and publish using the tag and new versionnumber

Eg. the current version number in package.json is 0.30.0. On a push to development travis starts.  
It finds that the latest release tagged alpha is 0.30.0-alpha.1. It increase the last numer and publishes to 0.30.0-alpha.2  
The components are now available and van be used for example through jsdelivr: https://cdn.jsdelivr.net/npm/openstad-components@0.30.01-alpha.2/dist/all.js

This means that you do not need to update the number in package.json for every commit.

Details in [.travis.yml](https://github.com/Amsterdam/openstad-components/blob/master/.travis.yml) and [set-publish-version.js](https://github.com/Amsterdam/openstad-components/blob/master/scripts/set-publish-version.js)

