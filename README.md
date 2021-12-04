# Verroompottisering van de Nederlandse kust

Deze repository bevat uitleg, code en data over de 'verroompottisering' van de Nederlandse kust, een project van Follow the Money. Dit project is nog niet af. De aanname van het project is dat Nederlandse vakantieparken in handen komen van een steeds kleinere groep grote aanbieders. Bestaande parken worden opgekocht en de bewoners, die er soms al lange tijd verblijven, moeten dikwijls vertrekken om plaats te maken voor luxe vakantiewoningen. Daarnaast worden ook vakantiehuizen in de natuur gebouwd, wat enorm lucratief is. FTM heeft hier een aantal vehalen over gemaakt:

1. [Wall Street aast op de Nederlandse camping](https://www.ftm.nl/artikelen/wall-street-aast-op-camping?utm_campaign=Dimitri-Tokmetzis&utm_source=article&utm_medium=link&share=LBHLucEJqkwRfZkGtIB81TrjjM35oM9b3l9zO1wdR3O7%2FTDQi6v7a%2F%2FMrkOGNjM%3D)
2. 

## De Data

De eerste stap is het verzamelen van data over vakantieparken in Nederland. Dat is minder makkelijk dan het lijkt, want deze overzichten bestaan niet, dus moeten we meerdere datasets combineren. 

**De data zijn afkomstig van:**
1. BAG: [Basisadministratie Adressen en Gebouwen](https://www.pdok.nl/introductie/-/article/basisregistratie-adressen-en-gebouwen-ba-1). Hierin staan bij sommige huizen ook een functie-omschrijving (in dit geval 'logies'). Deze dataset is niet compleet. 
2. BGT: [Basisadministratie Grootschalige Topografie](https://www.pdok.nl/introductie/-/article/basisregistratie-grootschalige-topografie-bgt-). Hierin staan vakantieparken, campings en caravanparken als gebieden ingetekend, meestal ook voorzien van een naam. Ook deze set is niet compleet, maar kan wel gebruikt worden om alle vakantiehuizen op die parken te vinden (bijvoorbeeld panden op die parken die in het BAG staan maar geen aanduiding 'logies' hebben). 
3. Handmatig intekenen. Van een aantal grote aanbieders hebben we op de website de locatie van parken opgezocht en vergeleken met het BGT en waar nodig zelf ingetekend op de kaart. Daar hebben we vervolgens ook de panden in geidentificeerd (in het BAG dus). Die aanbieders zijn: Roompot, EuroParcs Group, Landal, Center Parcs, RCN, Molecate en Ardoer. Deze eigendomsinformatie hebben we als veld toegevoegd bij de parken. Eventuele twijfels over de data staan aangegeven. 
4. Een overzicht van natuurgebieden in Nederland. In dit geval is gekozen voor [Natuurnetwerk Nederland](https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/c7d8d77b-8c47-4309-8c58-9b12b086407f) en [Natura2000](https://www.pdok.nl/introductie/-/article/beschermde-gebieden-natura2000-inspire-geharmoniseerd).

**Deze datasets zijn verwerkt in [Qgis](https://www.qgis.org/en/site/) en levert een aantal shapefiles op:**
1. Parken in Nederland, voorzien van, voor zover bekend, naam, eigenaar, aantal huisjes, oudste huis, nieuwste huis, mediaan en gemiddelde van het bouwjaar, gemeentenaam en provincienaam.
2. We hebben ook nog een overzicht van huisjes op deze parken, met bouwjaar erbij. Het grote probleem is dat die overzichten niet compleet zijn. Dat ligt aan een incomplete basisadministratie. Deze set geven we later vrij als die meer compleet is. 
3. Een shapefile met de natuurgebieden in Nederland (Natura2000 en Natuurnetwerk Nederland).
4. Een shapefile met huisjes die in de natuurgebieden liggen.

**Mogelijke data-issues om rekening mee te houden:**
1. We weten niet zeker of we alle parken hebben omdat zowel BAG als BGT niet compleet zijn. 
2. Verschillende parken delen soms hetzelfde gebied. Dat komt doordat er bijvoorbeeld een hotel, of aparte huisjes op een vakantiepark staan die onder een andere naam worden verhuurd. We hebben zoveel mogelijk de vermeldingen op de websites aangehouden. 
3. Het intekenen van ontbrekende parken is gedaan op basis van achtergrondkaarten en luchtfoto's. Daarop zijn niet altijd duidelijk de grenzen van een park te zien. Dat betekent dat de daadwerkelijke oppervlakte iets kan afwijken. Waar dit onduidelijk blijft, is dat in het veld 'opmerkingen' vermeld. We hebben altijd geprobeerd zo conservatief mogelijk in te tekenen.
4. Er is geen rekening gehouden met gemeentelijke herindelingen. Tot nu toe heeft dat nog niet tot problemen geleid, maar het is wel iets om alert op te zijn. 
5. Heel belangrijk: er is een onderverdeling gemaakt in type park:  bungalow, camping-, kampeer- en caravanterrein. In de praktijk zijn die grenzen boterzacht, want veel campings hebben huisjes, op sommige parken kun je ook kamperen. Caravanparken worden veranderd in bungalowparken, etc. En dit veranderd continu. Wees daarvan bewust. 
6. Het is op de site van Roompot niet duidelijk wat het bedrijf precies bezit. Soms doet het alleen de exploitatie. In 2021 is het bijvoorbeeld een samenwerking aangegaan met BoerenBed. Die staat in deze dataset onder Roompot, maar het is dus geen bezit. Ze regelen, voor zover bekend, alleen (een deel van) de verhuur. Dus je zou moeten spreken over het gebied waar Roompot een vorm van zeggenschap over heeft.
7. Eigenaar onbekend betekent niet dat daar niet achter te komen is. Het is in ieder geval niet een van de grote partijen en dus veel werk om het uit te zoeken en valt buiten de scope van dit onderzoek.
8. Deze set is een combinatie van verschillende datasets waarbij er allerlei attributen zijn gecombineerd en ruimtelijke 'joins' hebben plaatsgevonden. We hebben er alles aan gedaan om de data zo goed mogelijk te krijgen, maar er kunnen altijd nog fouten in zitten. Zo bleek een van de parken waar Roompot huizen op exploiteerde recentelijk failliet te zijn gegaan. Daarbij: nieuwsberichten zijn schaars en vaak onbetrouwbaar is onze ervaring. 
9. Met Natura2000 en Natuurnetwerk Nederland hebben we niet alle natuurgebieden in Nederland genomen. Er zijn ook nog provinciale beschermde gebieden, maar iedere provincie heeft daar weer andere regels voor, wat het vergelijken bemoeilijkt. Ook zijn er beschermde wetlands en nationale parken, maar die worden qua oppervlakte vrijwel volledig bedekt door Natura2000 of het natuurnetwerk en is dus vooral dubbelop.
10. Voor de selectie van huisjes die in de natuurgebieden staan zijn we zo strikt mogelijk geweest. Een huisje moet een actieve status in het BAG hebben. Dit om te voorkomen dat we huisjes meetellen die inmiddels gesloopt of herbouwd zijn. Bij een steekproef bleken huisjes zonder een actieve status wel op recente luchtfoto's te staan. In werkelijkheid zijn er dus meer huisjes, maar het is erg veel werk om na te gaan welke dat precies zijn. Door tijdbeperkingen hebben we besloten dat niet te doen. 

## Wat moet er nog gebeuren?
Er zijn nog allerlei manieren om de data te analyseren en databronnen te combineren die we nog niet hebben verkend. Enkele wensen:
1. Ruimtelijke analyses met locaties van parken, bestemmingsplannen en Natura2000-gebieden.
2. Veranderingen over tijd analyseren, bijvoorbeeld met behulp van heatmaps. 
3. De data zou idealiter in een PostGIS database gestopt worden om dubbelingen, etc. te voorkomen. Dat staat nog op de planning.

Suggesties voor analyses en data zijn welkom. Feedback op de kwaliteit van de data uiteraard ook. 

## Zelf aan de slag? 
Dat vinden we uiteraard heel leuk. Er is een [shapefile met attributen beschikbaar](https://github.com/ftmnl/verroompottisering/tree/main/shapefiles). Graag worden we wel genoemd als bron en vergeet ook niet het BAG en BGT te noemen. Mocht je ermee aan de slag gaan, laat het ons ook even weten: we vinden het altijd interessant om te zien wat anderen met onze data kunnen doen. Er is ook een [notebook](https://github.com/ftmnl/verroompottisering/blob/main/notebooks/vakantiehuizen_analyse.ipynb) met een paar simpele analyses ter inspiratie. Uiteindelijk hebben we dit niet gebruikt. 
