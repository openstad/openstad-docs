# Tags

## Inhoud
[Description](#description)
[Endpoints](#endpoints)
[Ideas](#ideas)

## Description

Tags are a form categorising with

In ideas zijn tags terug gebracht tot alleen de name, zowel in de resultaten als in de create/update van het idee.

Administrating can be done by admin. Adding to ideas is allowed by the author of the idea and moderator. 

## Endpoints

#### List all tags
```
GET :HOSTNAME/api/site/:SITE_ID/tag
```

#### Show one tag
```
GET :HOSTNAME/api/site/:SITE_ID/tag/:TAG_ID
```

#### Create a tag
```
POST :HOSTNAME/api/site/:SITE_ID/tag

{
  "name": "Fietsen"
}
```

#### Update a tag
```
PUT :HOSTNAME/api/site/:SITE_ID/tag/:TAG_ID

{
  "name": "Rode fietsen"
}
```

#### Delete a tag
```
DELETE :HOSTNAME/api/site/:SITE_ID/tag/:TAG_ID
```

## Ideas

Op idee niveau worden tags alleen op name gebruikt.

Gebruik includeTags om tags in het resultaat mee te nemen:
```
GET :HOSTNAME/api/site/:SITE_ID/idea?includeTags=1
```
Dat geeft dan als resultaat
```
{
  ...idea fields
  "tags": ["Rode fietsen", "Gele auto's"],
  ...more idea fields
}
```

Zo stuur je ze ook mee bij het creeren of updaten van een idea:
```
PUT :HOSTNAME/api/site/:SITE_ID/idea/:IDEA_ID

{
  "title": "Updated title",
  "tags": [1, 2],
  ...more idea fields
}

```

Getting ideas based upon tags is done with.

```
GET :HOSTNAME/api/site/:SITE_ID/idea?tags[]=1&tags[]=2
```

