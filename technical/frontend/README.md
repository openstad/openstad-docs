# Openstad Frontend
The openstad frontend is primarly built upon the ApostropheCMS, there are also a few react application that are run as modules inside ApostropheCMS.

ApostropheCMS allows for in page editing.

We have a custom implementation of ApostropheCMS multisite, this allows one installation to run multiple domains. As explainend in the architecture section. With every domain request the frontend server checks if the domain exists in cached config, if not present make a call to the Openstand API if such a domain exists

The documentation of ApostropheCMS
