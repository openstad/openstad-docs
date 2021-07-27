# Article

## Content
- [Endpoints](#endpoints)
- [ExtraData - zie Idea](/doc/idea#extradata)

Article is a basic rest object that allows for creating blogs or news pages. It's currently mostly used by the moderators, but could also be used by "normal" users. It's very similar to the Idea model, but arguments and votes are not implemented for articles. 

## Endpoints

`GET /api/site/:SITE_ID/article/`  
list all articles

`POST /api/site/:SITE_ID/article/`  
create an article

`GET /api/site/:SITE_ID/article/:ARTICLE_ID`  
view one article

`PUT /api/site/:SITE_ID/article/:ARTICLE_ID`  
update one article

`DELETE /api/site/:SITE_ID/article/:ARTICLE_ID`  
delete one article

GET requests are public, POST only available for moderators and owners

Following GET parameters are available:

`includePosterImage`
`includeUser`

## extraData

ExtraData is similar to ideas:- [read more](/technical/api/idea#extradata)

