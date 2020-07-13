# Newsletter Signup

The newsletter signup allows for signing up people for a newsletter. No sending of e-mail of managing subscriber status is done after signing up.
```
{
  "config": {
    "newslettersignup": {
      "isActive": true
    }
  }
}
```

## Endpoint

`GET /api/site/:SITE_ID/newslettersignup`
List all newsletter signups for a site
Query params: confirmed

Alleen beschikbaar voor admins

`POST /api/site/:SITE_ID/newslettersignup`
Create a newslettersignup

## Signup confirm (beta)

There is the possibility to send an e-mail and let the user confirm the signup. This is however in Beta and being currently used and tested.

WIP: Dutch will be corrected/

Optionele extra params zijn `autoConfirm` (default false), `confirmationEmail.from`, `confirmationEmail.subject` en `confirmationEmail.template`. Template is een nunjucksTemplate; zie [Email](/doc/email) voor meer informatie.

Deze staat open voor iedereen. Als je een ingelogde gebruiker bent dan wordt je aanmelding ook direct geconcirmed. Als je niet bent ingelogd dan wordt er een email verstuurd waarmee je moet confirmen.

Als je bent aangemeld zonder ingelogd te zijn, en je dan nog eens aanmeld terwijl je wel bent ingelogd, dan wordt je alsnog geconfirmed.

Voor het confirmen wordt een token gegenereerd. Dat wordt meegegeven in de email.
Ook voor het afmeden wordt een token gegenereerd. Dat zou bij elke verstuurde nieuwsbriief moeten worden toegevoegd, want een afmeldlink is wettelijk verplicht.

`POST /api/site/:SITE_ID/confirm`

Payload:
```
{
  "confirmToken": "TOKEN"
}
```

Bevestig een aanmelding. Open voor iedereen; het token geeft je rechten.


`POST /api/site/:SITE_ID/signout`

Payload:
```
{
  "signoutToken": "TOKEN"
}
```

Meld je af. Open voor iedereen; het token geeft je rechten.


`PUT /api/site/:SITE_ID/newslettersignup/:NEWSLETTERSIGNUP_ID`
Update a newslettersignup

Alleen voor admins

`DELETE /api/site/:SITE_ID/newslettersignup/:NEWSLETTERSIGNUP_ID`
Delete a newslettersignup

Alleen voor admins.

