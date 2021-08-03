# User

## Content
- [CRUD endpoints](#crud-endpoints)
- [User activity list andpoints](#user-activity-list-andpoints)
- [Anonymize user andpoints](#anonymize-user-andpoints)
- [Site specific data](#site-specific_data)

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


## Site specific data

Some userdata is site specific. On the other hand: we want the oauth server to be a single source of truth, and any user data in the API should be considered cached data.

The problem now is that the oauth server does not, and should not, understand sites.  
The chosen solution is to add a siteId parameter to the data. This is currently only implemented on extraData.

The parameter is filtered by the API. On the oauth server the data is stored but not understood.

In this example a specific value for siteId 2 is defined. The other sites will fallback on the unspecified value.

```
{
  "firstName": "Niels",
  "lastName": "Vegter",
  "extraData": {
    "bio": [
      "Bio van Niels",
      {
        "value": "Bio van Niels op site 2",
        "siteId": 2
      }
    ]
  }
}

```

Which values will be filtered like this and which values won't is defined in the siteConfig. The extraData definition was already part of that; a new boolean option 'sitespecific' was added.

Fields that exist on the API but not onthe oauth server are stored s site specific data in the extraData filed on the oauth server. These fields are at the moment 'listableByRole', 'detailsViewableByRole', 'nickName', 'gender' and 'signedUpForNewsletter'.

Default 'bio' and 'expertise' are defined as site specific

```
{
  "users": {
    "extraData": {
      "a-new-field": {
        "site-specific": true
      }
    }
  }
}
```

#### Note 1

It is not possible to define a default value in the API. This should be correct: the default option only exists for fields that start out as generic and are then changed to site specific.

#### Note 2

Required fields that a user has to fill in on the oauth server are of course at that time never site specific. If the API defined them a such they will become site specific and the oauth value is used as default value.

