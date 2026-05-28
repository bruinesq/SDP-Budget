# SDSEP Budget Tracker

A private web app for managing Ryan Nguyen's California Self-Determination Program (CSDP) budget through Harbor Regional Center.

---

## What It Does

Tracks all spending from the CSDP budget across service codes, pay periods, employees, and employer taxes — in real time, from any device.

---

## Key Features

### Budget Tab
- Total budget, total spent, remaining balance, and % used
- Breakdown by service code: **310** (Respite Services), **320** (Community Living Support), **331** (Community Integration / NextStep), **ITE** (Individual Training & Education)
- Budget Adjustments log with +/− entries
- NextStep monthly fee tracking ($375/mo)
- Start New Cycle button for next budget year

### Pay Periods Tab
- All pay periods listed most-recent-first
- Per-period: dates, service code, employee hours, gross labor, employer tax, total
- Tap any row → **slide-out panel** showing full CA OT breakdown per employee:
  - Regular hours × rate
  - 1.5× OT hours × rate (daily >8hrs or weekly >40hrs)
  - 2× OT hours × rate (daily >12hrs)
  - Gross wages, employer tax, and period total

### Clock Log Tab
- Weekly grid (Sun–Sat) with color-coded columns per employee
- Three columns per employee: **Reg / 1.5× / 2×** — updated automatically from daily hours entered
- Tap any cell to open the keypad and enter hours
- Week totals row with automatic CA OT classification
- Per-employee summary cards below grid showing estimated gross for the week

### Timesheet Tab
- Monthly view of all entered hours

### Projection Tab
- Forward-looking spend estimates based on current hours and rates

### Reconcile Tab (3-step process)
1. **Statement** — enter current balance per code (310/320/331) and cumulative employer tax from Premier statement
2. **Compare** — side-by-side: your clock log calculations vs. statement totals per code; Accept or Ignore discrepancies
3. **Finalize** — mark period reconciled; employer tax allocated proportionally per employee by gross

### Settings Tab
- Employee list with full rate history and OT rates
- Add new rate (with effective date)
- End/reactivate employees
- Employer tax rate history
- NextStep fee history
- PIN management (set/change/remove 6-digit PIN)
- Start New Cycle (next budget year)

---

## Employees

| Name | Key | Status | Rate (current) |
|---|---|---|---|
| Cordelia Nguyen | `cor` | Active | $33/hr |
| Maverick Gerber | `mav` | Active | $33/hr |
| Rafi Bouhamouda | `raf` | Active (from 2/15/26) | $28/hr |
| Nicholas Dungey | `nic` | Terminated 1/31/26 | — |

OT rates are calculated automatically: 1.5× = reg × 1.5, 2× = reg × 2.

---

## CA Overtime Rules Applied

- **Daily OT 1.5×**: hours 8–12 in a single day
- **Daily OT 2×**: hours over 12 in a single day
- **Weekly OT 1.5×**: hours over 40 in a Sun–Sat work week
- Calculations are performed **week-by-week** across each pay period — not across the entire period at once

---

## Budget Year

**December 1, 2025 – November 30, 2026**

| Code | Description | Budget |
|---|---|---|
| 310 | Respite Services | $14,452.80 |
| 320 | Community Living Support | $200,631.60+ |
| 331 | Community Integration (NextStep) | $9,984.00 |
| ITE | Individual Training & Education | $500.00 |

---

## Technical Stack

| Component | Details |
|---|---|
| Frontend | Single-file HTML/CSS/JS (no framework) |
| Database | Supabase (PostgreSQL) |
| Hosting | GitHub Pages |
| URL | `https://bruinesq.github.io/SDP-Budget/` |
| Fonts | Syne (UI), IBM Plex Mono (numbers) |
| Sync | Real-time via Supabase REST API |

### Supabase Tables
- `pay_periods` — all pay period records
- `timesheet` — daily clock log entries (primary key: date + emp)
- `adjustments` — budget adjustments
- `app_settings` — tax rates, NS fees, employees, PIN, tax history

---

## Security

- **6-digit PIN** required on all devices
- PIN stored in Supabase; device authentication stored in localStorage
- Once authenticated, a device remembers the PIN until PIN is changed
- Change PIN via Settings → 🔒 PIN Settings

---

## How to Deploy Updates

1. Download the latest `sdp_budget.html`
2. Go to `github.com/bruinesq/SDP-Budget`
3. Edit `index.html` → Select all → Paste → Commit
4. Wait ~60 seconds
5. Hard refresh on iPad: hold reload → Empty Caches and Hard Reload

---

## Data Source

Pay periods and employer taxes are reconciled against **Premier Financial Management Services** statements. Premier is the Fiscal Management Service (FMS) for the CSDP program through Harbor Regional Center.

---

*Built for Ryan Nguyen · Harbor Regional Center · Budget Year 2025–26*
