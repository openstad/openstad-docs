# Choices Guide

## Content
- [Endpoints](#endpoints)

## Endpoints

List choicesguides
```
GET /api/site/:SITE_ID/choicesguide
```

Get 1 choicesguide
```
GET /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID
```

Get 1 choicesguide with all content
```
GET /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID?&includeChoices=1&includeQuestions=1
```

Create a choicesguide
```
POST /api/site/:SITE_ID/choicesguide

{
  "title": "My First Choices Guide",
  "description": "This Is An Example"
}
```

Update a choicesguide
```
PUT /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID

{
  "title": "My first choices guide",
  "description": "This is an example"
}
```

Delete a choicesguide
```
DELETE /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID
```

---

Create a choicesguide questiongroup
```
POST /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/questiongroup

{
  "title": "My First Question Group",
  "description": "This Is An Example"
}
```

Update a choicesguide questiongroup
```
PUT /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/questiongroup/:QUESTIONGROUP_ID

{
  "title": "My first question group",
  "description": "This is an example"
}
```

Delete a choicesguide questiongroup
```
DELETE /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/questiongroup/QUESTIONGROUP_ID
```

---

Create a choicesguide question
```
POST /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/questiongroup/:QUESTIONGROUP_ID/question

{
  "title": "First Question",
  "description": "This Is An Example",
  "type": "continuous"
}
```

Update a choicesguide question
```
PUT /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/questiongroup/:QUESTIONGROUP_ID/question/:QUESTION_ID

{
  "title": "First question",
  "description": "This is an example",
  "type": "enum-radio",
  "values": [
    {
      "text": "This is option 1",
      "value": 0
    },
    {
      "text": "This is option 2",
      "value": 33
    },
    {
      "text": "This is option 3",
      "value": 67
    },
    {
      "text": "This is option 4",
      "value": 100
    }
  ]
}
```

Delete a choicesguide question
```
DELETE /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/questiongroup/:QUESTIONGROUP_ID/question/:QUESTION_ID
```

---

Create a choicesguide choice
```
POST /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/choice

{
  "title": "Choice one",
  "description": "Choive one has answerd 0 on all questions",
  "answers": {
    "2": 0,
    "3": 0,
    "4": 0,
    "5": 0,
    "6": 0
  }
}
```

Update a choicesguide choice
```
PUT /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/questiongroup/1/choice/:CHOICE_ID

{
  "title": "Choice one",
  "description": "Choive one has answerd 50 on all questions",
  "answers": {
    "2": 50,
    "3": 50,
    "4": 50,
    "5": 50,
    "6": 50
  }
}
```

Delete a choicesguide choice
```
DELETE /api/site/:SITE_ID/choicesguide/:CHOICESGUIDE_ID/choice/:CHOICE_ID
```

---

