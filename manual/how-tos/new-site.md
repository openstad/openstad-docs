# Nieuwe site aanmaken

Er zijn drie verschillende manieren om een nieuwe site aan te maken:
- [Een standaard template kiezen](#template-website) - dit kan ook een lege website zijn
- [Een bestaande website kopieëren](#kopie-van-bestaande-site)
- [Een bestaande website via een extern bestand exporteren en importeren](#exporteren-en-importeren)

## Template website

Door een nieuwe website te maken op basis van een template, kun je van start gaan met een site die al gevuld en ingesteld is voor een bepaald proces. Het is via deze route ook mogelijk om een lege website aan te maken.

Er zijn vier template websites beschikbaar:
- **Lege site** - begin from scratch met het inrichten van een nieuwe site.
- **'Plannen insturen'-site** - kan gebruikt worden voor de _indienfase_ van het [Participatief begroten](/project-management/processes/participatory-budgeting.md)-proces.
- **'Participatief begroten'-site** - kan gebruikt worden voor de _stemfase_ van het [Participatief begroten](/project-management/processes/participatory-budgeting.md)-proces.
- **'Stem'-site** - kan gebruikt worden voor het [Voorkeurspeiling](/project-management/processes/poll.md)-proces.

Om één van deze templates te gebruiken moet je in het [adminpanel](/manual/miscellaneous/adminpanel.md) rechtsboven op _Maak nieuwe site aan_ klikken. Je krijgt dan een formulier waar je de volgende velden moet invullen:
- **Naam van de website** - de titel die in het adminpanel gebruikt wordt om naar de website te refereren, deze hoeft niet overeen te komen met de titel die op de website zelf gebruikt wordt.
- **Domeinnaam** - de domeinnaam waarop de website bereikbaar moet worden. Deze kan later nog aangepast worden.
- **Type site** - kies welke template je als basis voor de website wil gebruiken, zie hierboven het overzicht van de beschikbare templates.
- **E-mail instellingen** - er kunnen verschillende e-mails verzonden worden vanuit de website. Je kunt hier de naam en het e-mail adres opgeven dat als afzender van deze mails getoond moet worden.

Klik vervolgens onderaan het formulier op _Site aanmaken_. Je komt daarna direct op het [dashboard](/manual/miscellaneous/adminpanel.md#dashboard) van de nieuwe website terecht.

## Kopie van bestaande site

Met deze functie kan er een kopie gemaakt worden van een site die al in het huidige [adminpanel](/manual/miscellaneous/adminpanel.md) bestaat.

Om een site te kopieëren druk je in het [adminpanel](/manual/miscellaneous/adminpanel.md) rechtsboven op _Kopieer site_. Je krijgt dan een formulier waar je de volgende velden moet invullen:
- **Naam van de website** - de titel die in het adminpanel gebruikt wordt om naar de website te refereren, deze hoeft niet overeen te komen met de titel die op de website zelf gebruikt wordt.
- **Domeinnaam** - de domeinnaam waarop de website bereikbaar moet worden. Deze kan later nog aangepast worden.
- **Kies site om te kopieren** - kies welke website je wil kopieëren.
- **E-mail instellingen** - er kunnen verschillende e-mails verzonden worden vanuit de website. Je kunt hier de naam en het e-mail adres opgeven dat als afzender van deze mails getoond moet worden.

Klik vervolgens onderaan het formulier op _Site aanmaken_. Je komt daarna direct op het [dashboard](/manual/miscellaneous/adminpanel.md#dashboard) van de nieuwe website terecht.

## Exporteren en importeren

Via deze functie kunnen er websites uitgewisseld worden tussen verschillende omgevingen. Dit kunnen verschillende installaties van de OpenStad-software zijn bij bijvoorbeeld andere gemeenten, maar het kunnen ook verschillende test- en productie-omgevingen zijn op dezelfde server.

### Exporteren van een website

Zoeken binnen het [adminpanel](/manual/miscellaneous/adminpanel.md) de website op die je wenst te exporteren, en klik vervolgens op _beheer_ (dus niet _beheer (beta)_) om het [dashboard](/manual/miscellaneous/adminpanel.md#dashboard) van de website te openen. In het menu aan de linkerkant zie je de optie _Export_.

Op het moment van schrijven kun je kiezen om de volgende elementen mee te exporteren:
- **CMS attachments** - Dit zijn bestanden die aan de website gekoppeld zijn, hier vallen ook afbeeldingen onder. **Let op**: Door deze optie aan te vinken kan het bestand dat geëxporteerd wordt erg groot worden.
- **Choices Guides** - Dit zijn de instellingen van de Keuzewijzer.

Klik vervolgens op _Export_ om de website op te slaan in het *.tgz bestandsformaat.

### Importeren van een website

Zodra je een *.tgz-bestand van een OpenStad-website hebt, kun je deze in een andere omgeving importeren. Ga hiervoor naar het [adminpanel](/manual/miscellaneous/adminpanel.md) en kies rechtsboven voor _Importeer site_. Je krijgt dan een formulier waar je de volgende velden moet invullen:
- **Naam van de website** - de titel die in het adminpanel gebruikt wordt om naar de website te refereren, deze hoeft niet overeen te komen met de titel die op de website zelf gebruikt wordt.
- **Selecteer bestand** - Kies hier het *.tgz-bestand van de OpenStad-website.
- **Domeinnaam** - de domeinnaam waarop de website bereikbaar moet worden. Deze kan later nog aangepast worden.

Klik vervolgens onderaan het formulier op _Import_. Je komt daarna direct op het [dashboard](/manual/miscellaneous/adminpanel.md#dashboard) van de nieuwe website terecht.
