# Security Notes

## Secrets

- Never place a real n8n API key in HTML, CSS, client-side JavaScript, screenshots or Git commits.
- Use the included Netlify Function and configure `N8N_BASE_URL`, `N8N_API_KEY` and `N8N_API_BASE_PATH` in Netlify environment variables.
- Keep **Remember API key on this device** disabled unless the browser profile and device are trusted.

## Data storage

This dashboard is a frontend application. Customers, leads, projects, tasks, settings and in-app notifications are stored in browser LocalStorage. Do not store sensitive personal, financial or regulated information in this demo architecture.

For a real multi-user production system, replace LocalStorage with an authenticated backend and database that provides authorization, validation, audit logging, backups and encryption.

## Authentication

The included login page is an explicitly labelled frontend demo. It does not verify a password against a server. Connect a real identity provider or backend authentication service before using the dashboard for private business data.

## Browser notifications

System notifications require a supported browser, an HTTPS deployment or localhost, and explicit user permission. In-app notifications continue to work without browser permission.

## Reporting a vulnerability

Do not publish credentials or sensitive details in a public issue. Contact the project owner privately with reproduction steps and affected files.
