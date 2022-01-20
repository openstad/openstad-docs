# Resource form

Met de widget Resource form creëer je een formulier waarmee gebruikers een [inzending kunnen insturen](../how-tos/upload-ideas.md).

## Widget settings

In resource form zijn er verschillende settings voor elk vraag die je kan stellen in het formulier. Een aantal vragen zitten er standaard in, maar je kan altijd meer toevoegen of vragen weghalen.&#x20;

![Overview resource form widget](https://lh6.googleusercontent.com/8I3mkv2NgQju5IkkG986nq3eWcwVuSmDP7hzNZrOOyAFvnoYE4yVAD18aabskPhZbjKTMVDKm3F-oStw19b\_Z8kB29YyFIS0anka0hON8lujnuepoLjyS\_cB7AiBulMEDc\_rBS5Z)

### Algemeen

| Instelling                                    | Toelichting                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Resource (from config)                        | <p><strong>Idea:</strong> dit gebruik je voor verschillende formulieren waarin bewoners inzendingen insturen. <br><strong>Article user: TODO, vanuit moderators?</strong><br><strong>Resource: TODO</strong><br><strong>Resource user: TODO</strong></p>                                                                                                                                                                                                                                                                                                                                                                         |
| Redirect after submit                         | Op welke pagina komen gebruikers terercht wanneer ze iets hebben ingezonden? Als je wilt dat ze hun eigen ingestuurde plan zien (in een planindien template website), vul dan in: /plan/:id                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| <mark style="color:orange;">Login text</mark> | TODO kan je leeg laten?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| How do you want to organise the form?         | <p><strong>Static (default)</strong>: je gebruikt de default vragen voor het type resource form die je gebruikt. Bij 'ideas', zijn dat bijvoorbeeld vragen om een plan in te dienen voor een participatief begroten proces.<br><strong>Static with dynamic fields appended</strong>: je gebruikt (een aantal van) de default vragen in het formulier en je voegt nieuwe vragen daar aan toe</p><p><strong>Dynamic</strong>: je bouwt je eigen vragen en gebruikt geen default vragen van het formulier. <br>Lees meer over dynamic appended &#x26; dynamic <a href="resource-form.md#nieuwe-vragen-toevoegen">hieronder</a>.</p> |

### Instellingen die er voor elke vraag zijn

|                        | Toelichting                                                                                                                                                                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label for \[naam]      | De naam van jouw vraag. Wordt weergegeven in bold, grote tekst.                                                                                                                                                                    |
| Info for \[naam]       | Extra toelichting over jouw vraag, om te kunnen uitleggen waarom je dit vraagt/wat je precies wilt weten.                                                                                                                          |
| This field is required | <p><strong>Yes</strong>: dit is een verplichte vraag, en indieners zullen een melding krijgen dat ze dit veld eerst moeten invullen voordat ze een plan kunnen insturen.<br><strong>No</strong>: dit is geen verplichte vraag.</p> |

Zo zien vragen er dan ongeveer uit. Met aanvullende instellingen kun je ook een aantal default vragen nog aanpassen.&#x20;

![Voorbeeld vragen](https://lh3.googleusercontent.com/WzbWotX43qlkCPcPPYz3Sf9fgVFd8iSUC9XKYFlepugC5NzudrpQSmwfc0cIItTS1nn\_V3oL--EZknUdEfpdguxaObBc9Ts51DqxbXpunWcX34uejTmhXIfSRQlEboQD2fMCPtvP)

### Aanvullende instellingen

|                                                                              | Toelichting                                                                                                                                                                                                                                                                                                                             |
| ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Field type                                                                   | <p><em>Onderdeel van: summary, estimate costs</em><br><em></em><strong>Text area:</strong> grotere veld om in te vullen, geschikt voor langere tekst<br><strong>Text bar</strong>: een veld van 1 regel, geschikt voor kortere tekst</p>                                                                                                |
| Use text editor                                                              | <p><em>Onderdeel van:</em> <em>description</em><br><em></em><strong>Yes</strong>: gebruikers kunnen hun tekst vormgeven met titels, bold, italics, hyperlinks, bulletpoints, genummerde lijst, en indents.<br><strong>Nee:</strong> gebruikers kunnen platte tekst invullen.</p>                                                        |
| Allow multiple images to be uploaded                                         | <p><em>Onderdeel van: images</em><br><em></em><strong>Yes</strong>: maakt het mogelijk om meerdere afbeeldingen toe te voegen. Let op: de standaard resource overview (hoe het ingediende plan wordt getoond) is niet ingericht voor meerdere afbeeldingen<br><strong>No</strong>: alleen 1 afbeelding kan worden toegevoegd</p>        |
| Display location                                                             | <p><em>Onderdeel van: location</em><br><em></em><strong>Yes</strong>: gebruikers krijgen deze vraag te zien<br><strong>No</strong>: gebruikers krijgen deze vraag niet te zien (vergeet dan niet om het niet verplicht te maken)</p>                                                                                                    |
| Minimum/maximum number of characters needed                                  | <p><em>Onderdeel van: estimate costs, role, phone, tip</em><br>Vul hier het minimum of het maximum aantal karakters in voor het formulier veld. <br>Let op: wil je een min of max instellen voor title, summary of description? Pas dat aan via de <a href="../miscellaneous/adminpanel.md">adminpanel</a> > Site settings > ideas.</p> |
| Text for button to submit/save                                               | <p><em>Onderdeel van: submitting</em><br><em></em><strong>To submit:</strong> tekst op de button wat mensen moeten klikken om hun inzending in te sturen<br><strong>To save:</strong> tekst op de button wat mensen moeten klikken om hun inzending op te slaan. Vaak niet van toepassing en kan je dus leeg laten.</p>                 |
| <mark style="color:orange;">Display budget for moderators?</mark>            | <p><em>Onderdeel van: budget</em><br><em>TODO ik weet niet precies wat dit doet</em></p>                                                                                                                                                                                                                                                |
| <mark style="color:orange;">Hide admin after the first public action?</mark> | <p><em>Onderdeel van: info</em><br><em>TODO ik weet niet precies wat dit doet</em></p>                                                                                                                                                                                                                                                  |

### Nieuwe vragen toevoegen

De widget is standaard ingericht met bepaalde vragen. Dit zijn vragen die je vaak gebruikt bij een participatief begroten proces, waarbij indieners een aantal basis dingen moeten toelichten over hun plan of initiatief.&#x20;

Maar je kunt ook nieuwe vragen toevoegen. Pas eerst de organisatie van het formulier aan: [Algemeen ](resource-form.md#algemeen)> How do you want to organise the form > Static with dynamic fields appended **of** Dynamic.&#x20;

![Nieuwe vragen toevoegen via Form Sections](https://lh5.googleusercontent.com/laEAqbl9dzXsE-QlLJD4p9hQ7xaT7EnU1jhrWVlcJmywBKN8Z7yKBt4KalmG1hXRzxtQs2NVpR36kaGBVg8Vy0ObXy\_23ZjU-kXG5e7FsyBmO6rgxFN8ezMaKtK4l6twhVAuy7Q5)

Om nieuwe vragen toe te voegen, klik je op Edit Form Sections. Geef je nieuwe vraag een titel. Vul eventueel Info in met een toelichting over de vraag.

![Naam invulen nieuwe vraag](https://lh4.googleusercontent.com/0deJrfwsPhByRttVqwE3AECVG6ur2K8H2hB8T2iC0AVXIAzSCadZHNnPPfjHJh7SxvRM1aSRh4D4IWmprWX373zk2SDv2CvtzyC5fOs902qmC9BxCvEokykqXC9kVZoRAFzi\_5rZ)

Vervolgens geef je jouw nieuwe vraag vorm door te klikken op Form fields > Edit form fields.

![Editing form fields](https://lh3.googleusercontent.com/5eSvXco2gepEU96VhV5XYj64nVM-AFcgNdxs1ITAvBou-yCnsJ8EmCQHq8OuXuovQ1fRkM2o535tBo\_iVvX6\_mCqgU-KB7ZLX79SphSHHf-YOjzwaul0Q7rO2qOEJRnbHKoSZhUf)

### Instellingen van Form Fields

|                                                                                                                                         | Toelichting                                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Type                                                                                                                                    |                                                                                                                                                                                                                                                  |
| Key (one word) for example: ‘summary’ (for storing, must be unique, no spaces and special characters)                                   | Dit wordt de categorie van de antwoorden. In de excel/csv resultaten die je uiteindelijk krijgt, zul je de antwoorden op deze vraag onder deze key vinden.                                                                                       |
| Info                                                                                                                                    | Dit is extra ruimte om de vraag toe te lichten.                                                                                                                                                                                                  |
| Required                                                                                                                                | Is de vraag verplicht, ja of nee?                                                                                                                                                                                                                |
| Minimum/maximum length                                                                                                                  | Vul hier het minimum of het maximum aantal karakters in voor het formulier veld.                                                                                                                                                                 |
| <mark style="color:orange;">Save field in root if data object and not in extraData, will only work if column exists in database)</mark> | TODO hou deze op No?                                                                                                                                                                                                                             |
| Only show to moderators                                                                                                                 | <p><em><mark style="color:orange;">Yes: de antwoorden op deze vraag worden alleen zichtbaar voor moderators?</mark></em><br><em><mark style="color:orange;">No: de antwoorden op deze vraag zijn zichtbaar voor alle gebruikers?</mark></em></p> |

{% hint style="warning" %}
Let op: Extra vragen die je zelf inricht zijn ongeschikt voor het opvragen/verzamelen van persoonsgegevens. Gebruik hiervoor alleen de hiervoor gebouwde vragen.
{% endhint %}

{% hint style="info" %}
De extra vragen die je via de resource form toevoegt worden zichtbaar in het formulier voor gebruikers. Om ze ook zichtbaar te maken in het resource representation (de weergave van ingezonden inzendingen) moet je daar ook wat aanpassingen maken. Lees meer in [resource representation](resource-representation.md).
{% endhint %}
