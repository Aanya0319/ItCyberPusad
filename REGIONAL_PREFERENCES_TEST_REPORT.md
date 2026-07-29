# Regional Preferences Fix — Test Report

## Fixed issues

- Removed hardcoded `en-IN` number formatting from dashboard statistics.
- Added a shared regional-settings normalization layer.
- Applied selected timezone to current-date and date-time formatting.
- Applied selected locale to dates, numbers and currency.
- Applied selected currency to lead values and report revenue.
- Added immediate re-render events for Dashboard, Customers, Leads, Projects, Tasks and Reports.
- Added LocalStorage persistence and invalid-value fallback handling.
- Updated CSV project export to use the selected date format.
- Added a live preview containing date, currency and timezone-aware current time.

## Automated browser checks

- US locale + USD + America/New_York + month-first preview: passed.
- India locale + INR + Asia/Kolkata + day-first preview: passed.
- Settings saved to LocalStorage: passed.
- Header timezone update: passed.
- Reports currency live re-render USD → INR: passed.
- Customers dates live re-render month-first → day-first: passed.
- ISO date format: passed.
- Invalid regional setting fallback: passed.
- JavaScript console errors: 0.

## Syntax and structure

- `node --check js/app.js`: passed.
- All HTML local file references validated.
- Duplicate HTML IDs checked.
