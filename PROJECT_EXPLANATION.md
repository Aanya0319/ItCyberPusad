# Project Explanation Guide

## 1. Multi-Page Structure

Each sidebar menu item opens a separate HTML file. This keeps every module independent while the shared `style.css` and `app.js` files maintain one consistent design and reusable functionality.

- Dashboard: `index.html`
- Customers: `customers.html`
- Leads: `leads.html`
- Projects: `projects.html`
- Tasks: `tasks.html`
- Reports: `reports.html`
- Settings: `settings.html`
- Profile: `profile.html`
- Sign in: `login.html`

## 2. Shared Sidebar and Header

Every page contains the same sidebar and header structure. The current page has the `active` class and `aria-current="page"`. On screens below 900px, JavaScript opens and closes the sidebar using the `sidebar-open` body class.

## 3. JavaScript Page Initialization

The `data-page` attribute on the `<body>` tells JavaScript which page is currently open.

Example:

```html
<body data-page="customers">
```

`initializeApp()` calls only the initializer needed for that page:

```javascript
const initializers = {
  dashboard: initDashboard,
  customers: initCustomers,
  leads: initLeads,
  projects: initProjects,
  tasks: initTasks,
  reports: initReports,
  settings: initSettings,
  profile: initProfile,
  login: initLogin
};
```

## 4. Dummy Data and LocalStorage

Customers, leads, projects and tasks begin with JavaScript dummy arrays. The project stores user changes in LocalStorage, so added or updated records remain available after refresh.

The storage helper functions are:

- `loadCollection()`
- `saveCollection()`
- `loadSettings()`

## 5. Search Logic

The shared search input dispatches an `appsearch` custom event. Each page listens for this event and filters its own collection.

Example customer search fields:

- Customer name
- Company
- Email

The matching text is converted to lowercase so the search is case-insensitive.

## 6. Filter Logic

Dropdown filters compare the selected value with each record. A value of `all` skips the status restriction.

Tasks use two filters together:

- Status
- Priority

A task must match the search, status and priority conditions to remain visible.

## 7. Working Forms

Native HTML `<dialog>` elements contain forms for adding:

- Customers
- Leads
- Projects
- Tasks

On form submission, JavaScript:

1. Prevents the default page reload.
2. Reads values using `FormData`.
3. Creates a new object with a unique ID.
4. Adds it to the correct data array.
5. Saves the array in LocalStorage.
6. Re-renders the table.
7. Closes and resets the form.
8. Shows a success toast.

## 8. Update and Delete Actions

- Leads can be marked as won.
- Tasks can be marked as completed.
- Customers, leads, projects and tasks can be deleted.

These actions update both the current table and LocalStorage.

## 9. Reports

The reports page calculates values from the current lead and project data. The period dropdown changes the revenue chart. The export button creates a CSV file using JavaScript `Blob` and downloads it in the browser.

## 10. Settings

The settings page stores profile, company and notification preferences in LocalStorage. Changing the profile name also updates the header name immediately.

The reset button clears all saved demo data and restores the original arrays after reload.

## 11. Responsive Design

The CSS uses media queries at 1180px, 900px, 680px and 430px.

On smaller screens:

- The sidebar becomes an off-canvas menu.
- Summary cards become one column.
- Header sections wrap.
- Filters become flexible rows.
- Tables allow horizontal scrolling.
- Form fields become one column.
- Dialog and buttons remain touch-friendly.

## 12. Deployment

This is a static website, so Netlify needs no build command. The publish directory is the project root (`.`). All page links are relative, so navigation works after deployment.
## 13. Interactive Profile Menu

JavaScript converts the header profile block into an accessible menu on every protected page. The trigger updates `aria-expanded`, closes on outside click or Escape, and provides links to the profile page and exact Settings sections.

The profile page saves personal information and an optional profile image in LocalStorage. `applySettings()` updates the avatar, initials, name, role, contact information and workspace identity everywhere without duplicating page-specific code.

The Sign Out action stores a local session flag and opens `login.html`. The login form validates the email/password fields, removes the flag and returns the user to the requested dashboard page. This is a frontend demonstration and does not store passwords.


## n8n Configuration Module

The `n8n-config.html` page is a dedicated Settings module for connecting n8n Cloud or self-hosted automation instances.

### Frontend connection logic

- `loadN8nConfig()` reads non-secret connection settings from LocalStorage.
- The API key is stored in SessionStorage by default, so it is removed when the browser session ends.
- LocalStorage key saving happens only when the user explicitly enables the remember option.
- `runN8nConnectionTest()` checks either `/healthz` or `/api/v1/workflows?limit=1`.
- `AbortController` applies the selected request timeout.
- Failed browser requests display CORS, certificate, network and proxy guidance rather than a fake successful state.

### Secure Netlify proxy

`netlify/functions/n8n-proxy.js` runs server-side and reads:

- `N8N_BASE_URL`
- `N8N_API_KEY`
- `N8N_API_BASE_PATH`

The browser sends only an action name (`health` or `api`) to the same-origin Netlify Function. The API key stays in Netlify's server-side environment.

### Webhook tester

The webhook form selects Test or Production URL, HTTP method, optional secret header and JSON request body. JavaScript validates the JSON before sending, shows HTTP status and timing, formats the response and adds a redacted diagnostic entry.

### Environment and code generators

The page generates self-hosting environment variables and request examples from current form values. Generated examples always use placeholder or environment-variable API keys, never the entered secret.
