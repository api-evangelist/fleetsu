---
generated: '2026-10-22'
method: generated
name: fleetsu-manage-geofences
description: Create a geofence, attach assets to it, and report on entries and exits.
api: openapi/fleetsu-openapi.yml
operations:
- getV1Fences
- postV1Fences
- postV1FencesByFenceidAssets
- getV1FencesByFenceidAssets
- getV1ReportsFencesInteractions
source: Grounded in openapi/fleetsu-openapi.yml; every operationId verified verbatim in the spec. Conventions
  from the spec info.description.
---

# Manage geofences

Create a geofence, attach assets to it, and report on entries and exits.

## Auth
HTTP Basic authentication with a Fleetsu username and password (`Authorization: Basic ...`) against `https://api.fleetsu.com`. Send `Accept: application/json`. Unauthenticated requests return 401.

## Conventions
- Pagination: `_limit` (1-1000, default 200) and `_start`.
- Sorting: `_sort=field`, `_sort=!field` for descending.
- Filtering: exact, wildcard (`*`), comma-separated OR; datetimes accept ISO 8601 with `>`/`<` ranges and default to UTC.
- `_extend` appends related objects, and `_group` groups results.
- Write operations in this API use POST for both create and update. The provider documents no idempotency keys, so check for existing records before you create one.

## Steps
1. Check existing fences with `getV1Fences` to avoid duplicates.
2. Create the fence with `postV1Fences`.
3. Attach assets with `postV1FencesByFenceidAssets`; confirm with `getV1FencesByFenceidAssets`.
4. Report entries/exits with `getV1ReportsFencesInteractions`.

## Operations
- `getV1Fences` - GET /v1/fences
- `postV1Fences` - POST /v1/fences
- `postV1FencesByFenceidAssets` - POST /v1/fences/{fenceId}/assets
- `getV1FencesByFenceidAssets` - GET /v1/fences/{fenceId}/assets
- `getV1ReportsFencesInteractions` - GET /v1/reports/fences/interactions
