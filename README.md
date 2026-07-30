# IT Cyber Business Suite

<p align="center">
  <img src="assets/images/it-cyber-logo.png" alt="IT Cyber logo" width="140">
</p>

<p align="center">
  A responsive business-management dashboard built with HTML5, CSS3, Vanilla JavaScript, Netlify Functions and n8n integration.
</p>

<p align="center">
  <a href="https://github.com/kautukade/N8N-web-dashboard-">
    <img src="https://img.shields.io/badge/GitHub-Repository-181717?logo=github" alt="GitHub repository">
  </a>
  <img src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Netlify-00C7B7?logo=netlify&logoColor=white" alt="Netlify">
  <img src="https://img.shields.io/badge/n8n-Automation-EA4B71" alt="n8n">
</p>

A modern, browser-based business management dashboard built with **HTML5, CSS3, and Vanilla JavaScript**. The application provides a single workspace for managing customers, leads, projects, tasks, reports, profile information, workspace preferences, and n8n automation settings.

## Live Demo

[Open IT Cyber Business Suite](https://peaceful-paprenjak-c949b3.netlify.app/)

## Project Overview

IT Cyber Business Suite is a frontend business dashboard designed to demonstrate practical dashboard development without using frontend frameworks. It provides interactive forms, searchable data tables, business reports, configurable settings, local browser storage, and an advanced n8n integration page.

## Features

### Dashboard

- Business overview and performance summary
- Monthly performance section
- Recent activities
- Recent project pipeline
- Project search and status filters

### Customer Management

- Add and manage customer records
- Search by customer name, company, or email
- Filter customers by account status
- Store customer contact and joining-date information

### Lead Management

- Add and track sales leads
- Record lead source, estimated value, and pipeline stage
- Search leads by name, company, or email
- Filter opportunities by sales stage

### Project Management

- Create and manage client projects
- Track start dates, deadlines, and project status
- Search by project name or client
- Filter projects by status

### Task Management

- Create and assign tasks
- Set due dates and priorities
- Track task completion status
- Search by task title or assignee
- Filter tasks by priority and status

### Reports

- Business performance reporting
- Monthly revenue overview
- Project distribution overview
- Selectable reporting periods
- Export report data in CSV format

### Profile Management

- Edit personal and professional information
- Upload or remove a profile photo
- View account statistics and workspace information
- Manage profile shortcuts and notification preferences

### Settings

- Profile and business information
- Light, dark, and system themes
- Accent color selection
- Layout density and text-size controls
- Locale, timezone, currency, and date-format preferences
- Browser and workspace notification preferences
- Security and session preferences
- JSON data import, export, and reset controls

### n8n Automation Configuration

- Connect an n8n Cloud or self-hosted instance
- Configure API access and connection settings
- Test instance health and API keys
- Test n8n webhook endpoints
- Generate self-hosted environment variables
- Generate cURL, JavaScript, and Netlify proxy examples
- Review connection diagnostics
- Export a redacted n8n configuration backup

## Technologies Used

- **HTML5** — application structure and semantic markup
- **CSS3** — layout, components, themes, and visual styling
- **Vanilla JavaScript** — application logic and interactions
- **LocalStorage** — browser-based data persistence
- **Netlify** — deployment and hosting
- **n8n** — optional workflow automation integration

## Data Storage

This project is a frontend demonstration. Customer, lead, project, task, profile, preference, and integration data are stored in the user's browser using LocalStorage.

> Clearing browser storage may remove saved application data. Export a JSON backup from the Settings page before resetting browser data.

## Installation

### 1. Clone the repository

```bash
git clone YOUR_REPOSITORY_URL
```

### 2. Open the project directory

```bash
cd YOUR_PROJECT_FOLDER
```

### 3. Run the project

You can open `index.html` directly in a browser or run a local development server.

Using Visual Studio Code Live Server:

1. Open the project folder in Visual Studio Code.
2. Install the **Live Server** extension.
3. Right-click `index.html`.
4. Select **Open with Live Server**.

Using Python:

```bash
python -m http.server 5500
```

Then open:

```text
http://localhost:5500
```

## Deployment on Netlify

1. Push the project to a GitHub repository.
2. Sign in to Netlify.
3. Select **Add new site** and choose **Import an existing project**.
4. Connect the GitHub repository.
5. Leave the build command empty for a static HTML project.
6. Set the publish directory to the folder containing `index.html`.
7. Deploy the site.

## n8n Security Note

n8n API keys and webhook secrets are sensitive. For production use, requests should be sent through a secure backend or a Netlify Function instead of exposing private credentials directly in frontend JavaScript.

Do not commit API keys, webhook secrets, passwords, or environment files to GitHub.

## Recommended Repository Files

```text
project-root/
├── index.html
├── customers.html
├── leads.html
├── projects.html
├── tasks.html
├── reports.html
├── settings.html
├── profile.html
├── n8n-config.html
├── css/
├── js/
├── assets/
├── README.md
└── .gitignore
```

Adjust this example structure to match the actual project files.

## Future Improvements

- Connect the dashboard to a secure backend and database
- Add user authentication and role-based access
- Add server-side validation
- Synchronize data across devices
- Add automated email and task workflows through n8n
- Add unit and browser testing
- Improve accessibility and keyboard navigation

## Author

**Aniket Rathod**  
Frontend Developer

## License

This project is intended for educational and portfolio use. Add a license file before allowing redistribution or commercial use.

---

Built with HTML, CSS, and JavaScript.
