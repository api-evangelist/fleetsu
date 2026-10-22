---
generated: '2026-10-22'
method: generated
name: fleetsu-locate-fleet-assets
description: 'Find where fleet vehicles are now: list assets, get current locations, isolate moving/offline
  units and drill into one asset.'
api: openapi/fleetsu-openapi.yml
operations:
- getV1Assets
- getV1AssetsLocations
- getV1AssetsMoving
- getV1AssetsOffline
- getV1AssetsByAssetid
source: Grounded in openapi/fleetsu-openapi.yml; every operationId verified verbatim in the spec. Conventions
  from the spec info.description.
---

# Locate fleet assets

Find where fleet vehicles are now: list assets, get current locations, isolate moving/offline units and drill into one asset.

## Auth
HTTP Basic authentication with a Fleetsu username and password (`Authorization: Basic ...`) against `https://api.fleetsu.com`. Send `Accept: application/json`. Unauthenticated requests return 401.

## Conventions
- Pagination: `_limit` (1-1000, default 200) and `_start`.
- Sorting: `_sort=field`, `_sort=!field` for descending.
- Filtering: exact, wildcard (`*`), comma-separated OR; datetimes accept ISO 8601 with `>`/`<` ranges and default to UTC.
- `_extend` appends related objects, and `_group` groups results.
- Write operations in this API use POST for both create and update. The provider documents no idempotency keys, so check for existing records before you create one.

## Steps
1. List assets with `getV1Assets` (filter e.g. `?label=Truck*`, page with `_limit`/`_start`).
2. Get current positions with `getV1AssetsLocations`.
3. Narrow to units in motion with `getV1AssetsMoving` or to silent units with `getV1AssetsOffline`.
4. Fetch full detail for one unit with `getV1AssetsByAssetid`.

## Operations
- `getV1Assets` - GET /v1/assets
- `getV1AssetsLocations` - GET /v1/assets/locations
- `getV1AssetsMoving` - GET /v1/assets/moving
- `getV1AssetsOffline` - GET /v1/assets/offline
- `getV1AssetsByAssetid` - GET /v1/assets/{assetId}
