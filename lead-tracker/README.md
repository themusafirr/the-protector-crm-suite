# The Protector — Lead Tracker

## Files
- `leads-tracker.csv` — sabhi leads (sample data se start kar)
- `renewals.csv` — renewal due clients (cron job roz check karega)
- `daily-log.csv` — har roz 9 AM auto-update log

## Setup (5 min)
1. Google Sheet banao → columns: same as `leads-tracker.csv`
2. Sheet ID copy karo (URL mein `d/` ke baad wala)
3. Cron job update karo Sheet ID ke saath (future mein)

## Daily Use
- Naya lead? → `leads-tracker.csv` mein row add kar
- Renewal aaya? → `renewals.csv` mein add kar
- Cron job subah 9 AM pe auto-check karega renewals

## Target
| Metric | Goal |
|---|---|
| Leads/month | 100 |
| Close % | 20% |
| Clients/month | 20 |
| Avg commission | ₹2,500 |
| Monthly income | ₹50,000 |