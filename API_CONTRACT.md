# API Contract — Prototype-Level Contract

The implementation may use Next.js server actions or REST handlers, but it must preserve these domain operation boundaries. If REST is used, prefix routes with `/api/v1`.

## Conventions
- JSON request/response.
- Use authenticated identity or explicit demo-role context; never trust a client-supplied organization ID without validating membership.
- Return a stable error shape: `{ "error": { "code": "...", "message": "...", "details": {} } }`.
- Use idempotency keys for create-order and simulated payment operations.
- Amounts are integer paise. Include currency (`INR`).
- All estimates must have `estimate_type` and `is_simulated` metadata where relevant.

## Key operations
| Method | Operation | Purpose |
|---|---|---|
| `GET` | `/api/v1/products` | Browse catalog and eligible offers |
| `GET` | `/api/v1/products/{productId}/offers` | Compare supplier offers |
| `POST` | `/api/v1/orders` | Validate basket, reserve stock, create order |
| `GET` | `/api/v1/orders/{orderId}` | Order, lines, allocations and timeline |
| `POST` | `/api/v1/orders/{orderId}/cancel` | Request cancellation if allowed |
| `POST` | `/api/v1/supplier-orders/{allocationId}/accept` | Supplier accepts assigned allocation |
| `POST` | `/api/v1/supplier-orders/{allocationId}/ready` | Mark allocation ready for pickup |
| `GET` | `/api/v1/logistics/jobs` | List eligible delivery jobs |
| `POST` | `/api/v1/routes/plan` | Plan a route for a set of jobs and vehicle |
| `POST` | `/api/v1/routes/{routeId}/confirm` | Confirm the reviewed route |
| `POST` | `/api/v1/routes/{routeId}/stops/{stopId}/status` | Update a stop status |
| `GET` | `/api/v1/dashboard/summary` | KPIs derived from scenario data |
| `POST` | `/api/v1/demo/reset` | Reset seeded scenario in demo mode only |

## Example order request
```json
{
  "retailerLocationId": "loc-retailer-01",
  "items": [
    { "productId": "sku-rice-5kg", "offerId": "offer-distributor-01", "quantity": 2 }
  ],
  "idempotencyKey": "demo-order-unique-001"
}
```

## Example order response
```json
{
  "orderId": "ord-demo-1001",
  "orderNumber": "KS-DEMO-1001",
  "status": "confirmed",
  "currency": "INR",
  "subtotalPaise": 120000,
  "estimatedFreightPaise": 8000,
  "estimatedTaxPaise": 0,
  "estimatedTotalPaise": 128000,
  "estimateDisclaimer": "Prototype estimate; not a tax invoice.",
  "allocations": [
    {
      "productId": "sku-rice-5kg",
      "supplierType": "authorized_distributor",
      "quantity": 2,
      "reason": "Eligible offer with sufficient demo stock and lower estimated total cost."
    }
  ]
}
```

## Example route-plan request
```json
{
  "planningWindow": "demo-morning",
  "vehicleId": "vehicle-demo-01",
  "jobIds": ["job-demo-01", "job-demo-02", "job-demo-03"],
  "planner": "demo"
}
```

## Example route-plan response
```json
{
  "routeId": "route-demo-01",
  "plannerType": "deterministic_demo",
  "isSimulated": true,
  "stops": [
    { "sequence": 1, "type": "pickup", "label": "Demo Distributor A" },
    { "sequence": 2, "type": "delivery", "label": "Kirana Store A" },
    { "sequence": 3, "type": "delivery", "label": "Kirana Store B" }
  ],
  "estimatedDistanceMeters": 8400,
  "estimatedDurationSeconds": 2100,
  "capacity": {
    "weightGrams": { "used": 42000, "available": 100000 },
    "volumeCm3": { "used": 65000, "available": 180000 }
  },
  "disclaimer": "Demo route plan; distance/time values are scenario estimates."
}
```

## Error codes
- `OFFER_NOT_ELIGIBLE`
- `INSUFFICIENT_STOCK`
- `INVALID_PACK_QUANTITY`
- `MOQ_NOT_MET`
- `UNAUTHORIZED_SUPPLIER`
- `ORDER_STATE_CONFLICT`
- `RESERVATION_CONFLICT`
- `ROUTE_CAPACITY_EXCEEDED`
- `INCOMPATIBLE_DELIVERY_JOBS`
- `IDEMPOTENCY_CONFLICT`
- `PROVIDER_UNAVAILABLE`

## Contract tests
For each operation, test successful response, validation failure, authorization failure, duplicate request behavior, and stale state behavior where applicable.
