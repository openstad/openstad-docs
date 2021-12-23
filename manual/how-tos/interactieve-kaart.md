# Interactieve kaart

## Gebruik van de kaart

De ‘interactieve kaart’-widget kan onder andere op de volgende manieren ingezet worden:

* **Ter informatie punten op de kaart tonen** - Plaats punten op de kaart en voeg hier een afbeelding en tekst aan toe.
* **Reacties op punten op de kaart uitvragen** - Plaats punten op de kaart, met afbeelding en tekst, en vraag gebruikers van de website om op deze punten te reageren.
* **Gebruikers zelf punten op de kaart laten plaatsen** - Vraag gebruikers om een locatie op de kaart te selecteren, en hier een afbeelding en tekst aan toe te voegen. Optioneel kunnen andere gebruikers hier weer op reageren.

## Indeling van de kaart

De indeling van de ‘interactieve kaart’-widget bestaat uit 3 hoofdonderdelen:

* **Kaart (C)** - aan de rechterkant wordt de kaart getoond, met daarop de punten die vooraf zijn ingeladen, of door gebruikers zijn geplaatst.
* **Contentvlak (B)** - het contentvlak aan de linkerkant bestaat uit twee onderdelen. Bovenaan het selectievlak met grijze achtergrond (B1), welke meer informatie geeft over een geselecteerde locatie of inzending. Er onder een lijstweergave met inzendingen (B2). Zie hieronder [#verschillende-weergaves](interactieve-kaart.md#verschillende-weergaves "mention") voor meer informatie over de inhoud van het selectievlak en de lijstweergave in verschillende omstandigheden.
* **Zoek- en filterbalk (A)** - uitgestrekt bovenaan de lijst- en kaartweergave bevindt zich in de overzichtsweergave een grijze balk met daarin optioneel een zoekveld, filter-dropdown en een knop om alle punten op de kaart weer in beeld te krijgen.

Hierboven is de lay-out op brede schermen beschreven, zoals desktop en tablet. Op smallere schermen, zoals mobiel, wordt óf de kaart óf het contentvlak op de volle breedte van het scherm getoond.

![Indeling van de widget: (A) Zoek- en filterbalk, (B1 en B2) contentvlak, (C) kaart.](<../../.gitbook/assets/Interactieve kaart indeling.png>)

## Verschillende weergaves

Er kunnen verschillende weergaves onderscheiden worden. Ten eerste is er een verschil tussen de _overzichtsweergave_ en de _detailweergave_.

In de _detailweergave_ wordt alle informatie behorend bij één specifiek punt op de kaart volledig getoond, met eventueel bijbehorende reacties.

![Detailweergave](<../../.gitbook/assets/Interactieve kaart - detailweergave.png>)

In de _overzichtsweergave_ worden meerdere punten op de kaart getoond. Dit kunnen alle punten zijn, maar het kan ook een selectie van alle punten zijn, bijvoorbeeld binnen een bepaald gebied en/of binnen een bepaald thema. Binnen de overzichtsweergave kunnen we nog 3 verschillende weergavemodi onderscheiden:

* **Niets geselecteerd** - dit is de weergave op het moment dat de widget vers geladen wordt. Op de kaart is niets geselecteerd. Optioneel wordt er in het grijze informatie/selectie-vlak algemene informatie getoond. In deze weergave kan dit vlak ook verborgen worden. Het contentvlak aan de linkerkant toont een lijst met tegels met alle punten die zichtbaar zijn op de kaart. Standaard worden bij het inladen van de widget alle punten op de kaart getoond, en worden deze dus ook in de lijst getoond. Als de gebruiker gaat inzoomen en schuiven met de kaart, dan kunnen er punten buiten de viewport vallen. Die punten verdwijnen ook uit de lijst. Oftewel; de lijst toont alleen de punten die op dat moment zichtbaar zijn op de kaart en dus binnen de viewport vallen. De gebruiker kan altijd terugkeren naar het totaaloverzicht door in de zoek- en filterbalk te klikken op de knop ‘Alles tonen’. Als de gebruiker klikt op een tegel in de lijst, dan opent de detailweergave van dat punt. Als de gebruiker klikt op een punt op de kaart, dan opent óf de detailweergave óf wordt de ‘punt geselecteerd’-weergavemodus getoond (zie hieronder), afhankelijk van de instellingen van de widget.
* **Punt geselecteerd (optioneel)** - als er op de kaart een (ingezonden) punt aangeklikt wordt, dan kan deze optioneel in de overzichtsweergave uitgelicht worden. In het contentvlak wordt dan bovenaan met grijze achtergrond het geselecteerde punt op de kaart als tegel getoond. Daaronder worden in de lijst de dichtstbijzijnde punten getoond, die dus geografisch het dichtst in de buurt liggen van het geselecteerde punt.
* **(Nieuwe) locatie geselecteerd** - dit is de weergavemodus als de gebruiker ergens op de kaart klikt, waar nog geen punt geplaatst is. In het contentvlak wordt een lijst met de dichtstbijzijnde punten vanaf de geselecteerde locatie getoond, vergelijkbaar met de ‘punt geselecteerd’-weergavemodus. Optioneel, afhankelijk van de instellingen van de widget, wordt er bovenaan in het contentvlak een knop getoond waarmee de gebruiker zelf op deze locatie een nieuw punt kan toevoegen aan de kaart.

![Niets geselecteerd](<../../.gitbook/assets/Interactieve kaart - niets geselecteerd.png>) ![Punt geselecteerd](<../../.gitbook/assets/Interactieve kaart - punt geselecteerd.png>) ![(Nieuwe) locatie geselecteerd](<../../.gitbook/assets/Interactieve kaart - locatie geselecteerd.png>)



## Interactieve kaart inzetten op een website

Om de interactieve kaart in te kunnen zetten op een website, is het belangrijk dat op verschillende plekken de juiste instellingen staan.

### Column section

Zoals elke widget, wordt ook de kaart geplaatst in een _column section_. Het is in het geval van de kaart belangrijk dat de volgende instellingen van de column section goed ingesteld zijn:

* **Columns**: Full screen (vertical & horizontal)

{% content-ref url="../modules/section-columns.md" %}
[section-columns.md](../modules/section-columns.md)
{% endcontent-ref %}

### Page Settings

In combinatie met de 'full screen'-instelling van de column section, is het ook belangrijk dat de cookiebar gefixeerd onderaan de pagina getoond wordt. Zorg dat in de _Page Settings_ van de pagina waarop je de kaart plaatst, het volgende staat ingesteld:

* **Hide the footer?**: Yes
* **Set the cookiebar fixed at the footer?**: Yes

{% content-ref url="../miscellaneous/page-settings.md" %}
[page-settings.md](../miscellaneous/page-settings.md)
{% endcontent-ref %}

### Global (optioneel)

Vanuit de globale instellingen van de website regel je twee verschillende zaken, die beide optioneel zijn; een _grens_ om een bepaald gebied af te kaderen, en de verschillende _thema's_ van de punten op de kaart.

Om een grens van een bepaald gebied aan te geven worden _polygonen_ gebruikt. Lees in de volgende artikel meer over het gebruik van polygonen:

{% content-ref url="polygonen.md" %}
[polygonen.md](polygonen.md)
{% endcontent-ref %}

Punten op de kaart kunnen gegroepeerd worden per thema, die je definieert in _Global_.

{% content-ref url="../miscellaneous/global.md" %}
[global.md](../miscellaneous/global.md)
{% endcontent-ref %}

In het geval van de interactieve kaart, kun je ook thema-specifieke iconen instellen. Lees meer in het volgende artikel:

{% content-ref url="../miscellaneous/interactieve-kaart-thema-iconen.md" %}
[interactieve-kaart-thema-iconen.md](../miscellaneous/interactieve-kaart-thema-iconen.md)
{% endcontent-ref %}

### 'Ideeën op een kaart'-widget

De rest van de instellingen definieer je in de _Ideeën op een kaart_-widget.

{% content-ref url="../modules/ideeen-op-een-kaart-kaart-applicatie.md" %}
[ideeen-op-een-kaart-kaart-applicatie.md](../modules/ideeen-op-een-kaart-kaart-applicatie.md)
{% endcontent-ref %}
