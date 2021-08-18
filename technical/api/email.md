# Email

The API sends a few type of e-mails.

## Confirmation after submitting an Idea or Article

After submitting an idea or an article an automatic *Thank you e-mail* is send to the user that submitted it.

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

Template uses the nunjucks templating engine, the following variables are available in the template:

- **user**: user object that created the Idea (see rest API for properties)
- **idea**: newly created Idea object (see rest API for properties)
- **HOSTNAME**: Hostname url of the site, same as  site.config.cms.hostname
- **SITENAME**: Name of the site, same as site.title
- **URL**: URL of the site, sames as site.config.cms.url,
- **EMAIL**: from adres (email only),
- **inzendingURL**: The url leading to the path, warning path should be set correctly in the config since CMS can change the page: site.config.cms.url + site.config.ideas.feedbackEmail.inzendingPath.replace(/\[\[ideaId\]\]/, idea.id),



## Notifications to Moderators

Notifications can be send to moderators to let them know if ideas and arguments have been created or edited on their site.

The e-mail template is also configurable per site:

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

The notifications are bundles and send periodically so arguments and ideas are an array.

Template uses the nunjucks templating engine, the following variables are available in the template.

- **data.idea**: an array van idea objecten, met de user included, en een 
- **inzendingURL** per idea
- **data.argument**: een array van argument objecten, met de user en idea included
- **HOSTNAME**: Hostname url of the site, same as  site.config.cms.hostname
- **SITENAME**: Name of the site, same as site.title
- **URL**: URL of the site, sames as site.config.cms.url


