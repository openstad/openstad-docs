# Vote

`GET /api/site/:SITE_ID/vote`
List all votes for a site. Query params: ideaId, userId, opinion

`POST /api/site/:SITE_ID/vote`
Create or update votes



## Voting types

Available voting types per site:

- likes
- count or count-per-theme
- budgeting or budgeting-per-theme

A site can have on type of voting active

If allowed by the parameter`config.votes.withExisting` voteType 'count' or 'budgeting' will replace old votes for same user.

The vote types *like* works as a toggle. Likes can have a positive, yes, and a negative, no, sentiment.

One voting round can be done on multiple ideas, if the user the votes again all previous votes for ideas are cancelled, or depending on the settings an error is thrown:

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

There are a multiple voting scenario's for different types of websites

- Submitting ideas website: people can submit ideas, and for every idea on the site it's possible to like positively or negatively. Voting the same sentiment cancels the vote, voting other sentiment cancels the vote and creates a new one
- Participatory budgeting: for budgeting site one vote is on multiple ideas within a set budget. So for instance there is 200.000 worth of budget then the users can select as many ideas as possible within that budget and make a vote on all of them
- Multiple votes: able to vote on a min and max amount of ideas
- Voting on an art or garden competition: max vote on one idea, but changeable
- Eberhard art project: max 1 vote, throw error on attempt to change



#### isViewable: false | true

Is the vote count publicly viewable. This can influence the voting process.

#### isActiveFrom: "ISODate" en isActiveTo: "ISODate"

Between what dates is voting allowed. Outside of these dates voting is closed.
The value in isActive overrules this. In other words: this only works if isActive is null.

#### isActive: null | false | true

If set to false voting is not active and trying to vote will result in an error.

#### requiredUserRole: "member" | "anonymous"

Voting is allowed for certain roles

#### withExisting: "error" | "replace"

This setting doesn't affect the vote type "likes".

#### voteType: 'likes' | 'count' | 'count-per-theme' | 'budgeting' | 'budgeting-per-theme'

See earlier in this doc

#### maxIdeas, minIdeas, 

Sets the amount of ideas allowed to vote on. So for instance minimum 1 idea and max 3 for one vote. A new vote by a user either replaces all ideas voted on of throws an error.

#### minBudget, maxBudget

For the vote type budgeting the min and max budget that the user is allowed to vote on should be set.

#### Example configuration

Submitting ideas phase:

```
{
  "isActive": true,
  "voteType": "likes",
  "isViewable": true,
  "withExisting": "replace",
}
```

Participatory budgeting:

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

