# Idea

## Content
- [Endpoints](#endpoints)
- [ExtraData](#extradata)
- [ToDo](#todo)

## Endpoints

`GET /api/site/:SITE_ID/idea/`
list all ideas

`POST /api/site/:SITE_ID/idea/`
create an idea

`GET /api/site/:SITE_ID/idea/:IDEA_ID`
view one idea

`PUT /api/site/:SITE_ID/idea/:IDEA_ID`
update one idea

`DELETE /api/site/:SITE_ID/idea/:IDEA_ID`
delete one idea

GET request are public, POST are only accessible to owners or moderators.

To include more data there are a few get parameters available: 

`selectRunning`
`includeArguments`
`includePosterImage`
`includeUser`
`includeVoteCount`
`includeUserVote`

## extraData
Ideas contain an extraData field for dynamic data that changes per site. The allowed values are configurable per site (it's own rest object)

Supported field types:
`boolean`
`int`
`string`
`arrayOfStrings`
`enum`
`object`

Object is a special case; it requires a subset of definitions (see example). These will be checked recursively.

Removing fields is done by sending them with value `null`.

#### extraDataMustBeDefined

In old versions ist wasn't required to define the extraData values in the site configuration, therefore by default the check is not made at the moment. However extraDataMustBeDefined: true forces the validation, and will soon be the default.

#### Example configuration


```
  "config": {
    "ideas": {
      "extraData": {
        "zomaar": {
          "type": "object",
          "subset": {
            "zomaar sub1": {
              "type": "string",
              "allowNull": true
            },
            "zomaar sub2": {
              "type": "boolean",
              "allowNull": true
            }
          },
          "allowNull": false
        },
        "images": {
          "type": "arrayOfStrings",
          "allowNull": true
        },
        "gebied": {
          "type": "enum",
          "values": [
            "Oud-West",
            "Bos en Lommer",
            "De Baarsjes",
            "Westerpark",
            "West Algemeen"
          ],
          "allowNull": false,
        }
      }
    }
  }
```

Example data:
```
  "extraData": {
    "zomaar": {
      "zomaar sub1": "Boe",
      "zomaar sub2": true
    },
    "gebied": "De Baarsjes",
    "images": [
      "https://image-server.staging.openstadsdeel.nl/image/kleine-wereld-6428.jpg"
    ]
  }
```

