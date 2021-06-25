# Choices Guide

The choices guide helps a visitor to form an idea or opinion by answering a set of questions and seeing the effect on a set of possible choices.

The basic idea is very simple: each question is answered by a visitor with a value between 0 and 100. Each *choice* has an answer stored, also between 0 and 100. Both answers are compared and the result shown.

Basic setup and configuration is described in https://docs.openstad.amsterdam/technical/components/use.html
```
   openstadcomponents['choices-guide'].ChoicesGuide.renderElement(element, config);
```
or
```
   OpenStadComponents['choices-guide'].ChoicesGuideResult.renderElement(element, config);
```

Once loaded and logged in as an admin you will find a button on the page that allows for creating questions and choices from within the component.

## Configuration

```
config = {
  divId: "choices-guide",
  siteId: 1,
  choicesGuideId: 1,
```

Number of questions per page
```
  noOfQuestionsToShow: 10,
```

Should the comparison start asuming that all questions are ansered at 50%
```
  startWithAllQuestionsAnswered: true,
```

Should a visitor answer each question or is the default answer enough
```
  startWithAllQuestionsAnsweredAndConfirmed: true,
```

How are the results shown
```
  choices: {
```

The way the results are shown: 'zero-to-100' (='default') or 'minus-to-plus-100' for a one dimensional view, 'plane' for two dimensional
```
    type: 'zero-to-100',
```

Colors used: 'default' is used by 'zero-to-100', 'min' and 'max' by 'minus-to-plus-100'
```
    barColor: { min: null, max: null, deafult: null }, // 
```

Header for the results block
```
    title: {
      noPreferenceYet: 'I have not yet made a choice',
      preference: '<b>My preference:</b><br/>{preferredChoice}',
      inBetween: 'My p[reference is in between choicesIk staat precies tussen meerdere voorkeuren in'
    },
```

```
  }
```

Urls that are used in the previous/next buttons
```
  beforeUrl: '/choices-guide/example.html?before',
  afterUrl: '/components/examples/choices-guide-result.html',
```

```
}
```

### Results

ChoicesGuideResults have extra configuration options
```
config = {
```

Show a number next to the result bars
```
  choices: {
    withPercentage: true,
  }
```

Submit the result to the api
```
  submission: {
```

Type describes what to do: 'none' does nothing, 'auto' sends the result to the api as soon as the page is shown, and 'form' waits for a form to be filled in and submitted.
```
    type: 'none',
```

See the [forms docs](./forms.md) for a description of these options
```
    form: {
    },
```

Optionally (in *edit choices guide*) you can require a user to be logged in before submitting the form
```
    requireLoginSettings: {
      title: "Stemcode",
      description: "Om te kunnen stemmen vul je de stemcode in die je per post hebt ontvangen. Wij controleren je stemcode op geldigheid. Als dat gelukt is kun je stemmen.",
      buttonTextLogin: "Vul je stemcode in",
      buttonTextLoggedIn: "Geldige stemcode",
      buttonTextAlreadySubmitted: "Ongeldige stemcode",
      changeLoginLinkText: "Vul een andere stemcode in",
      loggedInMessage: "Het controleren van je stemcode is gelukt! Klik op onderstaande knop om je keuze in te sturen.",
      notYetLoggedInError: "Klik hierboven om je stem te valideren.",
      alreadySubmittedMessage: "Deze stemcode is al gebruikt om te stemmen. Een stemcode kan maar één keer gebruikt worden.",
    },
```

```
  }
```


```
}
```

## Technical

### Datamodel

In pseude-json:

```
choices-guide: {
  title,
  decription,
  images,
  config,
  questionGroups: {
    title,
    decription,
    images,
    seqnr,
    answerDimensions,
    questions: {
      dimensions,
      minLable,
      maxLabel,
      title,
      decription,
      moreinfo,
      images,
      seqnr,
      type,
      values,
    },
    choices: {
      title,
      decription,
      images,
      seqnr,
      answers,
    },
    results: {
      extraData,
      result,
      userId,
      userFingerprint,
    }
  },
}
```

### Notes

Questions belong to a questionGroup.  
AnswerDimensions is used for a 2d view of the results; see (later)[#plane].

Posible choices are also part of the questiongroup. (The API knows choices on the top level, but this is not (yet) used by the frontend.)

Choices contain an answer to each question, to compare the visitors answers:

```
{
  2: 37, // the answer to question with id=2 is 37
  3:  5,
  7: 82
}

```

Results are stored per user, identified by a login or by a generated userFingerprint. The fingerprint system is not 100% fool proof. Data from an optional form with extra questions is stored as extraData.

### Plane

The two dimensional view on the results was created for a specific project.

The current implementation has limitations and should be reviewed/rebuild.

Documentation for this is not yet written. 