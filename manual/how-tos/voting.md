# Stemmen

_Status: WIP_

Er worden verschillende manieren van stemmen op inzendingen/plannen/ideeën/ontwerpen ondersteund. Zie hieronder een overzicht van de verschillende stemmethoden en de bijbehorende widgets en instellingen die nodig zijn om dat voor elkaar te krijgen. De volgende manieren worden beschreven:



*   Maximaal één inzending/plan kunnen kiezen
*   Meerdere inzendingen/plannen kunnen kiezen, waaronder de volgende mogelijkheden vallen:
    *   Begroten, aantal inzendingen/plannen kiezen tot een _maximaal bedrag_
    *   Begroten per thema, aantal inzendingen/plannen kiezen tot een _maximaal bedrag binnen een thema_
    *   _Maximaal aantal_ inzendingen/plannen kiezen

Bij de beschrijvingen hieronder wordt er vanuit gegaan dat de inzendingen/plannen al in de database van de desbetreffende website zitten. Is dit nog niet het geval, lees dan hoe je dit doet in één van de volgende how-to’s:



*   Inzendingen uploaden [TODO-LINK]; als je zelf handmatig enkele inzendingen wil uploaden, of bewoners zelf inzendingen wil laten uploaden.
*   Plannen exporteren en importeren [TODO-LINK]; als je de plannen via een spreadsheet-overzicht wil importeren. Dit gebruik je ook als je in een eerdere fase van het proces met een andere website een (grote) hoeveelheid plannen hebt opgehaald.

Lees meer over complete participatieprocessen en de bijbehorende stappen onder ‘Participatieprocessen’ [TODO-LINK].

Het is daarnaast belangrijk om goed na te denken over de vorm van authenticatie die bij het stemproces gebruikt wordt. Lees meer over de mogelijkheden en overwegingen onder ‘Authenticatie methodes’ [TODO-LINK].

Het bekijken van de voortgang of eindstand van de uitgebrachte stemmen wordt apart beschreven in de how-to ‘(Tussentijdse) uitslag van stemmen/likes bekijken’ [TODO-LINK].


## Maximaal één inzending/plan kiezen

Deze manier van stemmen kan zowel gebruikt worden om bewoners één voorkeursvariant te laten kiezen tussen een relatief grote hoeveelheid opties (vaak ideeën/inzendingen van medebewoners), maar net zo goed uit een beperkte hoeveelheid keuzemogelijkheden (bijvoorbeeld 3 verschillende ontwerpen voor de herinrichting van een straat).

Voor deze methode wordt de ‘Resource overview’-widget [TODO-LINK] gebruikt (in tegenstelling tot de hieronder beschreven stemmethodes onder ‘Meerdere inzendingen/plannen kiezen’). Dit is de widget die ook gebruikt wordt om een inzending overzicht weer te geven zonder stemmogelijkheid. Lees hier meer over in de how-to ‘Inzendingen weergeven’ [TODO-LINK].

Plaats de ‘Resource overview’-widget [TODO-LINK] op een pagina. De volgende instelling is in dit geval de belangrijkste:



*   ‘Enable voting’: Afhankelijk of het stemproces wel of niet open is.
*   ‘Display Type’ (alleen beschikbaar als ‘Enable voting’ op ‘No’ staat): Kies voor ‘Card in a grid’ om de layout van de pagina overeen te laten komen met de situatie als ‘Enable voting’ wel op ‘Yes’ staat.

Lees meer over alle andere instellingen van de widget op deze pagina [TODO-LINK].

Er zijn daarnaast ook bepaalde instellingen in het admin-panel [TODO-LINK naar Admin-panel in Overig]. De volgende instellingen zijn in dit geval de belangrijkste:



*   Settings
    *   Voting
        *   ‘Is the vote count publicly available?’: Maak hier een bewuste keuze.
        *   ‘Is voting active?’: Afhankelijk of het stemproces wel of niet open is.
        *   ‘What type of voting is available?’: Kies voor ‘Count’.
        *   ‘What is min amount users can vote for?’: Vul in ‘1’.
        *   ‘What is max amount users can vote for?’: Vul in ‘1’.

Lees meer over deze en andere instellingen van het admin-panel op deze pagina [TODO-LINK].


## Meerdere inzendingen/plannen kiezen

Deze manier van stemmen wordt vaak gebruikt als er een relatief grote hoeveelheid inzendingen/plannen/ideeën is, waarvan bewoners kunnen kiezen welke daarvan tot uitvoering worden gebracht. De hoeveelheid inzendingen die uitgevoerd kunnen worden is vaak afhankelijk van het beschikbare budget en de kosten van elke individuele inzending.

Er worden hieronder drie verschillende varianten beschreven:



*   Begroten
*   Begroten per thema
*   Maximaal aantal kiezen

De variant die je kunt omschrijven als ‘Maximaal aantal per thema’ wordt op het moment van schrijven nog ontwikkeld.


### Begroten

Bij deze variant is er één budget beschikbaar voor alle inzendingen. Van elke inzending zijn de kosten bekend om het plan tot uitvoering te brengen. Bewoners kunnen inzendingen kiezen zolang de totale kosten van de gekozen inzendingen het beschikbare budget niet overschrijden. Als bewoners tevreden zijn over hun keuze en het stemproces afronden, krijgt elke door de bewoner gekozen inzending er één stem bij.

Voor deze methode wordt de ‘Participatory budgeting-’widget [TODO-LINK] gebruikt. Plaats deze widget op een pagina. De volgende instellingen zijn in dit geval de belangrijkste:



*   ‘Enable voting’: Afhankelijk of het stemproces wel of niet open is.

[ TODO volgende opsomming nog netjes verwerken in de documentatie ]



*   Gebruik de ‘Participatory budgeting’-widget, belangrijkste instellingen:
    *   Enable voting
    *   Voting type: Budgeting
    *   Available Budget
*   Adminpanel → Settings → Voting
    *   Is the vote count publicly available?
    *   Is voting active?
    *   What type of voting is available? : Budgeting
    *   What is min budget users can vote for?
    *   What is max budget users can vote for?
*   Let op: plannen moeten een budget hebben


### Begroten per thema

[ TODO volgende opsomming nog netjes verwerken in de documentatie ]



*   Gebruik de ‘Participatory budgeting’-widget, belangrijkste instellingen:
    *   Enable voting
    *   Voting type: Budgeting per thema
*   Global → Info → Thema’s. Voor elk thema:
    *   (Name)
    *   Wat is de kleur van dit thema (momenteel alleen voor Budgeting per thema): verwijzen naar HEX-kleuren
    *   Available Budget (momenteel alleen voor Budgeting per thema)
    *   Minimum budget that has to be selected (momenteel alleen voor Budgeting per thema)
*   Adminpanel
    *   Is the vote count publicly available?
    *   Is voting active?
    *   What type of voting is available? : Budgeting
    *   What is min budget users can vote for? → optellen!
    *   What is max budget users can vote for? → optellen!
*   Let op: plannen moeten een budget hebben
*   Let op: instellingen in global bij elk thema
    *   Budget
        *   Als je minimum instelt, moet dat bij elk thema gekozen worden. Deze foutmelding als je dat niet doet is niet logisch, ik denk niet eerder op deze manier gebruikt. 
    *   Kleurcode


### Maximaal aantal kiezen

[ TODO de volgende opsomming nog netjes verwerken in de documentatie ]



*   Gebruik de ‘Participatory budgeting’-widget, belangrijkste instellingen:
    *   Enable voting
    *   Voting type: Count
    *   Maximum selectable ideas
    *   Minimum selectable ideas
*   Adminpanel
    *   Is the vote count publicly available?
    *   Is voting active?
    *   What type of voting is available? : Count
    *   What is max amount of ideas users can vote for?
    *   What is min amount of ideas users can vote for?

[ TODO aantekeningen hieronder betreffende opzet documentatie verwerken ]

Onderscheid maken tussen het stemmen met de ideas-module en het stemmen met de begroot-module. Misschien opdelen in verschillende pagina's, zodat er direct naar de juiste pagina gelinkt kan worden vanuit de proces-beschrijvingen?

Ook beschrijven hoe de admin-panel instellingen moeten staan voor de verschillende stemprocessen

Ideas:



*   Hier wordt heen verwezen vanuit proces 'Wedstrijd'

Begroot:



*   Hier wordt heen verwezen vanuit proces 'Participatief begroten'
*   Verschillende mogelijkheden (budget, count, budget per thema)

Ook beschrijven hoe het aantal uitgebrachte stemmen bekenen kan worden (ook tijdens de stemperiode) TODO

Ook beschrijven hoe het stemproces gesloten kan worden. Inclusief het sluiten in het admin-panel.
