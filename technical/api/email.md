# Email

The API sends a few type of e-mails.

## Confirmation after submitting an Idea

After submitting an idea an automatic Thank you e-mail is send to the user that submitted it.

By default this is a generic e-mail template. This can be customised per site in the config field of the Site model.

```
{
  "config": {
    "cms": {
      "url": "URL VAN DE WEBSITE"
    },
    "ideas": {
      "feedbackEmail": {
        "from": "NAAM <EMAIL@ADDRESS>",
        "subject": "ONDERWERP",
        "inzendingPath": "/PATH/NAAR/INGEDIEND/PLAN/[[ideaId]]",
        "template": "Beste {{user.fullName | default('indiener')}},<br/><br/>Bedankt voor je <a href=\"{{inzendingURL}}\">inzending</a>.<br/><br/>Groeten van het Project Team"
      }
    }
  }
}
```

Template is a nunjucks parameter

**user**: het user object van de inzender
**idea**: het idea object van de nieuwe inzending
**HOSTNAME**: site.config.cms.hostname,
**SITENAME**: site.title,
**URL**: site.config.cms.url,
**EMAIL**: from adres (email only),
**inzendingURL**: site.config.cms.url + site.config.ideas.feedbackEmail.inzendingPath.replace(/\[\[ideaId\]\]/, idea.id),

**TODO**
Misschien een config optie om dit uit te zetten?
Inline images?

## Notifications to Moderators

Notifications can be send to moderators for newly submitted ideas and updates to ideas.

Also possible to configure per site:

```
{
  "config": {
    "notifications": {
      "from": "NAAM <EMAIL@ADDRESS>",
      "to": "NAAM <EMAIL@ADDRESS>",
      "inzendingPath": "/PATH/NAAR/INGEDIEND/PLAN/[[ideaId]]",
      "template": "{% if data.idea %}{% for idea in data.idea %}{{idea.title}}{% endfor %}{% endif %}{% if data.argument %}{% for arg in data.argument %}{{arg.description | nl2br | safe}}{% endfor %}{% endif %}",
        "attachments": [{ filename: "FILENAME1", "cid": "CID1" }, { filename: "FILENAME2", "cid": "CID2" }]
    }
  }
}
```

Template is een nunjucks template - zie later in deze pagina. Daar zijn de volgende variabelen beschikbaar:

**data.idea**: een array van idea objecten, met de user included, en een **inzendingURL** per idea
**data.argument**: een array van argument objecten, met de user en idea included
**HOSTNAME**: site.config.cms.hostname
**SITENAME**: site.title
**URL**: site.config.cms.url

**TODO**
Misschien een config optie om dit uit te zetten?
Misschien een config optie om de frequentie te bepalen?
configureerbaar?
Subject configureerbaar?
Aparte templates voor ideas en arguments?
Inline images?

## Nunjucks templates

De email wordt opgemaakt met nunjucks; alle beschreven vars kunnen dus met nujucks syntax worden geinclude.
