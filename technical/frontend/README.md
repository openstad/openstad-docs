# Openstad Frontend
The openstad frontend is primarly built upon the ApostropheCMS, there are also a few react application that are run as modules inside ApostropheCMS.

The main repo is found here: https://github.com/Amsterdam/openstad-frontend

## In page editing
On of the main reasons ApostropheCMS was chosen because it easily allows for in page editing allowing for highly dynamic page.


## Multisite
We have a custom implementation of ApostropheCMS multisite, this allows one installation to run multiple domains. As explainend in the architecture section this works together with the API and Kubernetes to make it all work. With every domain request the frontend server checks if the domain exists in cached config, if not present make a call to the Openstand API if such a domain exists, if yes it will create an express server if not it will return a 404

## ApostropheCMS documentation
In ApostropheCMS almost everything is written as a module, found in a lib/modules folder, can be a widget hat can be displayed on a page, a custom page or any other of the possible extension of other ApostropheCMS functionality.

The documentation of ApostropheCMS is comprehensive and good place to start if you want to create your own modules: http://apostrophecms.org/.


## The Openstad version of ApostropheCMS
We have bundled the ApostropheCMS as Openstad CMS local npm pacakage. The files are found packages/cms this his allows for the core files to be overwritten without needing to change the core files. Simple create the files you want to overwrite directly under lib/modules.

This is a core feature of the ApostropheCMS and because of the way we bundled it works for both the ApostropheCMS widgets and the Openstad widgets.

For now  treat it as a local NPM package, in the future this will be moved to an external NPM package.
