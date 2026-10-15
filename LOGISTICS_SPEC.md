# Shared Logistics and Route Planning Specification

## Objective
Reduce avoidable delivery duplication by planning compatible pickup and delivery work together while preserving supplier, order and fulfillment ownership.

## Terminology
- **Order:** retailer’s commercial request.
- **Fulfillment allocation:** quantity assigned to one supplier/location.
- **Delivery job:** operational work to move allocated goods from pickup to retailer.
- **Shipment:** physical grouping of goods.
- **Route:** ordered stops assigned to a vehicle and planning window.
- **Stop:** pickup or delivery action at a location.

## Eligibility filter before route planning
A job is eligible only if:
- its allocation is accepted/ready according to the demo workflow;
- pickup and delivery locations are known;
- the planning window is compatible;
- the job’s service/handling flags are compatible with the vehicle;
- required authorization and fulfillment validations have already passed;
- it is not already assigned to an active route.

## Capacity
For each route, total carried load at each route segment must not exceed the vehicle’s configured weight or volume capacity. If multiple pickups and deliveries exist, load should be updated after each stop. A simple total-load check is acceptable only for the prototype if all jobs are picked up before the delivery sequence; document that simplification.

## Multi-origin handling
A route with multiple supplier origins requires pickup stops before delivery stops for the goods collected at each origin. The route planner must preserve pickup-before-delivery precedence. If the chosen solver configuration cannot represent a constraint, enforce it in application logic or simplify the demo scenario.

## Route planning modes
### Preferred: real configured providers
- OSRM: road network distance/duration estimates or matrices.
- VROOM: vehicle routing optimization for supported job/vehicle inputs.
- Validate service health, response schema, capacity, precedence and returned route.
- Store provider name/version/configuration where possible.
- If provider fails, report failure or use a labelled demo fallback only with dispatcher consent.

### Fallback: deterministic demo planner
- Use known synthetic coordinates or a predefined scenario.
- Group jobs by planning window and compatibility.
- Sort stops by a deterministic nearest-neighbor or predefined sequence.
- Estimate distances using a documented method. Straight-line distance must not be presented as road distance.
- Mark the plan `plannerType = deterministic_demo` and `isSimulated = true`.
- This mode is acceptable for the hackathon if transparent.

## Freight allocation
Prototype default:
1. Compute route-level estimated freight from a clearly stated synthetic rate or route estimate.
2. Allocate by shipment weight if every order has valid weight.
3. Otherwise allocate equally per delivery stop and label the fallback.
4. Apply paise rounding; assign any remainder deterministically so allocated shares sum exactly to route freight.
5. Display the allocation basis to the dispatcher and retailer.

## UI output
- Route map (if available) plus equivalent ordered stop list.
- Vehicle name, capacity, load used and utilization percentage.
- Ordered stops, pickup/delivery type, retailer label, order references.
- Estimated distance and duration with simulation/live label.
- Estimated route cost and per-order freight allocation.
- Excluded jobs and reasons.
- Warnings for infeasible capacity, missing coordinates or incompatible windows.

## KPIs
Calculate from actual demo records:
- eligible delivery jobs
- jobs included in shared route
- estimated route distance
- estimated route cost
- estimated cost per delivered order
- vehicle capacity utilization
- completed vs pending stops
- estimated savings versus a defined baseline (only if both values are calculated from the same assumptions)

## Required test scenarios
- Two compatible retailers consolidated into one route.
- Job excluded due to wrong planning window.
- Job excluded due to unauthorized/ineligible allocation.
- Vehicle capacity exceeded.
- Multiple pickup origins with precedence.
- Missing coordinate/provider failure.
- Repeated planning request does not create duplicate active route unintentionally.
