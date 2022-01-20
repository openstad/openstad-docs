# Polygonen

Een polygon voeg je toe om de grenzen van een buurt/gebied/stad aan te geven. Dit wordt getoond in de widgets die een kaart gebruiken, bijvoorbeeld [ideeën op een kaart](../modules/ideeen-op-een-kaart-kaart-applicatie.md) en [ideas map](../modules/idea-map.md).&#x20;

## **Gebied tekenen om JSON code te maken**

Bepaal eerst wat de grenzen van het gebied zijn. Gebruik, indien nodig, kaarten of een database van de gemeente om de juiste grenzen te vinden. Vervolgens moet je die grenzen aangeven in JSON code. Dat werkt als volgt:

1. Ga naar de website: [https://geojson.io/](https://geojson.io). Op deze website ga je het gebied natekenen om de juiste code te kunnen downloaden.
2. Klik rechtsboven in de kaart op het vijfhoekige icoon

&#x20;

![Kaart tekenen](https://lh3.googleusercontent.com/TqZvJL0PV-Q1DgTEQkQYYG\_tKXPaalifvInmWfP8UiOw23xlTxBfyT9Y4TpHIPYUU7pxKX494vv6oEeQa7R3Bkt1OH2YQrcWYQHQnYPvNxqiCocbymp4paKyT-VxNmfpqcN3kE-r)

3\. Nu kun je door te klikken het gebied omcirkelen waar het om gaat. Eindig altijd door het beginpunt aan te klikken en hiermee de gebiedsgrens te ‘sluiten’. Een omcirkeld gebied ziet er zo uit:

![omcirkeld gebied in geojson](https://lh6.googleusercontent.com/Qv059qDMR3cEE0ypacpThuCwWlQUmSMFkDiIqkL9o9PiRumxmM50Vd-sqNuRDOBblPCVpyZSoFSSFaLDRx6fAKW1VPjLVWCufoSX\_jSWMVwkN5BOvL7Gl\_Cpm-Ra44uq3zymbL71)

4\. Controleer of het gebied klopt. Wanneer je niet tevreden bent met het gebied klik je op het bewerken icoon. Je kunt dan de stippen die je hebt gezet aanpassen.

![Bewerken icoon](https://lh6.googleusercontent.com/5hCidviX5dps\_RLNvTSjodEWrYAVV99sim3YHuLdB7Z0t39g7bwCLZtgjhZ6W-C6SJy4G3JUcM6Cu8J4gig3-m83LhZkjZ2UudvLB0HJt2YYlqJjgl9yX03DgD2GmSTSWJ5urNWW)

5\. Tevreden? Kopieer dan alle (JSON) code uit het rechter tabblad.

![gekozen gebied en JSON code](https://lh6.googleusercontent.com/sBtLAuzOw9SemXW6lp8C96-zBsACE7XI18sDcS1R3Us2qlG4\_quGA3Is4djfsBaqTj9l4N1VZCo\_ag3pSEnAerFwMVvQztyM6UV2q9uDI-f\_Aw-TwScXF5ZzKgKXDUCS7ZX1LfH8)

6\. Die code ziet er zo uit (maar is waarschijnlijk langer):

![voorbeeld json code](https://lh4.googleusercontent.com/zt9tXgqCQZXR0d4tbLqvp2d\_MIJ2h60JQyJpwmNVWUAJUe5JC17\_l9KoFdAoIH\_DD-jNv39pxRzQz5zrZTC2zkxMQBJO\_2xnl6adeNZ\_37uBa5X\_mmFN6PYudawooCPtDr-t3LWc)

## **De polygoon (JSON) code toevoegen aan het OpenStad CMS.**

1. Ga naar je site in het OpenStad CMS en ga naar het admin panel door /admin achter de URL te zetten.&#x20;

* Als je nog niet ingelogd bent als admin of editor, kun je dat nu doen.&#x20;
* Klik links in het admin panel op de tab ‘Polygonen’&#x20;
* Nu zie je een lijst met bestaande polygonen. **Let op: Verwijder niks uit deze lijst, want dan zijn de polygonen ook niet meer bruikbaar voor andere websites!**

![Overzicht van polygonen in de admin panel](https://lh4.googleusercontent.com/XBhzSkB47-Iuv15wr-qsw3ToLLF51Ia89Y7pjvS0MldJRoo2J9gXD8w\_SKCMd6dDD3mZ439B61ELjbF9PjXbJVJm5CnhHvoc8JguMIwRAsV-PamyjLVH6TBtzn5AuRFWslZ\_MB7u)

2\. Klik rechts bovenin op ‘create’ om jouw Polygon toe te voegen met de code die je gekopieerd hebt.

* &#x20;Kies een herkenbare naam voor de Polygon. Bijvoorbeeld \[Stadsdeel] - \[Wijknaam] → **Zuid - Buitenveldert, Zuidas.**

![Aanmaken nieuwe polygon](https://lh3.googleusercontent.com/9w1-b84\_NimSR-Dvy\_9KM9ZZmTLVV6tUAAQPhOrqnOzpX1QJivQqCme2IQm1k5k5-3-SK75qu8Uhyeq-xUVZsca1pzvVRvwChdFsxm466DPBnFYwSXpwGvUTM4Xmlm51xkdykBjz)

* Scroll naar beneden en plak jouw ‘JSON code’ in het zwarte vlak.

![vlak waar je de JSON code kan plakken](https://lh6.googleusercontent.com/oCs1V8q8RzNuu5DU5i-MnL31-pQgOWAUf87Ysu40KfaBnSOZtERqKfx-KrO1fg1cSWvLM8adcp7Xqm8V7\_\_J75tc3Qsw2lfBgbwwC-DyxnkPmzUJ08abIOR8SuIeJYmMBkJyfsuj)

* Klik op ‘Save’ en jouw Polygon is opgeslagen.



## Via global de juiste Polygon selecteren voor jouw site

Om nu de juiste Polygon te selecteren voor verschillende widgets, ga je naar Global > Map > en selecteer je bij ‘Selecteer een polygon’ de naam van de polygon die je zojuist toegevoegd hebt.

![](https://lh3.googleusercontent.com/Td8XlqcNtzBttt49O68YcU63clR63Q1tvLAxiWWhjuv2xUzKi6BYH0AANoeKuA3sMx8g\_h80jLcRKwVRcUnt-iEVtaNJWN-TmlQ0JfXO9IMGo0rG6PGYjhV\_M2FG0L\_dpbX9JR3G)
