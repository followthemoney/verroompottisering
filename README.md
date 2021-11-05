# Verroompottisering van de Nederlandse kust

Deze repository bevat uitleg, code en data over de 'verroompottisering' van de Nederlandse kust, een project van Follow the Money. Dit project is nog niet af. De aanname van het project is dat Nederlandse vakantieparken in handen komen van een steeds kleinere groep grote aanbieders. Bestaande parken worden opgekocht en de bewoners, die er soms al lange tijd verblijven, moeten dikwijls vertrekken om plaats te maken voor luxe vakantiewoningen. 

## De Data

De eerste stap is het verzamelen van data over vakantieparken in Nederland. Dat is minder makkelijk dan het lijkt, want deze overzichten bestaan niet, dus moeten we meerdere datasets combineren. 

**De data zijn afkomstig van:**
1. BAG: [Basisadministratie Adressen en Gebouwen](https://www.pdok.nl/introductie/-/article/basisregistratie-adressen-en-gebouwen-ba-1). Hierin staan bij sommige huizen ook een functie-omschrijving (in dit geval 'logies'). Deze dataset is niet compleet. 
2. BGT: [Basisadministratie Grootschalige Topografie](https://www.pdok.nl/introductie/-/article/basisregistratie-grootschalige-topografie-bgt-). Hierin staan vakantieparken, campings en caravanparken als gebieden ingetekend, meestal ook voorzien van een naam. Ook deze set is niet compleet, maar kan wel gebruikt worden om alle vakantiehuizen op die parken te vinden (bijvoorbeeld panden op die parken die in het BAG staan maar geen aanduiding 'logies' hebben). 
3. Handmatig intekenen. Van een aantal grote aanbieders hebben we op de website de locatie van parken opgezocht en vergeleken met het BGT en waar nodig zelf ingetekend op de kaart. Daar hebben we vervolgens ook de panden in geidentificeerd (in het BAG dus). Die aanbieders zijn: Roompot, EuroParcs Group, Landal, Center Parcs, RCN, Molecate en Ardoer. Deze eigendomsinformatie hebben we als veld toegevoegd bij de parken. Eventuele twijfels over de data staan aangegeven. 

**Deze datasets zijn verwerkt in [Qgis](https://www.qgis.org/en/site/) en levert een aantal shapefiles op:**
1. Parken in Nederland, voorzien van, voor zover bekend, naam, eigenaar, aantal huisjes, oudste huis, nieuwste huis, mediaan en gemiddelde van het bouwjaar, gemeentenaam en provincienaam.
2. We hebben ook nog een overzicht van huisjes op deze parken, met bouwjaar erbij. Het grote probleem is dat die overzichten niet compleet zijn. Dat ligt aan een incomplete basisadministratie. Deze set geven we later vrij als die meer compleet is. 

**Mogelijke data-issues om rekening mee te houden:**
1. We weten niet zeker of we alle parken hebben omdat zowel BAG als BGT niet compleet zijn. 
2. Sommige parken op de site van Roompot en andere aanbieders delen hetzelfde gebied (een locatie bevat bijvoorbeeld een park en een soort hotel die afzonderlijk op de site staan). 
3. Het intekenen van ontbrekende parken is gedaan op basis van achtergrondkaarten en luchtfoto's. Daarop zijn niet altijd duidelijk de grenzen van een park te zien. Dat betekent dat de daadwerkelijke oppervlakte iets kan afwijken. Waar dit onduidelijk blijft, is dat in het veld 'opmerkingen' vermeld. 
4. Bij de datasets met gemeente-informatie is geen rekening gehouden met gemeentelijke herindelingen. Tot nu toe heeft dat nog niet tot problemen geleid, maar het is wel iets om alert op te zijn. 
5. Heel belangrijk: er is een onderverdeling gemaakt in type park: nl bungalow, camping-, kampeer- en caravanterrein. In de praktijk zijn die grenzen boterzacht, want veel campings hebben huisjes. Caravanparken worden veranderd in bungalowparken, etc. Wees daarvan bewust. 
6. Het is bij Roompot niet altijd duidelijk wat het bedrijf bezit. Soms doet het alleen de exploitatie. In 2021 is het bijvoorbeeld een samenwerking aangegaan met BoerenBed. Die staat in deze dataset onder Roompot, maar het is dus geen bezit. Ze regelen, voor zover bekend, alleen (een deel van) de verhuur. Dus je zou moeten spreken over het gebied waar Roompot zeggenschap over heeft.
7. Eigenaar onbekend betekent niet dat daar niet achter te komen is. Het is in ieder geval niet een van de grote partijen en dus veel werk om het uit te zoeken en valt buiten de scope van dit onderzoek.

## Wat moet er nog gebeuren?
Er zijn nog allerlei manieren om de data te analyseren en databronnen te combineren die we nog niet hebben verkend. Enkele wensen:
1. Ruimtelijke analyses met locaties van parken, bestemmingsplannen en Natura2000-gebieden.
2. Veranderingen over tijd analyseren, bijvoorbeeld met behulp van heatmaps. 

Suggesties voor analyses en data zijn welkom. Feedback op de kwaliteit van de data uiteraard ook. 

## Zelf aan de slag? 
Dat vinden we uiteraard heel leuk. Er is een [shapefile met attributen beschikbaar](https://github.com/ftmnl/verroompottisering/tree/main/shapefiles). Graag worden we wel genoemd als bron en vergeet ook niet het BAG en BGT te noemen. Mocht je ermee aan de slag gaan, laat het ons ook even weten: we vinden het altijd interessant om te zien wat anderen met onze data kunnen doen. Er is ook een [notebook](https://github.com/ftmnl/verroompottisering/blob/main/notebooks/vakantiehuizen_analyse.ipynb) met een paar simpele analyses ter inspiratie. Uiteindelijk hebben we dit niet gebruikt. 
