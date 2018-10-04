# Import WFS to Elasticsearch


```bash
export ELASTICSEARCH_URL=https://elasticsearch.codeformuenster.org
export ELASTICSEARCH_INDEX_PREFIX=""
# export BUILD="--build"
export BUILD=""

sudo \
  ELASTICSEARCH_URL="https://elasticsearch.codeformuenster.org" \
  ELASTICSEARCH_INDEX_PREFIX="" \
  BUILD="" \
  ./import.sh

```


---
[old]

Before doing anything, you should do:
- fill the `config.json` file in their respective directories with life
  - `url`: the URL to the WFS 1.1.0 aufgrabungen server
  - `eSurl`: the URL to the Elasticsearch server with index and type
  - `baseUrl`: the URL stump to the WFS 2.0.0 for everything else
- run `yarn` in the respective directories before executing the scripts

## `districts`
Inserts the districts into an elasticsearch index indexed with `geo_shape`

## `aufgrabungen`
Inserts the construction sites into the places index. Execute with `node aufgrabungen-to-elasticsearch.js`

## `geojsonwfs`
Inserts the following feature classes into the places index.
- pool
- agencies
- bookbus
- library
- cemetery
- wc
- wifi
- school
- playground
- sport
- kindergarden

Execute with `node index.js`

## `sportstaetten-belegungsplan`
Inserts the booking plans of sports facilities in Münster. You need to pass the environment parameter `GOOGLE_API_KEY` (Google Maps API key) when running the import script `import_hallenbelegung.py`
