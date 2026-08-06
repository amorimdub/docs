# Workspace Record Store

**Last verified:** 2026-07-17

The Workspace Record Store is a simple place for a Workspace to keep structured JSON facts that automations, AI Clients, and Members can push, get, and review over time.

It is not a general database product. You do not write query languages, design table schemas, browse spreadsheet-style grids, or treat Records as Company Files. A Collection holds JSON Records; CompanyOS stores full-snapshot revision history for each Record when you ask for history.

## Concepts

- **Collection** — a named Workspace container for related JSON Records. Only an Owner can create a Collection. An Owner can allow Member writes on a Collection.
- **Record** — one JSON object stored in a Collection, with an opaque ID and a monotonic version.
- **History** — the immutable list of full JSON snapshots for one Record, ordered by version. History is not a query planner or analytics warehouse.

## What you can do

1. Create a Collection (Owner).
2. Push a new Record into a Collection.
3. Get the current Record by ID.
4. Get that Record's revision history.

Replace, patch, list, archive, restore, and permanent delete are available on the Action Platform for advanced automation. Start with push, get, and history.

## Roles

| Action | Owner | Member |
| --- | --- | --- |
| Create Collection | Yes | No |
| Push / replace / patch when Member writes are enabled | Yes | Yes |
| Push / replace / patch when Member writes are disabled | Yes | No |
| Get Record and history | Yes | Yes |

## Ordinary HTTP examples

Call the Action Platform with ordinary HTTP. There is no CompanyOS language SDK. Authenticate with a Member session token or an Automation Grant secret as `Authorization: Bearer …`. Discover live operation IDs through `GET /api/v1/operations` before hard-coding long-lived automation.

Replace `https://app.companyos.cc` with your deployment origin when self-hosting.

### 1. Create a Collection (Owner)

Operation ID: `record_store.create_collection`

#### curl

```bash
curl -sS -X POST "https://app.companyos.cc/api/v1/operations/record_store.create_collection" \
  -H "Authorization: Bearer $COMPANYOS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Weekly KPIs",
    "description": "Team KPI snapshots",
    "member_writes_enabled": true
  }'
```

#### TypeScript (fetch)

```ts
const response = await fetch(
  "https://app.companyos.cc/api/v1/operations/record_store.create_collection",
  {
    method: "POST",
    headers: {
      Authorization: `Bearer ${process.env.COMPANYOS_TOKEN}`,
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      name: "Weekly KPIs",
      description: "Team KPI snapshots",
      member_writes_enabled: true,
    }),
  },
);
const body = await response.json();
// body.result.collection.id → col_…
```

#### Python (urllib)

```python
import json
import os
import urllib.request

req = urllib.request.Request(
    "https://app.companyos.cc/api/v1/operations/record_store.create_collection",
    data=json.dumps(
        {
            "name": "Weekly KPIs",
            "description": "Team KPI snapshots",
            "member_writes_enabled": True,
        }
    ).encode(),
    headers={
        "Authorization": f"Bearer {os.environ['COMPANYOS_TOKEN']}",
        "Content-Type": "application/json",
    },
    method="POST",
)
with urllib.request.urlopen(req) as res:
    body = json.load(res)
# body["result"]["collection"]["id"] → col_…
```

### 2. Push a Record

Operation ID: `record_store.push_record`

#### curl

```bash
curl -sS -X POST "https://app.companyos.cc/api/v1/operations/record_store.push_record" \
  -H "Authorization: Bearer $COMPANYOS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "collection_id": "col_example",
    "payload": { "leads": 12, "deals": 3 },
    "idempotency_key": "kpi-2026-07-17"
  }'
```

#### TypeScript (fetch)

```ts
const response = await fetch(
  "https://app.companyos.cc/api/v1/operations/record_store.push_record",
  {
    method: "POST",
    headers: {
      Authorization: `Bearer ${process.env.COMPANYOS_TOKEN}`,
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      collection_id: "col_example",
      payload: { leads: 12, deals: 3 },
      idempotency_key: "kpi-2026-07-17",
    }),
  },
);
const body = await response.json();
// body.result.record.id → rec_…
// body.result.record.version → 1
```

#### Python (urllib)

```python
import json
import os
import urllib.request

req = urllib.request.Request(
    "https://app.companyos.cc/api/v1/operations/record_store.push_record",
    data=json.dumps(
        {
            "collection_id": "col_example",
            "payload": {"leads": 12, "deals": 3},
            "idempotency_key": "kpi-2026-07-17",
        }
    ).encode(),
    headers={
        "Authorization": f"Bearer {os.environ['COMPANYOS_TOKEN']}",
        "Content-Type": "application/json",
    },
    method="POST",
)
with urllib.request.urlopen(req) as res:
    body = json.load(res)
```

### 3. Get a Record

Operation ID: `record_store.get_record`

#### curl

```bash
curl -sS -X POST "https://app.companyos.cc/api/v1/operations/record_store.get_record" \
  -H "Authorization: Bearer $COMPANYOS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "collection_id": "col_example",
    "record_id": "rec_example"
  }'
```

#### TypeScript (fetch)

```ts
const response = await fetch(
  "https://app.companyos.cc/api/v1/operations/record_store.get_record",
  {
    method: "POST",
    headers: {
      Authorization: `Bearer ${process.env.COMPANYOS_TOKEN}`,
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      collection_id: "col_example",
      record_id: "rec_example",
    }),
  },
);
const body = await response.json();
// body.result.record.payload
```

#### Python (urllib)

```python
import json
import os
import urllib.request

req = urllib.request.Request(
    "https://app.companyos.cc/api/v1/operations/record_store.get_record",
    data=json.dumps(
        {
            "collection_id": "col_example",
            "record_id": "rec_example",
        }
    ).encode(),
    headers={
        "Authorization": f"Bearer {os.environ['COMPANYOS_TOKEN']}",
        "Content-Type": "application/json",
    },
    method="POST",
)
with urllib.request.urlopen(req) as res:
    body = json.load(res)
```

### 4. Get Record history

Operation ID: `record_store.get_record_history`

#### curl

```bash
curl -sS -X POST "https://app.companyos.cc/api/v1/operations/record_store.get_record_history" \
  -H "Authorization: Bearer $COMPANYOS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "collection_id": "col_example",
    "record_id": "rec_example"
  }'
```

#### TypeScript (fetch)

```ts
const response = await fetch(
  "https://app.companyos.cc/api/v1/operations/record_store.get_record_history",
  {
    method: "POST",
    headers: {
      Authorization: `Bearer ${process.env.COMPANYOS_TOKEN}`,
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      collection_id: "col_example",
      record_id: "rec_example",
    }),
  },
);
const body = await response.json();
// body.result.revisions → [{ version, payload, created_at, created_by }, …]
```

#### Python (urllib)

```python
import json
import os
import urllib.request

req = urllib.request.Request(
    "https://app.companyos.cc/api/v1/operations/record_store.get_record_history",
    data=json.dumps(
        {
            "collection_id": "col_example",
            "record_id": "rec_example",
        }
    ).encode(),
    headers={
        "Authorization": f"Bearer {os.environ['COMPANYOS_TOKEN']}",
        "Content-Type": "application/json",
    },
    method="POST",
)
with urllib.request.urlopen(req) as res:
    body = json.load(res)
# body["result"]["revisions"]
```

## Limits and failures

- Workspace quotas are measured in stored bytes. Exceeding quota returns `record_store_quota_exceeded`.
- Oversized or invalid JSON payloads return `record_store_payload_too_large` or `record_store_invalid_payload`.
- Concurrent replace/patch/archive calls that pass a stale `expected_version` return `record_store_stale_version`.
- Reusing an `idempotency_key` with a different payload returns `record_store_idempotency_conflict`.

Every failure is an AI-Actionable Error with `code`, `message`, `recoverable`, `next`, and a docs link. See the [AI-Actionable Error Catalog](/build-with-companyos/error-catalog) and the [OpenAPI reference](/build-with-companyos/openapi).

## Related

- [Automation](/automation) — how unattended callers use Automation Grants
- [Build with CompanyOS](/build-with-companyos/index) — capability discovery and contracts
