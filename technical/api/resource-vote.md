#Vote

`GET /api/site/:SITE_ID/vote`
List all votes for a site
Query params: ideaId, userId, opinion

`POST /api/site/:SITE_ID/vote`
Create or update votes



## Voting types

Available voting types per site:

- likes
- count
- budgeting

A site can have on type of voting active

If allowed  voteType 'count' or 'budgeting' old vote for same user gets replaced, `config.votes.withExisting`.

The vote types *like* works as a toggle. Likes can have a positive, yes, and a negative, no, sentiment.

One voting round can be done on multiple ideas, if the user the votes again all previous votes for ideas are cancelled, or depending on the settins an error is thrown:

```
[
  {
    "ideaId": 7,
    "opinion": "yes"
  },
  {
    "ideaId": 8,
    "opinion": "yes"
  },
  {
    "ideaId": 9,
    "opinion": "yes"
  },
  {
    "ideaId": 10,
    "opinion": "yes"
  }
]
```

Or a vote on 1 idea

```
{
  "ideaId": 7,
  "opinion": "yes"
}
```



## Voting Configuration

There are a bunch of voting scenario's for different

- Submitting ideas website: people can submit ideas, and on every idea on the site it's possible to like positivily or negatively.  Voting sngame sentiment cancels the vote, voting other sentiment cancels the vote and creates a new one
- Participitory budgetting: for budgetting site one vote is on multiple ideas within a set budget. So for instance there is 200.000 worth of budget then the users can select as many ideas as possible within that budget and make a vot on all of them
- Multiple votes: able to vote on a min and max amout of ideas
- Voting on an art or garden competition: max vote on one idea, but changeable
- Eberhard art project: max 1 vote, throw error on attempt to change



#### isViewable: false | true

Is the vote count viewable. This can influence the voting

#### isActiveFrom: "ISODate" en isActiveTo: "ISODate"

Van waneer tot waneer kan er gestemd worden. Buiten deze data is het stemmen gesloten.
De waarde van isActive overruled dit. Anders gezegd: dit werkt alleen als isActive null is.

#### isActive: null | false | true

If set to false voting is not active and trying to vote will result in an error.

#### requiredUserRole: "member" | "anonymous"

For certain roles

#### withExisting: "error" | "replace"

If 

This setting doesn't affect the vote type "likes".

Deze config var heeft geen invloed op voteType 'likes'.

#### voteType: 'likes' | 'count' | 'budgeting'



#### maxIdeas, minIdeas, 

For the vote gype count set the amount of ideas allowed to vote on. So for instance minimum 1 idea and max 3 for one vote. A new vote by a user either replaces all ideas voted on of throws an error.

#### minBudget, maxBudget

For the vote type budgeting the min and max budget that the user is allowed to vote on should be set.

#### Example configuration

Submitting idea fase:

```
{
	"isActive": true,
	"voteType": "likes",
	"isViewable": true,
	"withExisting": "replace",
}
```

Participitory budgetting:

```
{
	"isActive": true,
	"voteType": "budgeting",
	"minBudget": 200000,
	"maxBudget": 300000,
	"withExisting": "error"
}
```

Vote on multiple ideas, throw error if already voted

```
{
	"isActive": true,
	"voteType": "count",
	"maxIdeas": 5,
	"minIdeas": 4,
	"withExisting": "error"
}
```

Art competition vote on one idea, replace previous vote if already 

```
{
  "isViewable": true,
	"isActive": true,
	"voteType": "count",
	"maxIdeas": 1,
	"minIdeas": 1,
	"withExisting": "replace",
	"mustConfirm": true
}
```

