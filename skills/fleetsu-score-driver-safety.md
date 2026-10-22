---
generated: '2026-10-22'
method: generated
name: fleetsu-score-driver-safety
description: 'Assess driver behaviour: list drivers, get individual safety scores and the fleet-wide driver
  scores report.'
api: openapi/fleetsu-openapi.yml
operations:
- getV1Drivers
- getV1DriversByDriverid
- getV1DriversByDriveridScore
- getV1ReportsDriversScores
source: Grounded in openapi/fleetsu-openapi.yml; every operationId verified verbatim in the spec. Conventions
  from the spec info.description.
---

# Score driver safety

Assess driver behaviour: list drivers, get individual safety scores and the fleet-wide driver scores report.

## Auth
HTTP Basic authentication with a Fleetsu username and password (`Authorization: Basic ...`) against `https://api.fleetsu.com`. Send `Accept: application/json`. Unauthenticated requests return 401.

## Conventions
- Pagination: `_limit` (1-1000, default 200) and `_start`.
- Sorting: `_sort=field`, `_sort=!field` for descending.
- Filtering: exact, wildcard (`*`), comma-separated OR; datetimes accept ISO 8601 with `>`/`<` ranges and default to UTC.
- `_extend` appends related objects, and `_group` groups results.
- Write operations in this API use POST for both create and update. The provider documents no idempotency keys, so check for existing records before you create one.

## Steps
1. List drivers with `getV1Drivers`.
2. Get one driver with `getV1DriversByDriverid` and their score with `getV1DriversByDriveridScore`.
3. Compare across the fleet with `getV1ReportsDriversScores`.

## Operations
- `getV1Drivers` - GET /v1/drivers
- `getV1DriversByDriverid` - GET /v1/drivers/{driverId}
- `getV1DriversByDriveridScore` - GET /v1/drivers/{driverId}/score
- `getV1ReportsDriversScores` - GET /v1/reports/drivers/scores
