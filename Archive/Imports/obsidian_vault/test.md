---
type: note
topic: tech
---

### shipments
* primary_key
* weight
* dimensions
* shipment_item_count
* space_remaining

### item
* primary_key
* shipment_id (foreign key)
* dimensions + weight
* rotation (or place inside container)
* is_hazardous

### container
* primary_key
* is_available
