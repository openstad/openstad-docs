#Importen van plannen (ideas)

Het is ook mogelijk om plannen up te loaden. Dit wordt onder andere gebruikt als burgers plannen hebben upgeload en op een nieuwe site en deze, lees meer bij usecases hoe dit gebruikt wordt.

## Updaten via een import
Importen kan via een CSV bestand. De bekende excel programma's kunnen exporteren naar CSV. De export verwacht dezelfde headers als de import, dit zijn:

- id	
- siteId	
- meetingId	
- status	
- title	
- summary	
- description	
- budget	
- location	
- modBreak	
- modBreakUserId	
- modBreakDate	
- extraData.area	
- extraData.theme	
- extraData.role	
- extraData.estimate
- extraData.images 

##Fouten bij importeren door validatie
Het kan gebeuren dat er bij importeren iets misgaat. Dit gebeurd bijvoorbeeld als een plan niet aan de ingestelde validatie regels voldoet.

##Formaat fouten bij importeren
Het geaccepteerde formaat voor importeren is CSV (comma seperated values) of TSV (tab seperated values). Excel, number (mac) en google drive kunnen allen exporteren naar dit formaat. In sommige gevallen gaat dit mis omdat een andere teken gebruikt wordt dan een comma. Bijv een ;. Dit kan je aangeven

##Gekke tekens na importeren
Het kan gebeuren dat na importeren (of exporteren) ineens gekke characters verschijnen. Dit heeft er mee te maken dat er verschillende "charsets" bestaan.
In dit geval kies bij importeren (of exporteren) gekozen wordt voor utf-8,
