# 🇮🇹 osm-italy-routing-labels
[![Build Status](https://img.shields.io/github/actions/workflow/status/davixde/osm-italy-routing-labels/build.yml?style=for-the-badge&label=BUILD%20MAPPA)](https://github.com/davixde/osm-italy-routing-labels/actions/workflows/build.yml)
[![Docker Status](https://img.shields.io/github/actions/workflow/status/davixde/osm-italy-routing-labels/docker-build.yml?style=for-the-badge&label=DOCKER-PRECOMPILATO)](https://github.com/davixde/osm-italy-routing-labels/actions/workflows/docker-build.yml)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/davixde/osm-italy-routing-labels?style=for-the-badge&label=release&color=blue)](https://github.com/davixde/osm-italy-routing-labels/releases/latest)

GitHub Action che scarica periodicamente[^1] la [mappa d'Italia aggiornata da Geofabrik](https://download.geofabrik.de/europe/italy.html), la filtra con [Osmium](https://github.com/osmcode/osmium-tool) e la rilascia nei [Releases](https://github.com/davixde/osm-italy-routing-labels/releases)

Il risultato è un file ```.osm.pbf``` 11 volte più leggero, ottimizzato per la geocodifica e la ricerca di indirizzi con Nominatim.
Inoltre verrà anche generata una immagine Docker pre-compilata con il database già importato e pronto all'uso

### Query del filtro
```py
w/highway
r/boundary=administrative
r/boundary=postal_code
nwr/place
nwr/addr:*
```
[^1]: Settimanalmente, ogni lunedì alle 00:00 UTC
  
## Integrare la mappa
**Curl:**
```bash
curl -L -o data#.osm.pbf https://github.com/davixde/osm-italy-routing-labels/releases/download/v1.0.0/italia_leggera.osm.pbf
```


## Avviare Nominatim in locale con la mappa scaricata
> [!NOTE]
> Potrebbe richiedere da pochi minuti a diverse ore, a seconda delle prestazioni dell'hardware in uso.

**Requisiti:**
- Docker (avviato ed in esecuzione)
```bash
git clone https://github.com/davixde/osm-italy-routing-labels.git
cd osm-italy-routing-labels
```
- Avviamo il container
```bash
docker compose up -d
```
- (Opzionale) Scaricare [nominatim-ui](https://github.com/osm-search/nominatim-ui/releases)

## Avviare Nominatim tramite Immagine Docker Precompilata (Istantaneo)
Se non vuoi eseguire l'importazione locale (che richiede tempo e risorse hardware), puoi utilizzare l'immagine Docker precompilata con il database già popolato, ospitata su GitHub Container Registry:

```bash
docker run -d \
  --name nominatim-italy \
  -p 8080:8080 \
  ghcr.io/davixde/osm-italy-routing-labels:latest
```
Il container si avvierà in pochi secondi pronto a rispondere alle query di geocoding.

