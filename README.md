# RemoveBGVideo n8n Templates

Import-ready n8n workflows for the RemoveBGVideo Public API v1.

- API Base: `https://api.removebgvideo.com`
- Docs: `https://removebgvideo.com/docs/examples/n8n`
- Website downloads mirror: `https://removebgvideo.com/downloads/n8n/`

## Included Templates

| Template | Purpose | Core Flow |
|---|---|---|
| `removebgvideo-url-auto-start-poll.json` | Simplest URL-based flow | `POST /v1/jobs` (`auto_start=true`) -> `GET /v1/jobs/{job_id}` |
| `removebgvideo-local-upload-v1.json` | Local file integration | `POST /v1/uploads` -> `POST /v1/jobs` |
| `removebgvideo-draft-start-pro.json` | Prompt/composition control | Draft job (`auto_start=false`) -> `POST /v1/jobs/{job_id}/start` |
| `removebgvideo-webhook-receiver.json` | Callback ingestion | Receive `job.*` webhook -> parse -> respond 200 |
| `removebgvideo-usage-daily-report.json` | Ops/monitoring | Schedule trigger -> `GET /v1/usage/summary` |

## Quick Start

1. Open n8n -> `Workflows` -> `Import from File`
2. Select one JSON file from `workflows/`
3. Replace placeholder values (see below)
4. Run `Test workflow`
5. Verify output URL or usage payload in execution data

## Required Placeholder Replacements

- `YOUR_API_KEY`
- `https://cdn.removebgvideo.com/uploads/382dcf8d-f1ee-43be-a514-b85a1541d017.mp4` (replace with your own input video URL)
- `https://removebgvideo.com/webhooks/removebgvideo` (webhook template)
- `/path/to/video.mp4` (local upload template)

## API Endpoints Used

- `POST /v1/uploads`
- `POST /v1/jobs`
- `POST /v1/jobs/{job_id}/start`
- `GET /v1/jobs/{job_id}`
- `GET /v1/usage/summary`

## Notes

- Use `webhook_url` in job payload for high-volume automations to reduce polling pressure.
- For production, store `job_id` and external correlation id in your own DB/log system.
- Keep one API key per environment (dev/stage/prod) and rotate periodically.
