# Help Center QA Demo

Minimal chat demo that routes questions to a single help-center page by title and summarizes only that page.

## Demo

<video src="./wegic-help-center-qa.mp4?raw=1" controls playsinline></video>

## Architecture Overview

### Components
- **Ingest script**: `scripts/ingest.js`
  - Reads `public/sitemap.xml`
  - Fetches each page, extracts title + content
  - Writes a local index to `data/docs.json`
- **API server**: `server.js`
  - Serves static UI from `public/`
  - Routes user question → candidate doc IDs (LLM)
  - Summarizes only the selected doc (LLM)
  - Fallback to Facebook contact when no answer
- **Frontend**: `public/index.html`
  - Minimal chat UI with user/Kimmy bubbles
  - `Test Connect` button for quick validation
- **Skill (optional)**: `.cursor/skills/help-center-qa/`
  - Independent Help Center QA behavior for agent use

### Data Flow (Runtime)
```
User Question
  → /api/chat
    → LLM selects candidate doc IDs (title list)
    → LLM summarizes selected doc content
    → Response (or fallback)
  → UI displays chat bubbles
```

### Data Flow (Ingest)
```
public/sitemap.xml
  → scripts/ingest.js
    → fetch pages + extract content
    → data/docs.json
```

## Integration Notes

- **LLM provider**: LiteLLM Proxy (OpenAI-compatible)
  - Endpoint: `LITELLM_BASE_URL + /v1/chat/completions`
  - Model: `LITELLM_MODEL`
  - Auth: `LITELLM_API_KEY`
- **Doc-only answers**: responses are constrained to the selected doc.
- **Fallback**: if doc does not contain the answer, return the fixed Facebook message.

## Optimization Ideas

- **Reduce latency**
  - Use a faster model for routing (title selection).
  - Trim document content more aggressively (reduce tokens).
  - Add caching for repeated questions.
  - Consider streaming responses for faster perceived latency.
- **Improve accuracy**
  - Add a second-pass rerank for candidate IDs.
  - Add simple keyword heuristics before LLM routing.
- **Observability**
  - Log latency per step (routing vs summary).
  - Track top failed queries and missing topics.

## Setup

1) Install dependencies
```
npm install
```

2) Ingest docs from the sitemap you downloaded
```
npm run ingest
```

3) Start the server
```
# Option A: use env vars
export LITELLM_API_KEY="your_key"
export LITELLM_BASE_URL="https://litellm-stable180.geesdev.com"
export LITELLM_MODEL="vertex_ai/claude-sonnet-4-5"

# Option B: create .env from the example
# cp .env.example .env

npm start
```

Open `http://localhost:3000`.

## Notes

- Default sitemap path: `public/sitemap.xml`
- You can override it:
```
SITEMAP_PATH="/path/to/sitemap.xml" npm run ingest
```

- Docs are stored in `data/docs.json`

# TODO
- sitemap自动化抓取更新
- help center qa意图识别与skill路由，避免与agent执行任务冲突