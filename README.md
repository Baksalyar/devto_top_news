# devto_top_news

The top-of-the-month news from DEV.to, packaged as RSS.

Builds an RSS feed for the top DEV.to posts from the last 30 days. It pulls the top list from the DEV.to public API, fetches each article body, and includes 2-3 paragraphs per item.

## Setup

### Poetry

```bash
poetry install
```

Run:

```bash
poetry run python devto_top_month_rss.py
```

### pip

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Run

```bash
python devto_top_month_rss.py
```

Daemon mode (random interval between 15-20 minutes):

```bash
python devto_top_month_rss.py --daemon --min-interval 900 --max-interval 1200
```

Serve the feed over HTTP and auto-refresh in one process:

```bash
python devto_top_month_rss.py --serve --port 8000 --min-interval 900 --max-interval 1200
```

Then subscribe to: `http://localhost:8000/devto_top_month.xml`

The script writes a small state file to track new items:

- `devto_top_month_state.json`

Options:

```bash
python devto_top_month_rss.py --limit 20 --top-days 30 --output devto_top_month.xml
```

## Public distribution (GitHub Pages)

Once GitHub Pages is enabled for this repository, your feed URL will be:

`https://baksalyar.github.io/devto_top_news/devto_top_month.xml`
