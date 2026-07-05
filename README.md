

GitHub Action che scarica periodicamente la [mappa d'Italia aggiornata da Geofabrik](https://download.geofabrik.de/europe/italy.html), la filtra con [Osmium](https://github.com/osmcode/osmium-tool) e la rilascia pubblicamente. 
Il risultato è un file ```.osm.pbf``` 11 volte più leggero, ottimizzato per la geocodifica e la ricerca di indirizzi con Nominatim.

## Query del filtro
- w/highway
- r/boundary=administrative
- n/place
- ```nwr/addr``` (Qualsi elemento con il tag addr:*)


