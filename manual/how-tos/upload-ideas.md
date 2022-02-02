# Inzendingen uploaden

Er zijn twee gebruiksgroepen die inzendingen willen uploaden. De eerste is bewoners, wanneer ze een plan willen indienen voor een begroot traject of een ontwerp voor een wedstrijd. De tweede groep is het projectteam van de gemeente zelf. Bewoners kunnen dan stemmen/hun voorkeur uitspreken/reageren op de inzendingen van de gemeente. Ook wanneer er een keuze aan bewoners wordt voorgelegd waarop gestemd kan worden, noemen we deze keuzeopties ook inzendingen. In het systeem worden ze namelijk op dezelfde manier gemaakt; met een _resource form._

Een [resource form](../modules/resource-form.md) is de widgets waarmee je inzendingen uploaden mogelijk maakt. Het is een formulier waarmee je een inzending kunt uploaden. Bewoners of de gemeente kunnen gebruik van het formulier maken. Lees in het widget hoofdstuk van _resource form_ hoe je het formulier aan kunt passen.

Na het maken van een resource form (de formulier wat bewoners/de gemeente gaat gebruiken), moet je de [inzendingen ook weergeven](show-ideas.md) zodat ze zichtbaar zijn voor gebruikers op de website. Dit wordt uitgelegd in het volgende how-to.

## Bewoners gaan inzendingen uploaden:

* Een veel gebruikte formulier is het [plan-indien](../../project-management/processes/participatory-budgeting.md#indienfase) formulier bij participatief begroten. Je kan hiervoor de [template ](new-site.md#template-website)gebruiken.&#x20;
* Ook kun je een eigen formulier maken met de widget [resource form.](../modules/resource-form.md)

### Admin panel instellingen

![Admin panel voor Ideas](https://lh4.googleusercontent.com/HcBH2BJoB2CsFtxOn4AsILWkwKJQEHNuzuzZRgJ50odZ92438sBPwNzsH1HPxb7gU\_PMKdmlcJxLIDmGRF2m7eLpZ\_AXFd9w8ZiOPaAYSS5b4ih7-x-mls1W5uTyaWP-upnX04ok)

| Instelling                                                                                   | Toelichting                                                                                                                                                                                                                                                                                                                                                                                                                |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Possible to send in ideas?                                                                   | <p>Aan: gebruikers kunnen inzendingen uploaden via het formulier. <br>Uit: gebruikers krijgen een foutmelding als ze inzendingen proberen te uploaden, omdat het formulier geen nieuwe inzendingen accepteert. (Als dit uit staat wil je, om verwarring te voorkomen, ook het formulier pagina <a href="new-page.md#nog-niet-publiceren">unpublishen </a>en verwijzingen naar het formulier verbergen of verwijderen).</p> |
| Minimum votes needed for idea?                                                               | Vul hierin het minimaal aantal likes dat een inzending moet hebben om door te gaan naar de volgende fase.                                                                                                                                                                                                                                                                                                                  |
| Min/max length of title, summary en description                                              | Vul hierin het minimum/maximum aantal karakters dat een inzending moet hebben bij het invullen van het formulier.                                                                                                                                                                                                                                                                                                          |
| Automatically update status from OPEN to CLOSED when an idea is a given number of days old.  | **Aan**: Vul het aantal dagen in wat je wil gebruiken. Hiermee kun je gebruik maken van bepaalde termijnen waarmee een status veranderd. Bijvoorbeeld: als je 90 dagen hebt om het minimum aantal likes te halen. **Uit**: je zal handmatig de [statussen ](../miscellaneous/idea-statuses.md)van inzendingen moeten aanpassen.                                                                                            |



### Thank you email

Een uploader van een inzending ontvangt automatisch een _thankyou_ email, dat de inzending is ingestuurd, op de email van zijn geregistreerde account (waarmee de inzending was geüpload).&#x20;

Het email kun je instellen in de [admin panel](../miscellaneous/adminpanel.md). Ga naar Settings > Ideas en scroll naar beneden voor het kopje _Thank you email._

![Thank you email weergave in het admin panel](<../../.gitbook/assets/image (3) (1).png>)

De email wordt geschreven in html. Hier staat een korte uitleg over als je klikt op _'More info on the E-mail Template'._

Indien je gebruik maakt van het template ['Plannen insturen'](new-site.md#template-website), staat er een email ingesteld met algemene informatie. Dit kun je aanpassen naar jouw projectgegevens.&#x20;

## Moderators gaan inzendingen uploaden

&#x20;<mark style="color:orange;"></mark> <mark style="color:orange;"></mark><mark style="color:orange;">**work in progress (**</mark><mark style="color:orange;">beperkte functionaliteit)</mark>

* <mark style="color:orange;">Admin panel</mark>
* <mark style="color:orange;">Formulier (verwijzen naar bewoner-beschrijving, formulier mogelijk unpublished laten)</mark>
