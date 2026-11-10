# Job Radar

A webhook workflow for searching recent job posts relevant to Python, FastAPI, backend and data roles. The result is a ranked JSON list.

**Flow:** Webhook -> Search Settings -> HTTP Request (Arbeitnow) -> Score And Filter Jobs -> Respond

## Run

Import `workflow.json` into n8n. In the Webhook node click **Listen for test event** and open:

`http://localhost:5678/webhook-test/job-radar?city=Berlin&limit=5`

Use `city=all` to include all locations or `city=remote` to restrict to remote posts. The filter also permits remote jobs when filtering by city. `limit` accepts 1–30 jobs.

## Result

Returns: `checked`, `matching`, `returned`, and a list of jobs with `title`, `company`, `location`, `score`, and `link`.

## What I used

- n8n Webhook and HTTP Request
- JavaScript Code nodes, keyword filtering and simple score calculation
- Public Arbeitnow API (no key needed)

## Limits

The workflow checks only one page of recent posts and uses keyword matching, not machine learning. Job availability and API content can change. The data provider is [Arbeitnow](https://www.arbeitnow.com/).
