## Arguments

`GET /api/site/:SITE_ID/argument`
list all arguments for a site

`GET /api/site/:SITE_ID/idea/:IDEA_ID/argument`
list all arguments for one idea

`GET /api/site/:SITE_ID/idea/:IDEA_ID/argument?sentiment=for?sentiment=for&withUserVote=1&withVoteCount=1`
list all arguments for one idea where sentiment is 'for'
include the number of votes on this argument
include whether or not the current user has voted

`GET /api/site/:SITE_ID/idea/:IDEA_ID/argument/:ARG_ID`
view one argument

`POST /api/site/:SITE_ID/idea/:IDEA_ID/argument`
create an argument
			 
`PUT /api/site/:SITE_ID/idea/:IDEA_ID/argument/:ARG_ID`
update one argument

`POST /api/site/:SITE_ID/idea/:IDEA_ID/argument/:ARG_ID/vote`
toggle the current users vote for this argument

`DELETE /api/site/:SITE_ID/idea/:IDEA_ID/argument/:ARG_ID`
delete one argument

