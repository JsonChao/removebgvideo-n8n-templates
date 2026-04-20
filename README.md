# RemoveBGVideo n8n Templates

Import-ready n8n workflows for RemoveBGVideo Public API v1.

## Included Templates

1. `removebgvideo-url-auto-start-poll.json`
- Input: hosted `video_url`
- Flow: create job (`auto_start=true`) -> get status

2. `removebgvideo-local-upload-v1.json`
- Input: local file path
- Flow: `POST /v1/uploads` -> `POST /v1/jobs`

3. `removebgvideo-draft-start-pro.json`
- Input: hosted `video_url`
- Flow: create draft (`auto_start=false`) -> start with `text_prompt`

4. `removebgvideo-webhook-receiver.json`
- Input: webhook callback from RemoveBGVideo backend
- Flow: receive -> extract fields -> respond 200

5. `removebgvideo-usage-daily-report.json`
- Input: schedule trigger
- Flow: query `/v1/usage/summary` -> format report string

## Variables to Replace

- `YOUR_API_KEY`
- `https://cdn.removebgvideo.com/uploads/demo.mp4` (replace with your own video URL)
- `https://your-app.com/webhooks/removebgvideo` (for webhook template)
- `/path/to/video.mp4` (for local upload template)

## Import Steps (n8n)

1. Open n8n -> Workflows
2. Click `Import from File`
3. Select one JSON file from `workflows/`
4. Replace placeholders in HTTP nodes
5. Run test execution

## API Endpoints Used

- `POST /v1/uploads`
- `POST /v1/jobs`
- `POST /v1/jobs/{job_id}/start`
- `GET /v1/jobs/{job_id}`
- `GET /v1/usage/summary`

Base URL: `https://api.removebgvideo.com`
