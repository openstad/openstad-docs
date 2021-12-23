# Interactieve kaart thema iconen

{% hint style="info" %}
Het gebruik van thema iconen op de kaart is een relatief technisch verhaal. In de toekomst zal dit gebruiksvriendelijker gemaakt worden, maar tot die tijd is er bepaalde kennis van webontwikkeling vereist.
{% endhint %}

Dit artikel is momenteel alleen van toepassing op de interactieve kaart, zie de how-to en widget referentie voor meer informatie:

{% content-ref url="../how-tos/interactieve-kaart.md" %}
[interactieve-kaart.md](../how-tos/interactieve-kaart.md)
{% endcontent-ref %}

{% content-ref url="../modules/ideeen-op-een-kaart-kaart-applicatie.md" %}
[ideeen-op-een-kaart-kaart-applicatie.md](../modules/ideeen-op-een-kaart-kaart-applicatie.md)
{% endcontent-ref %}

Daarnaast is dit artikel een aanvulling op het instellen van thema's op een website. De basis hiervoor wordt hier uitgelegd:

{% content-ref url="global.md" %}
[global.md](global.md)
{% endcontent-ref %}

Dit artikel gaat over de drie verschillende soorten iconen die in de interactieve kaart gebruikt worden; de markers die een inzending op de kaart aangeven, de icoontjes op de tegels in de lijstweergave, en de marker die een geselecteerde locatie op de kaart aan geeft.

![Twee verschillende soorten iconen in de interactieve kaart; links in de lijstweergave en rechts op de kaart.](<../../.gitbook/assets/Interactieve kaart - iconen.png>)

## Iconen definiëren

De iconen definieer je in het [JSON formaat](https://developer.mozilla.org/en-US/docs/Glossary/JSON).

Van alle iconen heeft het JSON object de volgende onderdelen:

| Key      | Toelichting                                                                                                                                                                                                            |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "html"   | De afbeelding van het icoon in [SVG formaat](https://developer.mozilla.org/en-US/docs/Web/SVG). Vul de SVG in als een string. Let op: de SVG string moet je [escapen](https://www.freeformatter.com/json-escape.html). |
| "width"  | De hoogte van het icoon in aantal pixels, als [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Number).                                                                      |
| "height" | De breedte van het icoon in aantal pixels, als [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Number).                                                                     |

In het geval van de inzendingen op de kaart en de geselecteerde-locatie-marker, is het ook nodig om het ankerpunt van het icoon aan te geven:

| Key      | Toelichting                                                                                                                                                                                                                                                                                                                      |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "anchor" | De positionering van het ankerpunt van de marker op de kaart, aangegeven met de x- en y-waarden in pixels, in een [array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array) van twee [numbers](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Number). |

In het geval van de geselecteerde-locatie-marker moet de volgende className toegeovegd worden:

| Key         | Waarde                  |
| ----------- | ----------------------- |
| "className" | "osc-ideas-on-map-icon" |

De iconen van inzendingen op de kaart en in de lijstweergave stel je in bij thema's in [global.md](global.md "mention"), de geselecteerde-locatie-marker geef je aan in de widget-instellingen onder [#kaart](../modules/ideeen-op-een-kaart-kaart-applicatie.md#kaart "mention").

### Voorbeelden

#### Icoon in lijstweergave

![](../../.gitbook/assets/icon-lijstweergave.svg)

```
{
  "html": "<svg xmlns=\"http://www.w3.org/2000/svg\" width=\"34\" height=\"34\" viewBox=\"0 0 34 34\">  <g fill=\"none\" fill-rule=\"evenodd\">    <circle cx=\"17\" cy=\"17\" r=\"17\" fill=\"#EC0000\" fill-rule=\"nonzero\"/>    <path fill=\"#FFF\" d=\"M22,19.5 C23.0355,19.5 23.875,20.3395 23.875,21.375 C23.875,22.4105 23.0355,23.25 22,23.25 C20.9645,23.25 20.125,22.4105 20.125,21.375 C20.125,20.3395 20.9645,19.5 22,19.5 Z M11.375,19.5 C12.4105,19.5 13.25,20.3395 13.25,21.375 C13.25,22.4105 12.4105,23.25 11.375,23.25 C10.3395,23.25 9.5,22.4105 9.5,21.375 C9.5,20.3395 10.3395,19.5 11.375,19.5 Z M18.875,11.375 L23.25,15.75 L27,15.75 L27,21.375 L25.125,21.375 C25.125,19.6491 23.7259,18.25 22,18.25 C20.2741,18.25 18.875,19.6491 18.875,21.375 L14.5,21.375 C14.5,19.6491 13.1009,18.25 11.375,18.25 C9.64911,18.25 8.25,19.6491 8.25,21.375 L7,21.375 L7,15.75 L11.375,11.375 L18.875,11.375 Z M18.25,12.625 L15.125,12.625 L15.125,15.75 L21.3512,15.75 L18.25,12.625 Z M13.875,12.625 L12,12.625 L8.875,15.75 L13.875,15.75 L13.875,12.625 Z\"/>  </g></svg>",
  "width": 34,
  "height": 34
}
```

#### Icoon op de kaart

![](../../.gitbook/assets/icon-kaart.svg)

```
{
  "html": "<svg xmlns=\"http://www.w3.org/2000/svg\" width=\"34\" height=\"45\" viewBox=\"0 0 34 45\">  <g fill=\"none\" fill-rule=\"evenodd\">    <path fill=\"#EC0000\" fill-rule=\"nonzero\" d=\"M17,0 C26.3917,0 34,7.53433 34,16.8347 C34,29.5249 19.3587,42.4714 18.7259,42.9841 L17,44.4938 L15.2741,42.9841 C14.6413,42.4714 0,29.5249 0,16.8347 C0,7.53575 7.60829,0 17,0 Z\"/>    <path fill=\"#FFF\" d=\"M22,19.5 C23.0355,19.5 23.875,20.3395 23.875,21.375 C23.875,22.4105 23.0355,23.25 22,23.25 C20.9645,23.25 20.125,22.4105 20.125,21.375 C20.125,20.3395 20.9645,19.5 22,19.5 Z M11.375,19.5 C12.4105,19.5 13.25,20.3395 13.25,21.375 C13.25,22.4105 12.4105,23.25 11.375,23.25 C10.3395,23.25 9.5,22.4105 9.5,21.375 C9.5,20.3395 10.3395,19.5 11.375,19.5 Z M18.875,11.375 L23.25,15.75 L27,15.75 L27,21.375 L25.125,21.375 C25.125,19.6491 23.7259,18.25 22,18.25 C20.2741,18.25 18.875,19.6491 18.875,21.375 L14.5,21.375 C14.5,19.6491 13.1009,18.25 11.375,18.25 C9.64911,18.25 8.25,19.6491 8.25,21.375 L7,21.375 L7,15.75 L11.375,11.375 L18.875,11.375 Z M18.25,12.625 L15.125,12.625 L15.125,15.75 L21.3512,15.75 L18.25,12.625 Z M13.875,12.625 L12,12.625 L8.875,15.75 L13.875,15.75 L13.875,12.625 Z\"/>  </g></svg>",
  "width": 34,
  "height": 45,
  "anchor": [17,45]
}
```
