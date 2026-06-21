# 🗄️ Database Schema: Travel Planner & Itinerary Builder

---

## Database 1: Trips

| Property Name | Type | Purpose |
| --- | --- | --- |
| **Trip Name** | `Title` | e.g., "Morocco Summer 2026". |
| **Destination** | `Text` | City, country, or region. |
| **Departure Date** | `Date` | Date of departure. |
| **Return Date** | `Date` | Date of return. |
| **Trip Duration** | `Formula` | Auto-calculates number of days. |
| **Budget (£)** | `Number` | Total estimated budget. |
| **Status** | `Select` | `Planning`, `Booked`, `In Progress`, `Completed`. |
| **Itinerary** | `Relation` | Links to Itinerary Items database. |
| **Packing List** | `Relation` | Links to Packing List database. |
| **Travel Party** | `Text` | Who's coming (e.g., "Solo", "Partner", "Family"). |
| **Notes** | `Text` | Booking references, visa info, etc. |

## Formula 2.0 Logic — Trip Duration
```javascript
if(
  empty(prop("Return Date")) or empty(prop("Departure Date")),
  "TBD",
  format(dateBetween(prop("Return Date"), prop("Departure Date"), "days")) + " days"
)
```

---

## Database 2: Itinerary Items

| Property Name | Type | Purpose |
| --- | --- | --- |
| **Activity** | `Title` | e.g., "Visit Jemaa el-Fna", "Airport Transfer". |
| **Trip** | `Relation` | Links to the Trips database. |
| **Date & Time** | `Date` | Scheduled date and time (with time enabled). |
| **Category** | `Select` | `Transport`, `Accommodation`, `Food`, `Sightseeing`, `Activity`. |
| **Location** | `Text` | Address or place name. |
| **Cost (£)** | `Number` | Estimated or actual cost of this item. |
| **Booked** | `Checkbox` | Whether this item has been booked/confirmed. |
| **Notes** | `Text` | Booking reference, directions, tips. |

---

## Database 3: Packing List

| Property Name | Type | Purpose |
| --- | --- | --- |
| **Item** | `Title` | e.g., "Passport", "Sunscreen", "Adapter". |
| **Trip** | `Relation` | Links to the Trips database. |
| **Category** | `Select` | `Documents`, `Clothing`, `Toiletries`, `Electronics`, `Misc`. |
| **Packed** | `Checkbox` | Mark when item is packed. |
| **Quantity** | `Number` | Number of items needed. |
| **Priority** | `Select` | `Essential`, `Important`, `Nice to Have`. |

## Formula 2.0 Logic — Packing Progress Bar (on Trips)
*Via Rollup on Packing List:*
```javascript
slice("▓▓▓▓▓▓▓▓▓▓", 0, round((prop("Items Packed") / prop("Total Items")) * 10))
```

## Architectural Notes
- **Vault Method:** All three databases reside in `[DB] Backend`. Dashboard uses Linked Views.
- **Recommended Views:** Active Trip (filtered Table), Itinerary (Calendar by Date & Time), Packing List (Table, grouped by Category).
