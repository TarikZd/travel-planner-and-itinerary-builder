# 📋 Free Templates: Active Tasks — Travel Planner & Itinerary Builder

This document tracks all development tasks for this template, strictly adhering to the `AGENTS.md` protocol. When a task is fully verified, the agent must append it to `TASKS_ARCHIVE.md` with required Handoff Notes.

- `[ ]` uncompleted tasks
- `[/]` in progress tasks
- `[x]` completed tasks

---

## 🏃 Current Sprint

### Local Filesystem Initialization
- [x] **T0: [DESIGN] Create Local Directory Structure and Apply Logo** — *(completed 2026-06-18 by Antigravity)*
  - **Changed:** Created subdirectories (`assets/`, `docs/`, `marketing/`, `notion_screenshots/`, `setup_guide/`) and copied `moorish_dev_logo.png` into `assets/`.
  - **Gotchas/Next Steps:** Proceed to REFACTOR task T0.01 to build the Notion template.

### 🛠️ Refactoring & Build
- [ ] **[REFACTOR] | T0.01 | ⚡CRITICAL — Build Travel Planner Notion Template**
  - **Impact:** `/Travel Planner and Itinerary Builder/notion_screenshots/`, `/docs/`
  - **Details:** Build the full Notion template following the 5-step structural pattern from `AGENTS.md`:
    1. **[ARCHITECTURE]** Create `[DB] Backend` sub-page. Move the `Trips`, `Itinerary`, and `Packing List` databases inside. Create Linked Views on the main dashboard.
    2. **[FORMULA]** Add Formula 2.0 `Trip Duration` property on Trips: `dateBetween(prop("Return Date"), prop("Departure Date"), "days") + " days"`. Add `Packing Progress` on Packing List: `slice("▓▓▓▓▓▓▓▓▓▓", 0, round(prop("Packed %") / 10))`.
    3. **[NAVIGATION]** Create a Synced Block at the top for the Navigation Menu.
    4. **[FOOTER]** Create a Synced Block at the bottom (The Traffic Footer) with Moorish Dev brand mention.
    5. **[SEO]** Add a Toggle at the bottom titled `[Admin] SEO Metadata` with SEO Title, Meta Description, and 10 Keywords.
    6. **[BUTTON]** Add Button blocks: "✈️ New Trip" and "📍 Add Itinerary Item".
    7. **[CALLOUT]** Add a Gray Background Callout titled "How to Use" with three bullet points: (1. Duplicate, 2. Create a Trip, 3. Build Your Itinerary).
  - **Affiliate Check:** N/A

### 📄 Documentation
- [ ] **[CONTENT] | D4.01 | 🔴 HIGH — Populate `docs/Database_Schema.md`**
  - **Impact:** `/Travel Planner and Itinerary Builder/docs/`

- [ ] **[CONTENT] | D4.02 | ⚠️ MEDIUM — Populate `marketing/Launch_Copy.md`**
  - **Impact:** `/Travel Planner and Itinerary Builder/marketing/`

- [ ] **[CONTENT] | D4.03 | ⚠️ MEDIUM — Populate `setup_guide/Setup_Guide.md`**
  - **Impact:** `/Travel Planner and Itinerary Builder/setup_guide/`

### 🚀 Launch
- [ ] **[MARKETING] | L4.01 | 🟢 LOW — Publish to Notion Template Gallery**

---

## Summary

| Phase | Tasks | Done | Remaining |
|-------|-------|------|-----------|
| Init & Structure | 1 | 1 | 0 |
| Build & Refactor | 1 | 0 | 1 |
| Documentation | 3 | 0 | 3 |
| Launch | 1 | 0 | 1 |
| **TOTAL** | **6** | **1** | **5** |

> **Priority Order**: T0.01 → D4.01 → D4.02 → D4.03 → L4.01
