# Beheren van email templates en configuratie voor plannen
Wanneer er een nieuwe site is aangemaakt kan er gebruik worden gemaakt van de default mail templates voor plannen. In de meeste gevallen wil je dit echter overschrijven. Voor plannen zijn de volgende emails te bewerken:
- Definitief plan ingestuurd	
- Concept	plan ingestuurd
- Concept plan gepubliceerd (van concept naar definitief veranderd)	

## inzendingURL instellen voor gebruik in templates
De inzendingURL van een plan is de gecombineerde variabelen die bestaat uit de website url en het inzendingPath. Dit pad specificeert de plek in de site waar het plan te vinden is.
Het is essentieel om dit inzendingPath te specificeren mocht de wens er zijn om in een mailtemplate een link naar de betreffende op te nemen.
<img width="1155" alt="Screenshot 2023-05-03 at 14 45 20" src="https://user-images.githubusercontent.com/5735209/235919800-bb3a05c0-f883-438e-9611-cd39f6d05ef4.png">
Let hierbij op de conventie om het plan-id dynamisch in het pad te laten zetten {ideaId}

## Invoervelden op mailtemplates
Een email template blok bestaat uit een "From Adress", vanuit welk de email wordt verstuurd.
De "Subject line" specificeert het onderwerp van de mail die verstuurd wordt.
Met "Template" specificeer je de body van de mail. 
<img width="1069" alt="Screenshot 2023-05-03 at 14 33 32" src="https://user-images.githubusercontent.com/5735209/235917163-cf47e842-a321-41fd-9bd9-f2ae6edfbbee.png">

De volgende variabelen zijn te gebruiken in het template veld en worden vaak gebruikt:
- inzendingURL (de volledige url waar het plan te vinden is : {{inzendingURL}}
- URL (base url van de site inclusief https) : {{URL}}
- idea (het plan met alle velden die getoond kunnen worden) : {{idea.id}}
- SITENAME (De titel van de website) : {{SITENAME}}
- EMAIL (het adres waarmee mensen contact kunnen opnemen) : {{EMAIL}}
- HOSTNAME (De url van de website zonder https) : {{HOSTNAME}}
- user (De gebruiker, ingelogd of anoniem die het plan heeft ingedient) : {{user.fullName | default('indiener')}}

Een template zou i.c.m. bovenstaande er zo uit komen te zien:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<?xml encoding="utf-8" ?>
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{{SITENAME}}</title>

    <style type="text/css">
      ...styling;
    </style>
  </head>
  <body style="margin: 0; padding: 0; min-width: 100%">
    <table
      cellpadding="0"
      cellspacing="0"
      border="0"
      align="center"
      width="100%"
      id="backgroundTable"
      style="
        background-color: #fff;
        color: #000;
        font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
        font-size: 16px;
        width: 100%;
      "
    >
      <tr>
        <td></td>
        <td width="560">{% include 'logo.njk' %}</td>
        <td></td>
      </tr>
      <tr>
        <td></td>
        <td>
          {% if idea.extraData and idea.extraData.images %} {% for image in
          idea.extraData.images %}
          <img class="multipleImages" src="{{image}}" width="100%" /><br />
          {% endfor %} {% endif %}
        </td>
        <td></td>
      </tr>
      <tr>
        <td></td>
        <td width="560">
          <h2 class="blue">Bedankt voor uw CONCEPT plan!</h2>
        </td>
        <td></td>
      </tr>
      <tr>
        <td></td>
        <td width="560">
          <img
            src="https://westbegroot.amsterdam.nl/uploads/attachments/ck07xgjwz00pa2u3w6yvaclno-wb2020-headerfoto-2x-v2.full.png"
            width="560"
            style="display: block; width: 100%"
          />
          <h4>Beste {{user.fullName | default('indiener')}},</h4>

          U heeft een CONCEPT plan geplaats op {{SITENAME}}.<br />
          Uw plan is nog niet definitief ingediend. Vergeet niet om uw concept
          definitief te maken voor de deadline. U kunt het plan
          <b><a href="{{inzendingURL}}">hier</a></b> bewerken en indienen.<br />
          <br />

          <p style="margin-bottom: 3em; margin-top: 2em">
            Hartelijke groet,<br />
            Team {{SITENAME}}
          </p>
        </td>
        <td></td>
      </tr>
      <tr>
        <td></td>
        <td style="height: 15px; background-color: #787979" width="560"></td>
        <td></td>
      </tr>
      <tr>
        <td></td>
        <td style="text-align: center; height: 15px" width="560">
          <h4>
            <a href="{{URL}}" style="color: black; text-decoration: none"
              >{{HOSTNAME}}</a
            >
          </h4>
        </td>
        <td></td>
      </tr>
    </table>

    <br /><br style="display: block; clear: both" />
  </body>
</html>

```
