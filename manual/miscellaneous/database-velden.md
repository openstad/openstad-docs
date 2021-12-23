# Database velden

{% hint style="info" %}
Sommige database velden beginnen met extraData. . Je bent zelf vrij om hier eigen velden aan toe te voegen. Deze data is niet zorgvuldig afgeschermd, dus zorg dat je dit niet gebruikt voor gevoelige informatie zoals persoonsgegevens.
{% endhint %}

| Database veld        | Toelichting                | Voorbeeld                                                              |
| -------------------- | -------------------------- | ---------------------------------------------------------------------- |
| id                   |                            |                                                                        |
| title                |                            |                                                                        |
| summary              |                            |                                                                        |
| description          |                            |                                                                        |
| status               |                            |                                                                        |
| budget               |                            |                                                                        |
| location             | JSON formaat               | `{"type":"Point","coordinates":[52.37307089425847,4.899129867553712]}` |
| extraData.images     | URL string(s) in een array | `["https://image.server.com/image/g46387tyg674"]`                      |
| extraData.area       |                            |                                                                        |
| extraData.theme      |                            |                                                                        |
| extraData.originalId |                            |                                                                        |
| ...                  |                            |                                                                        |
