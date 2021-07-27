# User

## Content
- [CRUD endpoints](#crud-endpoints)
- [User activity list andpoints](#user-activity-list-andpoints)
- [Anonymize user andpoints](#anonymize-user-andpoints)

Users in the API are considered cache; the oauth server is the single source of truth.

## CRUD endpoints

`GET /api/site/:SITE_ID/user/`  
list all users

`POST /api/site/:SITE_ID/user/`  
create an user

`GET /api/site/:SITE_ID/user/:USER_ID`  
view one user

`PUT /api/site/:SITE_ID/user/:USER_ID`  
update one user

`DELETE /api/site/:SITE_ID/user/:USER_ID`  
delete one user

## User activity list andpoints

`GET :HOSTNAME/api/site/:SITE_ID/user/:USER_ID/activity`  

#### Query params

`includeOtherSites`  
default true

`includeIdeas`  
`includeArticles`  
`includeArguments`  
`includeVotes`  
If none of these is defined then all are true(!)

Example:  
`GET :HOSTNAME/api/site/:SITE_ID/user/:USER_ID/activity?includeOtherSites=0&includeIdeas=1&includeVotes=1`  



## Anonymize user andpoints

```
/api/site/:SITE_ID/user/:USER_ID/will-anonymize
/api/site/:SITE_ID/user/:USER_ID/will-anonymizeall
/api/site/:SITE_ID/user/:USER_ID/do-anonymize
/api/site/:SITE_ID/user/:USER_ID/do-anonymizeall
```

do-anonymize will 
- remove all personal information(*) from the API user record for this site
- remove votes from the site if voting is active
- remove the connection to the oauth server user
- remove the user from the oauth server if this user does not exist on any other site

do-anonymizeall will do this for this user on all sites.

will-anonymize(all) returns a list of
- ideas and arguments that will be anonymized
- votes that will be removed
- users that will be anonymized
- sites related to the above

do-anonymize(all) returns the same information. That is: it returns the information from before the anonymization.

(*) firstName and lastName will be replaced with the values defined in _config.users_:
```
"users": {
  "anonymize": {
    "firstName": "Gebruiker",
    "lastName": "verwijderd"
  }
}
```
