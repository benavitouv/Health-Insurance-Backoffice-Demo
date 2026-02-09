# Health Insurance Request UI

Hebrew UI for submitting health insurance requests. The server accepts the form, uploads the attachment, and calls the webhook with the `Process this insurance request` message and the attachment id.

## Requirements

- Node.js 18+ (tested with Node 25)

## Run locally

```bash
npm start
```

Server defaults to `http://localhost:5173`.

## Configuration

The server uses these environment variables (defaults are baked in for the demo; set env vars to override).

Required (override if needed):

- `WEBHOOK_URL` - webhook endpoint URL.
- `WEBHOOK_SECRET` - value for the `x-webhook-secret` header.
- `STORAGE_URL` - storage API endpoint URL.
- `STORAGE_API_KEY` - value for the `X-API-Key` header.

Optional:

- `BASE_URL` - base URL for the Wonderful demo app (used to derive the API base URL).
- `API_BASE_URL` - API base URL (defaults to the `BASE_URL` with `wonderful.app` replaced by `api`).
- `PORT` - server port (default `5173`).

Defaults currently in code (edit `server.mjs` or set env vars if you need to change the task metadata):

- `BASE_URL`: `https://wonderful.app.demo.wonderful.ai`
- `WEBHOOK_URL`: `https://api.demo.wonderful.ai/api/v1/tasks/webhook/7a86a4e3-ed34-4307-b44c-57bc94f795b3`
- `WEBHOOK_SECRET`: `05d5dc71-c710-470d-88bf-6f038763b95b`
- `STORAGE_URL`: `https://api.demo.wonderful.ai/api/v1/storage`
- `STORAGE_API_KEY`: `f2440f35-f26d-4145-8c15-295b40987ed6`
- `task_type`: `process_application`
- `trigger_id`: `4fd88805-7cde-4a7a-9d99-5347e5fb308e`

## Vercel Deployment

Set the required environment variables in the Vercel dashboard (Project → Settings → Environment Variables) before deploying. The frontend does not receive these values.

### Example (placeholders)

```bash
PORT=5173 \\
WEBHOOK_URL=<your_webhook_url> \\
WEBHOOK_SECRET=<your_webhook_secret> \\
STORAGE_URL=<your_storage_url> \\
STORAGE_API_KEY=<your_storage_api_key> \\
npm start
```
