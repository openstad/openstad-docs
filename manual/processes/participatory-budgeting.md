# Participatief begroten - Opzetten digitale tools

_Status: WIP_

[TODO mogelijk opsplitsen in verschillende pagina's, één per fase]

[TODO er is vaak budget beschikbaar, waarvan de gemeente wil dat de bewoners bepalen wat hiermee gebeurt. ]

Een begroot process bestaat uit drie hoofdfasen.
1. [Indienfase](#indienfase)
2. [Tussenfase](#tussenfase)
3. [Stemfase](#stemfase)

Voorbeelden van het 'participatief begroten'-proces zijn te vinden onder de 'Use cases' op OpenStad.org. [TODO link naar het use cases overzicht toevoegen, en mogelijk hieronder een opsomming van specifieke use cases]


## Indienfase

> [Lees hier waar je in deze fase rekening mee moet houden wat betreft procesontwerp en projectmanagement](/processes/participatory-budgeting-PM.md#indienfase)

Tijdens de indienfase worden bewoners van een bepaald gebied uitgenodigd om ideeën die ze hebben voor hun buurt te uploaden. Bewoners dienen plannen in door middel van het invullen van een formulier op de website. De plannen kunnen ‘geliked’ worden en andere bewoners kunnen reacties plaatsen bij een plan. 


### Voorbereiding indienfase

Maak in het admin-panel [TODO link toevoegen] een nieuwe lege website aan en volg onderstaande how-to's om deze te vullen, of begin te werken vanuit een website waar de basisfunctionaliteit al werkt: [TODO toevoegen hoe en wat].

Voor het begin van deze fase zijn de volgende how-to's relevant:
* [Plannen indienen](../manual/how-tos/upload-ideas.md) - vraag bewoners in het formulier ten minste om een titel, samenvatting, beschrijving en afbeelding. Het vragen naar een locatie is vaak ook gewenst.
* [Plannen weergeven](../manual/how-tos/show-ideas.md) - kies voor de combinatie van overzicht- en detailweergave zodat er op de detailweergave-pagina argumenten geplaatst kunnen worden (zie volgende punt).
* [Reacties en argumenten](../manual/how-tos/arguments.md) - het is projectafhankelijk of er algemene reacties, of een scheiding tussen voor- en tegen-argumenten gewenst is.
* [Likes verzamelen](../manual/how-tos/like-ideas.md) - stel een stemdrempel in, en bekijk de herkomst van de likes om mogelijke fraude op te sporen. Lees hier ook hoe de mogelijkheid om plannen te liken uitgeschakeld kan worden.

### Gedurende de indienfase

Tijdens de indienfase zijn de volgende how-to's relevant:
* [Moderatie](../manual/how-tos/moderation.md)

### Afronding van de indienfase

Het sluiten van de indienfase bestaat uit twee stappen. Om de bewoners die op de laatste dag hun plan hebben ingediend nog de mogelijkheid te geven om voldoende likes te verzamelen, kan de mogelijkheid om plannen in te dienen (een week) eerder gesloten worden dan de mogelijkheid om likes te geven.

Het sluiten van de indienperiode gaat als volgt:
1. Pas de pagina's van de website aan, zodat het voor bezoekers duidelijk is dat er geen plannen meer ingediend kunnen worden, maar dat bezoekers de ingediende plannen nog wel kunnen liken.
2. Schakel in het admin-panel [TODO link en misschien meer uitleg toevoegen] uit dat er nog plannen ingediend kunnen worden, zodat dit ook aan de achterkant geblokkeerd wordt.

Het sluiten van de mogelijkheid om te liken gaat als volgt:
1. Pas de pagina's van de website aan, zodat het voor bezoekers duidelijk is dat ook de ingediende plannen niet meer geliked kunnen worden.
2. Wijzig de status van de ingediende plannen om het liken uit te schakelen. Hoe dit werkt is beschreven in de volgende how-to: [Likes verzamelen](../manual/how-tos/like-ideas.md)

## Tussenfase

> [Lees hier waar je in deze fase rekening mee moet houden wat betreft procesontwerp en projectmanagement](/processes/participatory-budgeting-PM.md#tussenfase)

[ TODO proces-beschrijving hier weghalen en doorverwijzen? ]


### Process

Omdat het belangrijk is in de stemfase alleen plannen voor te leggen die bij winst ook uitgevoerd kunnen worden, wordt er tussen het indienen en het stemmen een haalbaarheidstoets uitgevoerd door de gemeente. In deze haalbaarheidstoets worden de plannen getoets op criteria zoals: het plan leidt niet tot meerjarige of structurele kosten, het plan is technisch en juridisch uitvoerbaar, de begroting van het plan is realistisch en het plan is financieel haalbaar. Vaak raken plannen meerdere afdelingen binnen de gemeente en moeten er ambtearen samen komen om te discussiëren over de haalbaarheid van het plan, plan voor deze fase genoeg tijd. 

Mogelijk wordt er binnen de haalbare plannen nog een selectie gemaakt, om het totaal aantal plannen uiteindelijk op de stemsite wat te beperken. In deze fase blijft de indienwebsite zichtbaar voor het publiek. 


### Digitale tool

Er vanuit gaande dat er een behoorlijk bedrag beschikbaar is dat door bewoners verdeeld wordt, is het waarschijnlijk wenselijk dat bewoners kunnen stemmen met een unieke persoonlijke stemcode. Deze stemcodes moeten aangemaakt worden, en gecombineerd worden met gegevens uit de Basisregistratie Personen (BRP).

Voor deze fase zijn de volgende how-to's relevant:
* [Plannen exporteren en importeren](manual/how-tos/importing-plans.md) - lees hier hoe de plannen te exporteren zijn. Dit overzicht is handig bij de haalbaarheidstoetsen, en is een goede basis voor de spreadsheet die in de volgende fase nodig is om de verwerkte plannen weer te importeren.
* [Unieke stemcodes](manual/how-tos/voting-codes.md) - genereer unieke stemcodes, en lees tips om deze op de juiste manier te verwerken.

## Stemfase

> [Lees hier waar je in deze fase rekening mee moet houden wat betreft procesontwerp en projectmanagement](/processes/participatory-budgeting-PM.md#stemfase)

Voor deze fase wordt aan de achterkant een nieuwe website gebruikt. Dit heeft als voordeel dat de originele ingediende plannen van bewoners bewaard blijven en als archief kunnen dienen, terwijl op de stemsite alleen de plannen geplaatst worden die door zijn naar de stemfase. Deze plannen kunnen hier ook een aangepaste (kortere) beschrijving krijgen volgens een format dat bij alle plannen overeenkomt, zodat ze goed te vergelijken zijn. Een ander voordeel is dat deze website opgezet, gevuld en getest kan worden, terwijl voor bezoekers de indienwebsite nog zichtbaar is.

### Voorbereiding stemfase

Maak voor deze fase dus een nieuwe website aan in het admin-panel, of begin te werken vanuit een website waar de basisfunctionaliteit al werkt: [TODO toevoegen hoe en wat].

Voor deze fase zijn de volgende how-to's relevant:
* [Plannen exporteren en importeren](manual/how-tos/importing-plans.md) - importeer de verwerkte plannen uit de indienfase.
* [Stemmen](manual/how-tos/voting.md) - stel de stemmodule naar wens in.

### Gedurende de stemfase

Tijdens de stemfase zijn de volgende how-to's relevant:
* [Stemmen](manual/how-tos/voting.md) - bekijk de voortgang van de uitgebrachte stemmen.

### Afronding stemfase

Bij de afronding van de stemfase zijn de volgende how-to's relevant:
* [Stemmen](manual/how-tos/voting.md) - lees hoe je de stemfunctionaliteit kunt sluiten.

Vergeet niet de content van de pagina's aan te passen om bezoekers van de site duidelijk te maken dat de stemfase gesloten is.

### Uitslag

Voor de uitslag zijn de volgende how-to's relevant:

*   Nieuwsbrief - lees hoe je e-mail adressen verzameld van mensen die op de hoogte gehouden willen worden.
*   Plannen overview sorteren - Lees hier hoe je een selectie van de plannen kunt weergeven in resource overview. 
*   Files - lees hier hoe je een pdf kunt uploaden waar je via een link heen kunt navigeren. 

Pas de pagina’s aan om de uitslag bekend te maken.