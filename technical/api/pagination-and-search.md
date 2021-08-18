# Pagination and search

## Middleware
All REST routes have pagination if the correct GET parameters are added to the URL on all GET list routes: Site, Idea, Article, Newslettersignup, Argument, Submission & Vote.
The heavy lifting is done by express middleware.

## Pagination parameters

If a query param `page` is used the results will be returned in pages. Optionally a param `pageSize` can be used; this defaults to 20.

The results will than be extended with some metadata:

```
{
  "metadata": {
    "page": 3,
    "pageSize": 20,
    "pageCount": 6,
    "totalCount": 118,
    "links": {
      "self": "/api/site/18/idea?page=3",
      "first": "/api/site/18/idea?page=0",
      "last": "/api/site/18/idea?page=5",
      "previous": "/api/site/18/idea?page=2",
      "next": "/api/site/18/idea?page=4"
    }
  },
  "records": [
    ... the results
  ]
}
```

Pagination is done in the database query. A request for 20 records from a table with 100000 should be fast.

But...

Search does not use the query because fuzzy SQL does not/hardly exist. Search will therefore be done on the results: it will fetch all 100000 records and search those in JS.

Pagination can than only be done after the searching of course, so this might be quite expensive.

## Search

Search requests are created with the query param `search`:

```
?search[text][criteria]=openstad&search[title][criteria]=goed&search[options][andOr]=and"
```

An npm module like ns will create an url like this form a nested js object.

```
{
  "criteria": [
    {
      "text": "openstad"
    },
    {
      "title": "goed idee"
    }
  ],
  "options": {
    "andOr": "and"
  }
}
```

Currently searches are recognized for `title`, `summary` en `description`. The value `text` will search in all three of these.

`andOr` should be self explanatory.

It may seem like overkill, but this way it should be really simple to add new ways of searching.

Searching itself is done by a module [fuzzysort](https://github.com/farzher/fuzzysort). This module adds scores to found values.
The results are sorted on this score; a hardcoded arbitrary minimum value determines if a result is included.

