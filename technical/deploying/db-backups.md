# Backups

There are a few backup possibilities. 



## Cloud provider backups

Most cloud providers offer some form of backups through snapshots.



## Database backups

We have 2 cronjobs in the API for backing up MongoDB en Mysql that can connect to an S3 storage bucket. Both AWS as Digital Ocean support S3. For both providers rules about expiration and deleting old files can be set throught their API. Openstad currectly doesn't actively manage removing old backup files.

These get activated if certain environment values are set in the Helm values, mostly managed by a custom-values.yml.

There is also a shell script to be found that can connect to a Openstack storage, although this one is not added to a cron and has to be added manually.  















