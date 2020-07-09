# Participatief begroten

_Status: WIP_

[TODO er is vaak budget beschikbaar, waarvan de gemeente wil dat de bewoners bepalen wat hiermee gebeurt. ]

Dit proces bestaat uit verschillende fases. De twee belangrijkste zijn de indienfase en de stemfase. Maar ook daartussen is er een hoop werk te doen. In deze tussenfase wordt bijvoorbeeld de haalbaarheidstoets van de ingediende plannen gedaan, zodat er in de stemfase enkel plannen aan bewoners voorgelegd worden die ook daadwerkelijk uitgevoerd kunnen worden, en dat het bekend is hoeveel budget er voor de uitvoering van de plannen nodig is.

Voorbeelden van het 'participatief begroten'-proces zijn te vinden onder de 'Use cases' op OpenStad.org. [TODO link naar het use cases overzicht toevoegen, en mogelijk hieronder een opsomming van specifieke use cases]

## Indienfase
Tijdens de indienfase is het voor bewoners mogelijk om plannen te uploaden voor hun buurt in te dienen. Op deze plannen kan vervolgens gestemd worden zodat de gemeente weet hoeveel draagvlak er voor een plan is, voordat er tijd en geld gestoken wordt in een haalbaarheidsonderzoek. Ook kunnen andere bewoners reacties plaatsen bij een plan.

Maak in het admin-panel [TODO link toevoegen] een nieuwe lege website aan en volg onderstaande how-to's om deze te vullen, of begin te werken vanuit een website waar de basisfunctionaliteit al werkt: [TODO toevoegen hoe en wat].

Voor het begin van deze fase zijn de volgende how-to's relevant:
* [Plannen indienen](../manual/how-tos/upload-ideas.md) - vraag bewoners ten minste om een titel, samenvatting, beschrijving en afbeelding. Het vragen naar een locatie is vaak ook gewenst.
* [Plannen weergeven](../manual/how-tos/show-ideas.md) - kies voor de combinatie van overzicht- en detailweergave zodat er op de detailweergave-pagina argumenten geplaatst kunnen worden (zie volgende punt).
* [Reacties en argumenten](../manual/how-tos/arguments.md) - het is projectafhankelijk of er algemene reacties, of een scheiding tussen voor- en tegen-argumenten gewenst is.
* [Likes verzamelen](../manual/how-tos/like-ideas.md) - stel een stemdrempel in, en bekijk de herkomst van de likes om mogelijke fraude op te sporen. Lees hier ook hoe de mogelijkheid om plannen te liken uitgeschakeld kan worden.

Tijdens de indienfase zijn de volgende how-to's relevant:
* [Moderatie](../manual/how-tos/moderation.md)

Het sluiten van de indienfase bestaat uit twee stappen. Om de bewoners die op de laatste dag hun plan hebben ingediend nog de mogelijkheid te geven om voldoende likes te verzamelen, kan de mogelijkheid om plannen in te dienen eerder gesloten worden dan de mogelijkheid om likes te geven (met bijvoorbeeld een week ertussen).

Het sluiten van de indienperiode gaat als volgt:
1. Pas de pagina's van de website aan, zodat het voor bezoekers duidelijk is dat er geen plannen meer ingediend kunnen worden, maar dat bezoekers de ingediende plannen nog wel kunnen liken.
2. Schakel in het admin-panel [TODO link en misschien meer uitleg toevoegen] uit dat er nog plannen ingediend kunnen worden, zodat dit ook aan de achterkant geblokkeerd wordt.

Het sluiten van de mogelijkheid om te liken gaat als volgt:
1. Pas de pagina's van de website aan, zodat het voor bezoekers duidelijk is dat ook de ingediende plannen niet meer geliked kunnen worden.
2. Wijzig de status van de ingediende plannen om het liken uit te schakelen. Hoe dit werkt is beschreven in de volgende how-to: [Likes verzamelen](../manual/how-tos/like-ideas.md)

## Tussenfase
In deze fase blijft de indienwebsite zichtbaar voor het publiek. Tijdens de tussenfase worden de ingediende plannen (die de stemdrempel hebben gehaald) op haalbaarheid onderzocht. Mogelijk wordt er binnen de haalbare plannen nog een selectie gemaakt, om het totaal aantal plannen uiteindelijk op de stemsite wat te beperken.

Er vanuit gaande dat er een behoorlijk bedrag beschikbaar is dat door bewoners verdeeld wordt, is het waarschijnlijk wenselijk dat bewoners kunnen stemmen met een unieke persoonlijke stemcode. Deze stemcodes moeten aangemaakt worden, en gecombineerd worden met gegevens uit de Basisregistratie Personen (BRP).

Voor deze fase zijn de volgende how-to's relevant:
* [Plannen exporteren en importeren](manual/how-tos/importing-plans.md) - lees hier hoe de plannen te exporteren zijn. Dit overzicht is handig bij de haalbaarheidstoetsen, en is een goede basis voor de spreadsheet die in de volgende fase nodig is om de verwerkte plannen weer te importeren.
* [Unieke stemcodes](manual/how-tos/voting-codes.md) - genereer unieke stemcodes, en lees tips om deze op de juiste manier te verwerken.

## Stemfase
Voor deze fase wordt aan de achterkant een nieuwe website gebruikt. Dit heeft als voordeel dat de originele ingediende plannen van bewoners bewaard blijven en als archief kunnen dienen, terwijl op de stemsite alleen de plannen geplaatst worden die door zijn naar de stemfase. Deze plannen kunnen hier ook een aangepaste (kortere) beschrijving krijgen volgens een format dat bij alle plannen overeenkomt, zodat ze goed te vergelijken zijn. Een ander voordeel is dat deze website opgezet, gevuld en getest kan worden, terwijl voor bezoekers de indienwebsite nog zichtbaar is.

Maak voor deze fase dus een nieuwe website aan in het admin-panel, of begin te werken vanuit een website waar de basisfunctionaliteit al werkt: [TODO toevoegen hoe en wat].

Voor deze fase zijn de volgende how-to's relevant:
* [Plannen exporteren en importeren](manual/how-tos/importing-plans.md) - importeer de verwerkte plannen uit de indienfase.
* [Stemmen](manual/how-tos/voting.md) - stel de stemmodule naar wens in.

Het afsluiten van de stemmogelijkheid gaat als volgt:
1. Pas de pagina's van de website aan, zodat het voor bezoekers duidelijk is dat er niet meer gestemd kan worden.
2. Sluit het stemmen in het admin-panel, zodat dit ook aan de achterkant geblokkeerd is. [TODO link en meer uitleg toevoegen]