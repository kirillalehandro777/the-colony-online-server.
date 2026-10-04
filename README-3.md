# The Colony Online Server — Render + PostgreSQL

Free-tier friendly backend for The Colony.

## Environment variables

- `DATABASE_URL` — PostgreSQL connection string from Supabase.
- `CORS_ORIGIN` — optional comma-separated allowed origins. For the HTML game use `*` initially.
- `PORT` — Render supplies this automatically.

The server creates its PostgreSQL tables automatically on startup.

## Local run

```bash
npm install
DATABASE_URL="postgresql://..." CORS_ORIGIN="*" npm start
```

Health check:

`GET /health`

Expected response contains `ok: true` and `protocol: 3`.

## API

- `POST /v1/register`
- `GET /v1/me`
- `GET /v1/state`
- `PUT /v1/state`
- `POST /v1/sync`
- `GET /v1/tournament`

Tournament events are idempotent and validated server-side.

Cloud saves are normalized but are not yet a fully authoritative economy. The next security phase should replace whole-state economy writes with server-authoritative gameplay commands.
