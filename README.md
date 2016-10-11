# Postleitzahlen

This repository contains the shapes of german postcode areas (Postleitzahlengebiete) in geojson format.


# Data Format

`data/postleitzahlen.geojson` - [GeoJSON](http://geojson.org) (RFC 7946)

# Filtering for ZIP-Codes

Using [jq](https://stedolan.github.io/jq/)

```
cat data/postleitzahlen.geojson|jq '.features[] | if (.properties.postcode == "80333" or .properties.postcode == "80335") then . else empty end'|jq -s . > ziptofence.json
```

# Mapshaper to merge them

Using [mapshaper](https://github.com/mbloch/mapshaper)

```
mapshaper -i ziptofence.json --dissolve -o format=geojson out.json
```

# Finale refinement easy through mapbox

[Mapbox.com](https://mapbox.com)

# Source

Extracted from [http://www.openstreetmap.org/](OpenStreetMap)
