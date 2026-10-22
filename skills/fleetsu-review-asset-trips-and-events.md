---
generated: '2026-10-22'
method: generated
name: fleetsu-review-asset-trips-and-events
description: 'Reconstruct what an asset did over a period: its trips, its telematics events and the meaning
  of each event code.'
api: openapi/fleetsu-openapi.yml
operations:
- getV1AssetsByAssetidTrips
- getV1AssetsByAssetidEvents
- getV1EventsCodes
- getV1EventsByEventid
source: Grounded in openapi/fleetsu-openapi.yml; every operationId verified verbatim in the spec. Conventions
  from the spec info.description.
---

# Review asset trips and events

Reconstruct what an asset did over a period: its trips, its telematics events and the meaning of each event code.

## Auth
HTTP Basic authentication with a Fleetsu username and password (`Authorization: Basic ...`) against `https://api.fleetsu.com`. Send `Accept: application/json`. Unauthenticated requests return 401.

## Conventions
- Pagination: `_limit` (1-1000, default 200) and `_start`.
- Sorting: `_sort=field`, `_sort=!field` for descending.
- Filtering: exact, wildcard (`*`), comma-separated OR; datetimes accept ISO 8601 with `>`/`<` ranges and default to UTC.
- `_extend` appends related objects, and `_group` groups results.
- Write operations in this API use POST for both create and update. The provider documents no idempotency keys, so check for existing records before you create one.

## Steps
1. Pull trips for the asset with `getV1AssetsByAssetidTrips`, using a datetime range such as `?datetime=>2024-01-01T00:00:00Z,<2024-01-31T23:59:59Z`.
2. Pull events with `getV1AssetsByAssetidEvents`.
3. Resolve event codes against `getV1EventsCodes`.
4. Inspect any single event with `getV1EventsByEventid`.

## Operations
- `getV1AssetsByAssetidTrips` - GET /v1/assets/{assetId}/trips
- `getV1AssetsByAssetidEvents` - GET /v1/assets/{assetId}/events
- `getV1EventsCodes` - GET /v1/events/codes
- `getV1EventsByEventid` - GET /v1/events/{eventId}
