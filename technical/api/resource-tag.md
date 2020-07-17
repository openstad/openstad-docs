# Tags

[Description](#description)
[Endpoints](#endpoints)
[Ideas](#ideas)

## Description

Tags are a form categorising for ideas.

Administrating can be done by moderators. Adding to ideas is allowed by the author of the idea and moderator. 

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

In order to get the tags in an idea call
```
GET :HOSTNAME/api/site/:SITE_ID/idea?includeTags=1
```
When updating an Idea add te id's of the tags:

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

