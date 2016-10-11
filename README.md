# Postleitzahlen

This repository contains the shapes of german postcode areas (Postleitzahlengebiete) in geojson format.

# Data Format

## `data/postleitzahlen.geojson`

GeoJSON

# Filtering for ZIP-Codes

```
cat data/postleitzahlen.geojson|jq '.features[] | if (.properties.postcode == "80333" or .properties.postcode == "80335") then . else empty end'|jq -s . > ziptofence.json
```

## Mapshaper to merge them

```
mapshaper -i ziptofence.json --dissolve -o format=geojson out.json
```

# Source

Extracted from [http://www.openstreetmap.org/](OpenStreetMap)
