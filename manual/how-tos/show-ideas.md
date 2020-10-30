# Inzendingen weergeven

Er zijn grofweg twee verschillende manieren om inzendingen weer te geven:



*   Met enkel een overzichtspagina. Hierop staan alle inzendingen, bestaande uit een tegel voor elke inzending. Als je op een tegel klikt, wordt er middels een uitklapper binnen de overzichtspagina een beperkte hoeveelheid informatie getoond.
*   Met een combinatie van een overzichtspagina en een detailpagina. Op de detailpagina is ruimte voor uitgebreide gedetailleerde informatie van een enkele inzending. Er kan op een detailpagina ook een reactiemodule geplaatst worden, om website bezoekers te laten reageren op elke individuele inzending.


## Inzendingen overzichtspagina

Voor het weergeven van een overzicht van inzendingen wordt de ‘Resource overview’-widget [ TODO-LINK toevoegen naar widget ] gebruikt. Deze kan op verschillende manieren ingezet worden:



*   Als overzichtspagina van de inzendingen, waarbij de details van een inzending op een eigen detailpagina getoond worden.
*   Als overzichtspagina van de inzendingen, waarbij de details van een inzending in een ‘uitklapper’ zichtbaar worden binnen dezelfde overzichtspagina.
*   Als overzichtspagina van de inzendingen inclusief een stemmodule, waarbij op één van de inzendingen gestemd kan worden.

Zorg om te beginnen dat je een pagina hebt op welke het inzendingen overzicht getoond gaat worden [ TODO-LINK naar how-to om pagina’s te maken]. Voeg op deze pagina de ‘Resource overview’-widget [ TODO-LINK naar widget ] toe. De belangrijkste instellingen worden hieronder beschreven, afhankelijk van welke manier gewenst is.

[ TODO Let op: dit gaat alleen over het tonen van inzendingen. Als het gewenst is dat het een overzicht gecombineerd met stemfunctionaliteit is, kijk dan bij de ‘Stemmen’-how-to ]


### Overzichtspagina met losse detailpagina

In dit geval wordt er op de overzichtspagina voor elke inzending een tegel getoond, en kun je hier op klikken om doorgelinkt te worden naar een losse detailpagina waar de gehele inzending weergegeven wordt.

Om het overzicht op deze manier weer te geven zijn er drie instellingen van de ‘Resource overview’-widget belangrijk:



*   Enable voting: Kies voor ‘No’.
*   Display Type: Kies voor ‘Card in a row - linking to item on another page’.
*   Url structure for the resource: hier vul je de ‘slug’ [TODO-LINK naar slug onder Terminologie] van de detailpagina in, waar de tegel naartoe moet linken. Zorg dat dit overeenkomt met de URL van de detailpagina die je gaat gebruiken. Lees hierover meer onder het kopje ‘Inzending detailpagina’.

[TODO screenshot ]


### Overzichtspagina met uitklapper, zonder losse detailpagina

Ook hier wordt er op de overzichtspagina voor elke inzending een tegel getoond. Het verschil met bovenstaande manier, ‘Overzichtspagina met losse detailpagina’, is echter dat er niet wordt doorgelinkt naar een losse detailpagina als je op de tegel klikt. In plaats daarvan opent er onder de tegel, in de overzichtspagina zelf, een uitklapper met meer details van de inzending.

Om het overzicht op deze manier weer te geven zijn er twee instellingen van de ‘Resource overview’-widget belangrijk:



*   Enable voting: Kies voor ‘No’.
*   Display Type: Kies voor ‘Card in a grid - opens item into on the same page’ [TODO typo fixen]

[ TODO screenshot van uitklapper toevoegen]


### Overzichtspagina met uitklapper en stemmodule, zonder losse detailpagina

[ TODO misschien is het beter om dit onderdeel te verplaatsen naar de ‘Stemmen’-todo, zodat er een totaaloverzicht van alle stemmogelijkheden komt. Daar kan dan hiervandaan heen gelinkt worden ]

Deze manier is grotendeels hetzelfde als bovenstaande, ‘Overzichtspagina met uitklapper, zonder losse detailpagina’ [TODO - Als dit verplaatst wordt moet deze tekst anders]. Het verschil is dat er bovenaan het overzicht een stemmodule verschijnt, waarin op één van de inzendingen uit het overzicht gestemd kan worden. Elke inzending in het overzicht krijgt op zowel de tegel als in de uitklapper een ‘Stem’-knop.

Om het overzicht op deze manier weer te geven is er één instelling van de ‘Resource overview’-widget belangrijk:



*   Enable voting: Kies voor ‘Yes’.

[TODO screenshot stemmodule ]


## Inzending detailpagina

Dit is van toepassing als je hierboven, bij het kiezen van de opzet van de overzichtspagina, hebt gekozen om een losse detailpagina te gebruiken voor de uitgebreide details van een inzending (eerste optie). Zorg er voor dat je een pagina hebt waarop de detailpagina weergegeven wordt [TODO-LINK naar pagina’s toevoegen how-to]. In het instellingenscherm van een pagina zie je de ‘slug’, deze moet ingevuld worden in de ‘Resource overview’-widget [TODO-LINK naar widget toevoegen] onder ‘Url structure for the resource’, zoals hierboven ook beschreven.

Je kunt de detailpagina op twee manieren opbouwen:



*   In één vooraf bepaalde layout.
*   Opgebouwd uit losse elementen, waarbij je zelf de layout van de pagina vorm kunt geven.

Bij beide manieren gebruik je de ‘Resource representation’-widget. Lees meer over de verschillende mogelijkheden op deze pagina [TODO-LINK toevoegen].

Het is mogelijk om op de detailpagina ook een reactiemogelijkheid toe te voegen. Hoe dit moet wordt beschreven in de how-to ‘Reacties en argumenten’ [TODO-LINK naar how-to toevoegen].


## Ontwerp je eigen manier om plannen weer te geven

[TODO - Dit is nu nog gericht op de resource overview module alleen, maar moet ook de single variant bij komen ]

Deze module biedt de mogelijkheid om eigen templates te maken voor de overzichtspagina. Lees meer over deze functionaliteit onder Raw [ TODO-LINK naar Raw pagina onder Overig ] en bekijk de lijst met beschikbare variabelen in de Resource raw widget documentatie [ TODO-LINK toevoegen naar widget docs ].