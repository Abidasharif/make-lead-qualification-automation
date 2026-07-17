# Automated Lead Qualification & Routing System

An automated pipeline built on **Make.com** that processes incoming Excel leads, evaluates them via conditional routing logic, updates a spreadsheet database, and alerts sales teams through Slack notifications.

## 🚀 Key Features & Logic Flow
- **No Duplicate Processing:** Filters incoming rows to ensure only leads with an empty `Status` are parsed.
- **Path A (Invalid Leads):** Uses multi-block `OR` logic to catch rows missing critical data (Email, Country, or Budget) and marks them as `Invalid`.
- **Path B (Qualified Leads):** Uses `AND` logic to filter high-value leads (USA location + Budget ≥ $10,000), triggers a rich Slack notification message, and sets the status to `Qualified`.
- **Path C (Not Qualified Leads):** Handles completed rows that fall below thresholds, marking them `Not Qualified` without pinging Slack.
- **Graceful Error Handling:** Employs `Skip` error directives on core API modules to ensure minor network drops do not crash the runner loop.
