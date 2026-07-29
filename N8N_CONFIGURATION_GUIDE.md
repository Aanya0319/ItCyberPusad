# n8n Configuration Guide

This project includes an advanced n8n configuration page at `n8n-config.html` and a secure Netlify Function at `netlify/functions/n8n-proxy.js`.

## What the page can do

- Save an n8n Cloud, self-hosted or local instance URL
- Keep an API key in session storage by default
- Optionally remember an API key in LocalStorage on a trusted device
- Test the n8n `/healthz` endpoint
- Test public REST API authentication through `/api/v1/workflows?limit=1`
- Test n8n Webhook node Test and Production URLs
- Validate and format JSON webhook payloads
- Add an optional custom webhook header
- Display status, response body, timing and diagnostic logs
- Generate self-hosted environment variables
- Generate cURL, server-side JavaScript and Netlify proxy examples
- Export a redacted configuration backup
- Remove saved n8n configuration and logs

## Recommended secure setup on Netlify

The safest frontend deployment uses the included Netlify Function. The browser calls the same-origin function and the function reads the n8n API key from Netlify environment variables.

### 1. Deploy the project

Push the complete project to GitHub and connect that repository to Netlify. The included `netlify.toml` sets the publish directory and functions directory.

### 2. Add Netlify environment variables

Open the deployed site's configuration and add:

```text
N8N_BASE_URL=https://your-workspace.app.n8n.cloud
N8N_API_KEY=your-secret-api-key
N8N_API_BASE_PATH=/api/v1
```

Do not add the API key to Git, HTML, JavaScript or a public `.env` file.

### 3. Configure the dashboard

1. Open **Settings → n8n Automation**.
2. Select **Secure Netlify Function** as the connection route.
3. Keep the proxy endpoint as `/.netlify/functions/n8n-proxy`.
4. Enter the n8n instance URL for display and generated examples.
5. Select **Test health**.
6. Select **Test API key**.
7. Save the connection.

In proxy mode, the API key input is disabled because the secret comes from Netlify environment variables.

## Direct browser mode

Direct browser mode calls the n8n instance from the user's browser. It can work for development or tightly controlled internal deployments, but it has two important limitations:

1. The API key is present in the browser while the request is made.
2. The n8n server must allow the dashboard origin through CORS.

The configuration page keeps the key in `sessionStorage` unless **Save API key in this browser's LocalStorage** is explicitly selected.

## Create an n8n API key

1. Sign in to n8n.
2. Open **Settings**.
3. Open **n8n API**.
4. Create an API key with a descriptive label and suitable expiration.
5. Copy the key once and store it securely.

Official guide:

- https://docs.n8n.io/connect/n8n-api/authentication/

## Webhook tester setup

### Test URL

1. Add a Webhook node to an n8n workflow.
2. Configure the HTTP method to match the dashboard tester.
3. Select **Listen for test event** in n8n.
4. Copy the Test URL into the dashboard.
5. Send the webhook.

### Production URL

1. Finish and publish/activate the workflow.
2. Copy the Production URL.
3. Add it to the dashboard.
4. Select **Production URL** in the tester.
5. Send the request.

For browser requests, configure **Allowed Origins (CORS)** in the Webhook node using the exact dashboard origin, such as:

```text
https://your-dashboard.netlify.app
```

Official webhook guide:

- https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook/

## Self-hosted environment variables

The page generates a starting `.env` configuration:

```text
N8N_HOST=n8n.example.com
N8N_PORT=5678
N8N_PROTOCOL=https
N8N_EDITOR_BASE_URL=https://n8n.example.com/
WEBHOOK_URL=https://n8n.example.com/
GENERIC_TIMEZONE=Asia/Kolkata
TZ=Asia/Kolkata
N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true
N8N_ENCRYPTION_KEY=replace-with-a-long-random-secret
```

Important:

- Use HTTPS for public deployments.
- Keep `N8N_ENCRYPTION_KEY` private and backed up.
- Set `WEBHOOK_URL` to the public URL when n8n is behind a reverse proxy.
- Use a database, backups and monitoring appropriate for production workloads.

Official resources:

- https://docs.n8n.io/deploy/host-n8n/install-options/install-with-docker
- https://docs.n8n.io/deploy/host-n8n/configure-n8n/basic-configuration/use-environment-variables/
- https://docs.n8n.io/deploy/host-n8n/keep-n8n-running/monitor-n8n

## Troubleshooting

### Browser says the request may be blocked by CORS

Use **Secure Netlify Function** mode for REST API tests. For Webhook node calls, set the Webhook node's Allowed Origins to the deployed dashboard origin.

### Health check fails

Check:

- The instance URL is public and correct
- HTTPS certificate is valid
- `/healthz` is available
- Firewall or reverse-proxy rules allow the request
- The request timeout is sufficient

### API key test returns 401 or 403

Check:

- The key is current and not expired
- The value was copied without extra spaces
- The Netlify `N8N_API_KEY` environment variable is set in proxy mode
- The REST API base path is `/api/v1` unless the instance was customized

### Netlify proxy returns missing environment-variable errors

Add the required variables in Netlify and trigger a new deployment. Environment-variable changes do not become available to an already-built function until the site/function is redeployed.

### Test webhook works but production webhook does not

Publish/activate the n8n workflow and use the Production URL rather than the Test URL.

## Security checklist

- Prefer the Netlify Function proxy for REST API access
- Never commit API keys
- Use expiring API keys where appropriate
- Rotate a key immediately if it is exposed
- Restrict webhook CORS to exact trusted origins
- Protect sensitive webhooks with authentication or a secret header
- Use HTTPS
- Do not log secrets or full sensitive payloads
- Keep n8n updated and backed up
