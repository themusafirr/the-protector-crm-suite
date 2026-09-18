# The Protector — Notion Dashboard Setup

## 🎯 Goal
Track renewals, claims, commissions, monthly targets in one dashboard.

---

## 📋 Database 1: Clients (Master Table)

| Property | Type | Notes |
|---|---|---|
| Name | Title | Client ka naam |
| Phone | Phone | 9649228281 etc |
| Insurance Type | Select | Bike / Car / Health / Life / Shop / Other |
| Policy Number | Text | Company ka policy ID |
| Company | Select | HDFC / ICICI / TATA / Bajaj / Max Life / Other |
| Premium Amount | Number | ₹ |
| Commission | Number | ₹ (auto-calculated) |
| Status | Select | New Lead / Quoted / In-Process / Closed / Lost |
| Purchase Date | Date | Policy start |
| Renewal Date | Date | Policy expiry — **main trigger for reminders** |
| Assigned Agent | Person | Pankaj |
| Notes | Text | Free-form |

---

## 📋 Database 2: Renewals (Filter view)

Filter: `Renewal Date` is within `next 30 days`

This becomes your **Daily Action Queue** — har roz subah yeh dekh ke kya renew karna hai.

---

## 📋 Database 3: Claims (Track)

| Property | Type | Notes |
|---|---|---|
| Claim ID | Title | Internal tracking |
| Client | Relation | → Clients DB |
| Type | Select | Cashless / Reimbursement / Third-party |
| Status | Select | Intimated / Documents Pending / Under Review / Approved / Settled / Rejected |
| Amount Claimed | Number | ₹ |
| Amount Settled | Number | ₹ |
| Company | Select | HDFC / ICICI etc |
| Date | Date | Intimation date |
| Notes | Text | Updates |

---

## 📋 Database 4: Commission Tracker (Monthly)

| Property | Type | Notes |
|---|---|---|
| Month | Select | Sep 2026 / Oct 2026 |
| Client | Relation | → Clients |
| Type | Select | New / Renewal |
| Insurance | Select | Bike / Car / Health |
| Premium | Number | ₹ |
| Commission Earned | Number | ₹ |
| Company | Text | HDFC Ergo |
| Paid | Checkbox | Yes / No |

**Rollup:** Sum of "Commission Earned" = Monthly Income

---

## 🎨 Views to Create

### 1. "Active Clients" (Gallery)
- Filter: Status = `Closed`
- Group by: Insurance Type
- Cover: random photo

### 2. "Renewals Due — 7 Days" (List)
- Filter: Renewal Date is within next 7 days
- Sort: Renewal Date ascending
- **THIS IS YOUR MORNING VIEW**

### 3. "Hot Leads" (Board)
- Filter: Status = `New Lead` or `Quoted`
- Group by: Status
- Sort: Last contacted descending

### 4. "Monthly Commission" (Calendar + Sum)
- Show by month
- Total = dashboard widget

---

## 📊 Dashboard Page (Home)

Top widgets:
1. **This Month** — count of new clients, total commission
2. **Renewals Due Today** — count
3. **Hot Leads** — count
4. **Pending Claims** — count

---

## ⚙️ Setup Steps (15 min)

| Step | Action |
|---|---|
| 1 | Notion → New Page → "The Protector" |
| 2 | Add 4 databases (Clients, Renewals, Claims, Commission) |
| 3 | Add relations between DBs |
| 4 | Create 4 views as above |
| 5 | Build dashboard page with linked views |
| 6 | Share with yourself on mobile |

---

## 💡 Pro Tip

Use **Notion API** later to auto-sync from CSV files. For now: **manual entry** after every deal close. **5 min daily** sufficient.

---

## 🔗 Notion API (Optional — Auto-sync)

1. notion.so/my-integrations → New integration
2. Token copy karo
3. Share "The Protector" page with integration
4. Cron job mein add karo → auto-sync CSV → Notion

> Token mujhe de do agar setup karwana ho. Otherwise manual chalao pehle.