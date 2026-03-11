# StatusCake Bulk Uptime Insert

A lightweight, client-side tool for bulk inserting uptime monitoring tests into [StatusCake](https://www.statuscake.com/) via the v1 API.

Generates executable **bash scripts** with `curl` commands — no server required, no CORS issues.

## 🚀 Live Demo

**[Open the tool →](https://YOUR_USERNAME.github.io/statuscake-bulk-uptime/)**

## How It Works

1. **Enter your API key** — Get it from StatusCake → Account → API Keys
2. **Generate a connection test script** — Verifies your key works, shows existing tests, contact groups, and monitoring regions
3. **Paste your test data** (CSV or JSON) — Parse & validate before sending
4. **Generate a bulk insert script** — Download or copy the bash script and run it locally

The tool never sends your API key to any third party. Everything runs in your browser — scripts are generated client-side and executed on your machine.

## Input Formats

### CSV

```csv
name,website_url,test_type,check_rate
Production Site,https://example.com,HTTP,300
Staging API,https://staging-api.example.com,HTTP,60
Mail Server,mail.example.com,SMTP,1800
```

### JSON

```json
[
  {
    "name": "Production Site",
    "website_url": "https://example.com",
    "test_type": "HTTP",
    "check_rate": 300,
    "contact_groups": ["12345"],
    "tags": ["production"]
  }
]
```

## Fields

| Field | Required | Description |
|-------|----------|-------------|
| `name` | ✅ | Display name for the test |
| `website_url` | ✅ | URL or IP to monitor |
| `test_type` | ✅ | `HTTP`, `HEAD`, `TCP`, `DNS`, `SMTP`, `SSH`, `PING`, or `PUSH` |
| `check_rate` | ✅ | Interval in seconds: `0`, `30`, `60`, `300`, `900`, `1800`, `3600` |
| `confirmation` | | Number of confirmation servers (reduces false positives) |
| `contact_groups` | | Array of contact group IDs |
| `tags` | | Array of tags |
| `regions` | | Array of monitoring regions |

## Deploy to GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch** → `main` / `root`
4. Your tool will be live at `https://YOUR_USERNAME.github.io/statuscake-bulk-uptime/`

Or just download `index.html` and open it locally — it's fully self-contained.

## API Reference

This tool uses the [StatusCake v1 API](https://developers.statuscake.com/api/):

- `GET /v1/uptime` — List existing uptime tests
- `POST /v1/uptime` — Create a new uptime test
- `GET /v1/contact-groups` — List contact groups
- `GET /v1/uptime-locations` — List monitoring regions

Authentication: `Authorization: Bearer YOUR_API_KEY`

## License

MIT
