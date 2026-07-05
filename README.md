# osm-italy-routing-labels
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/davixde/osm-italy-routing-labels/build.yml?style=for-the-badge&label=Action)](https://github.com/davixde/osm-italy-routing-labels/actions)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/davixde/osm-italy-routing-labels?style=for-the-badge&label=release&color=blue)](https://github.com/davixde/osm-italy-routing-labels/releases/latest)

GitHub Action che scarica periodicamente[^1] la [mappa d'Italia aggiornata da Geofabrik](https://download.geofabrik.de/europe/italy.html), la filtra con [Osmium](https://github.com/osmcode/osmium-tool) e la rilascia pubblicamente. 

Il risultato è un file ```.osm.pbf``` 11 volte più leggero, ottimizzato per la geocodifica e la ricerca di indirizzi con Nominatim.

## Query del filtro
```py
w/highway
r/boundary=administrative
n/place
nwr/addr
```
[^1]: Settimanalmente, ogni lunedì alle 00:00 UTC

## Scaricare la mappa
### Curl
```curl -L -o data#.osm.pbf https://github.com/davixde/osm-italy-routing-labels/releases/download/v1.0.0/italia_leggera.osm.pbf```
