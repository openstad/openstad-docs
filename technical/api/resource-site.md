# Site

`GET /api/site/`
list all sites

`POST /api/site/`
create a site

`GET /api/site/:SITE_ID`
view one site

`PUT /api/site/:SITE_ID`
update one site

`DELETE /api/site/:SITE_ID`
delete one site

GET request are public, certain config data is excluded publicly. The post, put and delete are all admin only.

## Anonymize all users for a site

New endpoints:

`PUT /api/site/:SITE_ID/will-anonymize-all-users`
`PUT /api/site/:SITE_ID/do-anonymize-all-users`
Anonymize all users for one site.

Only available to admins
`site.config.projectHasEnded` must be `true`
Administrators will not be anonymized.

Returns
- a list of users that will be / have been anonymized
- a list of admins that will not be / have not been anonymized

### Project has ended

projectHasEnded is a new site.config param. This param is available through the React Admin.

Setting this parameter will also update a range of ther settings:
```
config.votes.isActive = false;
config.ideas.canAddNewIdeas = false;
config.articles.canAddNewArticles = false;
config.arguments.isClosed = true;
config.polls.canAddPolls = false;
config.users.canCreateNewUsers = false;
```

This now works one way: setting the projectHasEnded will set the above parameters. Unsetting it will _not_ update these parameters.

If settings do not match the projectHasEnded settings a warning is given


#### Site config

One of the crucial aspects of the Site is it's config option, it is saved in a JSON column. The site configuration for how site should handle voting, ideas, arguments, domains, what Database CMS uses, if Basic Auth is turned and and more.

This is the current default configuration:

```
{
  "config": {
    "allowedDomains": {
      "type": "arrayOfStrings",
      "default": [
        "https://openstad-api.amsterdam.nl"
      ]
    },
    "basicAuth": {
      "type": "object",
      "subset": {
        "active": {
          "type": "boolean",
          "default": false
        },
        "user": {
          "type": "string",
          "default": "openstad"
        },
        "password": {
          "type": "string",
          "default": "LqKNcKC7"
        }
      }
    },
    "cms": {
      "type": "object",
      "subset": {
        "dbName": {
          "type": "string",
          "default": "domainname-id"
        },
        "url": {
          "type": "string",
          "default": "https://openstad-api.amsterdam.nl"
        },
        "hostname": {
          "type": "string",
          "default": "openstad-api.amsterdam.nl"
        },
        "after-login-redirect-uri": {
          "type": "string",
          "default": "/oauth/login?jwt=[[jwt]]"
        }
      }
    },
    "notifications": {
      "type": "object",
      "subset": {
        "from": {
          "type": "string",
          "default": "EMAIL@NOT.DEFINED"
        },
        "to": {
          "type": "string",
          "default": "EMAIL@NOT.DEFINED"
        }
      }
    },
    "email": {
      "type": "object",
      "subset": {
        "siteaddress": {
          "type": "string",
          "default": "EMAIL@NOT.DEFINED"
        },
        "thankyoumail": {
          "type": "object",
          "subset": {
            "from": {
              "type": "string",
              "default": "EMAIL@NOT.DEFINED"
            }
          }
        }
      }
    },
    "oauth": {
      "type": "objectsInObject",
      "subset": {
        "auth-server-url": {
          "type": "string"
        },
        "auth-client-id": {
          "type": "string"
        },
        "auth-client-secret": {
          "type": "string"
        },
        "auth-server-login-path": {
          "type": "string"
        },
        "auth-server-exchange-code-path": {
          "type": "string"
        },
        "auth-server-get-user-path": {
          "type": "string"
        },
        "auth-server-logout-path": {
          "type": "string"
        },
        "after-login-redirect-uri": {
          "type": "string"
        }
      }
    },
    "ideas": {
      "type": "object",
      "subset": {
        "canAddNewIdeas": {
          "type": "boolean",
          "default": true
        },
        "feedbackEmail": {
          "from": {
            "type": "string",
            "default": "EMAIL@NOT.DEFINED"
          },
          "subject": {
            "type": "string"
          },
          "inzendingPath": {
            "type": "string",
            "default": "/PATH/TO/PLAN/[[ideaId]]"
          },
          "template": {
            "type": "string"
          }
        }
      }
    },
    "arguments": {
      "type": "object",
      "subset": {
        "new": {
          "type": "object",
          "subset": {
            "anonymous": {
              "type": "object",
              "subset": {
                "redirect": {
                  "type": "string",
                  "default": null
                },
                "notAllowedMessage": {
                  "type": "string",
                  "default": null
                }
              }
            },
            "showFields": {
              "type": "arrayOfStrings",
              "default": [
                "zipCode",
                "nickName"
              ]
            }
          }
        }
      }
    },
    "votes": {
      "type": "object",
      "subset": {
        "isViewable": {
          "type": "boolean",
          "default": false
        },
        "isActive": {
          "type": "boolean",
          "default": null
        },
        "isActiveFrom": {
          "type": "string"
        },
        "isActiveTo": {
          "type": "string"
        },
        "requiredUserRole": {
          "type": "string",
          "default": "member"
        },
        "mustConfirm": {
          "type": "boolean",
          "default": false
        },
        "withExisting": {
          "type": "enum",
          "values": [
            "error",
            "replace"
          ],
          "default": "error"
        },
        "voteType": {
          "type": "enum",
          "values": [
            "likes",
            "count",
            "budgeting"
          ],
          "default": "likes"
        },
        "maxIdeas": {
          "type": "int"
        },
        "minIdeas": {
          "type": "int"
        },
        "minBudget": {
          "type": "int"
        },
        "maxBudget": {
          "type": "int"
        }
      }
    },
    "newslettersignup": {
      "type": "object",
      "subset": {
        "isActive": {
          "type": "boolean",
          "default": false
        },
        "confirmationEmail": {
          "type": "object",
          "subset": {
            "from": {
              "type": "string",
              "default": "EMAIL@NOT.DEFINED"
            },
            "subject": {
              "type": "string"
            },
            "url": {
              "type": "string",
              "default": "/PATH/TO/CONFIRMATION/[[token]]"
            },
            "template": {
              "type": "string"
            }
          }
        }
      }
    },
    "ignoreBruteForce": {
      "type": "arrayOfStrings",
      "default": []
    }
  }
}
```


