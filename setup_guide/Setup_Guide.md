# 📖 Start Here: Travel Planner & Itinerary Builder

Welcome to the **Travel Planner & Itinerary Builder** by **Moorish Dev**. Plan your next adventure in under 60 seconds.

---

## ⚡ Quick Start (60 Seconds)

1. **Duplicate this template** → Click `Duplicate` in the top-right corner.
2. **Create a Trip** → Click "✈️ New Trip", name it, and set departure/return dates. Duration auto-calculates.
3. **Build your Itinerary** → Click "📍 Add Itinerary Item", link it to your trip, and set the date/time.
4. **Pack your bags** → Open the Packing List view, add items, and check them off as you pack.

---

## 🏗️ Architecture Overview

| Location | What's Here |
| --- | --- |
| **Main Dashboard** | Trip overview + Itinerary Calendar + Packing Progress |
| **`[DB] Backend`** | Raw `Trips`, `Itinerary Items`, `Packing List` databases |

---

## ✍️ Manual Setup Steps (Required)

### Step 1: Verify the Trip Duration Formula
1. Open `[DB] Backend` → `Trips` database.
2. Click `Trip Duration` → **Edit Property** → Verify type is `Formula`.
3. If not, paste:
```javascript
if(
  empty(prop("Return Date")) or empty(prop("Departure Date")),
  "TBD",
  format(dateBetween(prop("Return Date"), prop("Departure Date"), "days")) + " days"
)
```

### Step 2: Set Up the Itinerary Calendar
1. On the dashboard's Itinerary Linked View → `+ Add a view` → `Calendar`.
2. Set date to `Date & Time`. Name it `📅 Day-by-Day`.

### Step 3: Create Button Blocks
1. Type `/button` → Create `✈️ New Trip` (adds to Trips) and `📍 Add Itinerary Item` (adds to Itinerary Items).

---

## 🎨 Customization Tips
- **Share your itinerary**: Share the Itinerary sub-page publicly so travel companions can view the plan.
- **Add a budget tracker**: The `Cost (£)` field on Itinerary Items + a Rollup on Trips gives you real-time spend vs. budget.
- **Color-code by category**: Use select colors on `Category` (Transport, Food, etc.) for instant visual clarity.

---

*Built by Moorish Dev | Last Updated: June 2026*
