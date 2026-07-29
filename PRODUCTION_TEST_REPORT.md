# Production Test Report

Test date: 28 July 2026

## Automated checks

| Area | Result |
|---|---|
| HTML pages loaded | 11/11 passed |
| New IT Cyber logo rendering | Passed |
| Notification button on protected pages | 9/9 passed |
| Notification panel open/close | Passed |
| Unread count and badge | Passed |
| Mark all notifications read | Passed |
| Clear/empty notification state | Passed |
| Customer create action | Passed |
| Customer summary count refresh | Passed |
| Customer activity notification | Passed |
| Browser notification settings flow | Passed with API test double |
| Profile dropdown and Escape close | Passed |
| Mobile notification visibility | Passed at 390 × 844 |
| Mobile panel viewport fit | Passed |
| JavaScript syntax | Passed |
| Netlify Function syntax | Passed |
| Internal asset/link audit | Passed |
| Duplicate HTML IDs | None found |
| Form label audit | Passed |
| CSS brace validation | Passed |
| Netlify TOML parsing | Passed |
| Browser JavaScript errors | 0 |

## Browser test method

The environment blocks direct localhost navigation in the system browser. Each page was therefore rendered in an isolated Chromium document with the production CSS and JavaScript injected unchanged. LocalStorage and the Notifications API were replaced by test doubles only for browser automation. This allowed interaction testing without modifying the delivered project files.

## Manual deployment checks still required

After deploying to Netlify:

1. Confirm the Netlify HTTPS certificate is active.
2. Open Settings → Notifications and grant browser permission.
3. Send a test notification.
4. Configure n8n environment variables and test the secure Function connection.
5. Check the deployed browser console and Netlify Function logs.
6. Confirm the custom domain, if used, redirects to HTTPS.
