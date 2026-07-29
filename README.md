# IT Cyber Simple Business Dashboard

A clean, responsive and fully functional IT Cyber branded multi-page business dashboard built with HTML5, CSS3 and Vanilla JavaScript. The project does not use React, Bootstrap, Tailwind CSS or any other framework.

## Pages

- `index.html` — Dashboard overview
- `customers.html` — Customer management
- `leads.html` — Sales lead pipeline
- `projects.html` — Project management
- `tasks.html` — Task management
- `reports.html` — Business performance reports
- `settings.html` — Complete account, business, appearance, regional, notification, security and data settings
- `n8n-config.html` — Advanced n8n API, webhook, hosting and automation configuration
- `profile.html` — Profile overview, avatar and personal-information editor
- `login.html` — Frontend demo sign-in page used by the working sign-out flow
- `404.html` — Branded production not-found page

## Features

### Dashboard
- Dynamic summary cards
- Monthly performance bars
- Recent activities
- Recent project table
- Project search and status filter

### Customers
- Customer summary cards
- Add customer form
- Customer search
- Active/inactive filter
- Delete customer action

### Leads
- Lead pipeline summary
- Add lead form
- Search and stage filter
- Mark lead as won
- Delete lead action
- Pipeline value calculation

### Projects
- Project summary cards
- Add project form
- Search by project or client
- Status filter
- Delete project action

### Tasks
- Task summary cards
- Add task form
- Search by task or assignee
- Status and priority filters
- Mark task as completed
- Delete task action

### Reports
- Revenue summary cards
- Period selector
- Responsive revenue chart
- Project status distribution
- CSV report export


### Profile Menu and Account
- Clickable header profile trigger on every protected page
- Dropdown with My Profile, Edit Profile, Account Settings, Notifications and Sign Out
- Click-outside and Escape-key closing behavior
- Dedicated responsive profile page
- Profile photo upload, preview and removal
- Editable name, email, role, title, phone, city, country and bio
- Live initials/photo, name and role updates across all pages
- Local demo sign-out and sign-in flow
- Direct links to exact Settings sections

### Notification Center
- Working notification bell on desktop, tablet and mobile
- Persistent unread badge and notification history
- Mark individual notification as read by opening it
- Mark all read and clear all actions
- Customer, lead, project and task activity alerts
- Links from each notification to the related page
- Optional sound preference
- Browser notification permission and test action
- HTTPS/localhost compatibility status

### Settings
- Profile name, email, role, phone, job title and bio
- Live avatar initials and header profile updates
- Company contact, website, address and registration details
- Light, dark and system theme options
- Blue, green, purple and orange accent colors
- Compact/comfortable density and text-size controls
- Dashboard welcome banner, reduced motion and delete-confirmation preferences
- Locale, timezone, currency and date-format controls with live preview
- Email, task, lead, project, weekly report and sound preferences
- Two-factor, session timeout and login alert preferences
- Frontend-only password validation without storing passwords
- Browser notification permission, status and test controls
- JSON workspace export and import
- Settings-only reset and complete demo-data reset
- Local settings persistence across every page


### n8n Automation Configuration
- Separate advanced configuration page inside Settings
- n8n Cloud, self-hosted and local connection profiles
- Direct browser and secure Netlify Function connection modes
- `/healthz` instance health test
- Public REST API authentication test using `X-N8N-API-KEY`
- Session-only secret handling by default
- Optional LocalStorage API-key persistence with a security warning
- Real Test and Production webhook request tester
- JSON validation, formatting and response inspection
- Optional custom webhook authentication header
- Self-hosted `.env` variable generator
- Generated cURL, server-side JavaScript and Netlify proxy examples
- Connection status, timing and browser diagnostic log
- Redacted configuration export and complete configuration reset
- Six official n8n documentation links
- Included `netlify/functions/n8n-proxy.js` secure proxy

### Shared Features
- Custom IT Cyber logo in the sidebar, login screen and browser favicon
- Separate HTML page for every sidebar item
- Active navigation state on each page
- Responsive desktop, tablet and mobile layout
- Mobile hamburger sidebar
- Current date and year display
- Accessible form labels and dialog forms
- Empty table states
- Toast notifications and full in-app notification center
- LocalStorage data persistence
- Saved profile, company and appearance applied across all pages
- Optional confirmation before destructive actions

## Technologies Used

- HTML5
- CSS3
- Vanilla JavaScript
- CSS Grid and Flexbox
- Browser LocalStorage
- Git and GitHub
- Netlify

## Folder Structure

```text
business-dashboard/
├── index.html
├── customers.html
├── leads.html
├── projects.html
├── tasks.html
├── reports.html
├── settings.html
├── n8n-config.html
├── profile.html
├── login.html
├── 404.html
├── site.webmanifest
├── robots.txt
├── css/
│   └── style.css
├── js/
│   └── app.js
├── assets/
│   ├── icons/
│   └── images/
│       ├── it-cyber-logo.png
│       └── it-cyber-favicon.png
├── netlify.toml
├── netlify/
│   └── functions/
│       └── n8n-proxy.js
├── N8N_CONFIGURATION_GUIDE.md
├── PRODUCTION_READINESS_REPORT.md
├── PRODUCTION_TEST_REPORT.md
├── SECURITY.md
├── PROJECT_EXPLANATION.md
└── README.md
```

## Run Locally

### Option 1: Open directly

Open `index.html` in a modern browser.

### Option 2: Use a local server

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

You can also use the VS Code Live Server extension.

## How Data Works

The project uses JavaScript dummy data. When records are added, updated or deleted, the changes are stored in browser LocalStorage. No backend or database is required.

Use **Settings → Data controls → Reset all data** to restore the original records. You can also export or import a JSON workspace backup.

## Suggested Git Commit History

```text
Initial project setup
Create dashboard layout
Add sidebar and header
Create summary cards
Add customers management page
Add leads pipeline page
Add projects management page
Add tasks management page
Add reports and CSV export
Build complete settings and local storage controls
Add interactive profile menu and profile page
Add n8n configuration and secure Netlify proxy
Add demo sign-in and sign-out flow
Make all pages responsive
Fix bugs and update README
```

## Netlify Deployment

1. Push the project to a GitHub repository.
2. Open Netlify.
3. Select **Add new project**.
4. Select **Import an existing project**.
5. Connect GitHub and select the repository.
6. Keep the build command blank.
7. Set the publish directory to `.`.
8. Select **Deploy**.
9. Test every page and mobile navigation after deployment.

The included `netlify.toml` already contains the publish and functions directories:

```toml
[build]
  publish = "."

[functions]
  directory = "netlify/functions"
```

For secure n8n API access, add these environment variables in Netlify before deploying:

```text
N8N_BASE_URL=https://your-workspace.app.n8n.cloud
N8N_API_KEY=your-secret-api-key
N8N_API_BASE_PATH=/api/v1
```

See `N8N_CONFIGURATION_GUIDE.md` for detailed setup and troubleshooting.

## Submission Links

- GitHub Repository: `Add your GitHub link here`
- Netlify Live Website: `Add your Netlify link here`

## Developer

**Kautuk Ade**


## Production Readiness

The included frontend package is configured for Netlify production deployment with:

- Content Security Policy and security headers
- HTTPS HSTS policy
- HTML and static-asset cache rules
- Netlify Function no-store responses
- Branded 404 page
- Web app manifest and touch icon
- `.gitignore` and safe `.env.example`
- Hardened n8n proxy input validation
- Responsive notification center

Read `PRODUCTION_READINESS_REPORT.md` for the completed audit, test coverage and deployment checklist. Read `SECURITY.md` before connecting real customer data.

### Important architecture note

This remains a frontend dashboard demonstration. The login page does not authenticate against a server, and workspace records use browser LocalStorage. A real multi-user deployment that stores private business data must connect secure authentication, authorization, a backend API and a database. Email preferences also require an email service or n8n workflow.

## Regional preferences

The Regional settings section is fully connected to the shared application formatter. Locale, timezone, currency and date-format selections are saved in browser LocalStorage and applied across Dashboard, Customers, Leads, Projects, Tasks, Reports, Profile and notification dates. Dynamic tables, cards and charts re-render immediately when regional settings change.

Supported options:

- Locales: English (India), English (United States), English (United Kingdom)
- Timezones: Asia/Kolkata, America/New_York, Europe/London, Asia/Dubai
- Currencies: INR, USD, GBP, EUR
- Date formats: locale default, day-first, month-first and ISO

## Mobile Responsive Design

The complete website is optimized for phones, tablets, laptops and desktop screens.

Mobile-specific behavior includes:

- Tested layouts at 320 px, 360 px, 390 px and 768 px widths
- Off-canvas sidebar navigation with overlay and body-scroll locking
- Compact sticky mobile header
- Responsive search, notification and profile controls
- Full-screen mobile notification center
- Viewport-safe profile dropdown
- Horizontally scrollable Settings navigation
- One-column mobile forms and settings cards
- Touch-friendly controls with a minimum 44 px target height
- Mobile dialogs limited to the visible viewport
- Customer, lead, project, task and dashboard tables converted into labeled cards below 640 px
- Dynamic table rows automatically receive responsive field labels
- Responsive Reports charts and n8n code panels
- Safe-area support for notched phones
- No page-level horizontal overflow

The detailed validation results are available in [`MOBILE_RESPONSIVE_TEST_REPORT.md`](MOBILE_RESPONSIVE_TEST_REPORT.md).

## Administrator Panel Navigation

The Administrator profile control now opens a dedicated account panel with internal scrolling. While this panel is open, the dashboard background and its current scroll position remain fixed. Closing the panel through Back, the backdrop or Escape restores the exact previous dashboard position.

The panel includes quick access to Dashboard, Customers, Leads, Projects, Tasks, Reports, Profile, Settings, Notifications and n8n Configuration. Profile, Settings and n8n Configuration pages also include page-level Back buttons with safe history fallback navigation.
