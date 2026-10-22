---
generated: '2026-10-22'
method: generated
name: fleetsu-export-ato-logbook
description: 'Produce ATO-compliant vehicle logbook data: list logbooks and their trips, then export as
  CSV or PDF.'
api: openapi/fleetsu-openapi.yml
operations:
- getV1Logbooks
- getV1LogbooksByLogbookid
- getV1LogbooksTrips
- getV1LogbooksTripsCsv
- getV1LogbooksByLogbookidPdf
source: Grounded in openapi/fleetsu-openapi.yml; every operationId verified verbatim in the spec. Conventions
  from the spec info.description.
---

# Export ato logbook

Produce ATO-compliant vehicle logbook data: list logbooks and their trips, then export as CSV or PDF.

## Auth
HTTP Basic authentication with a Fleetsu username and password (`Authorization: Basic ...`) against `https://api.fleetsu.com`. Send `Accept: application/json`. Unauthenticated requests return 401.

## Conventions
- Pagination: `_limit` (1-1000, default 200) and `_start`.
- Sorting: `_sort=field`, `_sort=!field` for descending.
- Filtering: exact, wildcard (`*`), comma-separated OR; datetimes accept ISO 8601 with `>`/`<` ranges and default to UTC.
- `_extend` appends related objects, and `_group` groups results.
- Write operations in this API use POST for both create and update. The provider documents no idempotency keys, so check for existing records before you create one.

## Steps
1. List logbooks with `getV1Logbooks`; open one with `getV1LogbooksByLogbookid`.
2. List logbook trips with `getV1LogbooksTrips`.
3. Export trips with `getV1LogbooksTripsCsv` or the logbook with `getV1LogbooksByLogbookidPdf`.

## Operations
- `getV1Logbooks` - GET /v1/logbooks
- `getV1LogbooksByLogbookid` - GET /v1/logbooks/{logbookId}
- `getV1LogbooksTrips` - GET /v1/logbooks/trips
- `getV1LogbooksTripsCsv` - GET /v1/logbooks/trips.csv
- `getV1LogbooksByLogbookidPdf` - GET /v1/logbooks/{logbookId}.pdf
