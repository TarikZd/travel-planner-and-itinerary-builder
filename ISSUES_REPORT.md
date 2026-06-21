# Template Audit & Friction Points — Travel Planner & Itinerary Builder

## 1. Logo Hosting Issue (Notion API)
- **Problem:** The Notion API does not support local file uploads for page icons.
- **Resolution:** Distribute `moorish_dev_logo.png` to `assets/`. User sets it as page icon manually.

## 2. Three-Database Architecture Complexity
- **Problem:** This template requires three related databases: `Trips`, `Itinerary Items`, and `Packing List`. Setting up Relations between all three via API needs careful ordering (create databases first, then add relations).
- **Resolution:** Create databases in order: `Trips` first, then `Itinerary Items` (with Relation to Trips), then `Packing List` (with Relation to Trips). Document this dependency in `setup_guide/Setup_Guide.md`.

## 3. Trip Duration Formula
- **Problem:** The `dateBetween()` formula requires both `Departure Date` and `Return Date` to be `Date` type properties with valid values. If either is empty, the formula returns `null`.
- **Resolution:** Add an `if()` guard: `if(empty(prop("Return Date")) or empty(prop("Departure Date")), "TBD", dateBetween(...))`.

## 4. Packing Progress Requires Rollup
- **Problem:** The `Packing Progress` visual bar requires a Rollup counting checked items vs. total items in the Packing List. This requires a `Checkbox` property on Packing List items and a two-step Rollup configuration.
- **Resolution:** Stage the Rollup as a manual step in `setup_guide/Setup_Guide.md`.

## 5. Button Block API Limitation
- **Problem:** Notion's native Button blocks cannot be created via the public Notion API.
- **Resolution:** User must manually create `✈️ New Trip` and `📍 Add Itinerary Item` button blocks.
