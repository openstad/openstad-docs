# Article

## Inhoud
[Endpoints](#endpoints)
[ExtraData - zie Idea](/doc/idea#extradata)

Article is a basic rest object that allows for creating blogs or news pages. It's currently mostly used by the moderators, but could also be used by "normal" users. It's very similar to the Idea

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

GET request zijn public, POST is alleen toegankelijk voor admin, de anderen alleen voor admin en de eigenaar

Je kunt aan de GETs query parameters meegeven. Die werken als scopes voor Sequelize; dat komt uit de bestaande app. Bestaande scopes zijn:

`includePosterImage`
`includeUser`

## extraData

ExtraData is similar to ideas:- [read more](/technical/api/idea#extradata)



## Todo

Arguments and votes are currently not implemented for articles. 