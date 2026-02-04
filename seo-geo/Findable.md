# Findable - SEO & AI Visibility Assistant

A Progressive Web App (PWA) that helps small business owners check if their website can be found by search engines and AI assistants.

## Demo

Demo video: [download](./findable.mp4?raw=1)

## Features

- **One-Click Health Check**: Enter your domain and get instant visibility scores
- **Dual Scoring System**: 
  - Search Findability (SEO Ready) 
  - AI Readiness (GEO Ready)
- **3-Step Action Plan**: Actionable tasks prioritized by impact
- **Ready-to-Use Deliverables**: Copy-paste content including:
  - Optimized titles and descriptions
  - AI-quotable answer blocks
  - FAQ content
  - JSON-LD schema snippets
- **Export Options**: Download CSV and Markdown reports

## Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **PWA**: next-pwa

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn
- (Optional) AI API Key for intelligent content generation

### Installation

```bash
# Install dependencies
npm install

# (Optional) Configure AI API Key
cp env.example .env.local
# Edit .env.local and add your API key

# Run development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### AI Configuration (Optional)

The app can use AI to generate smarter, more personalized content suggestions. Without AI, it uses rule-based generation which still works well.

**Supported AI Providers:**

| Provider | Model | Cost |
|----------|-------|------|
| OpenAI | gpt-4o-mini | ~$0.15/1M tokens |
| OpenAI | gpt-4o | ~$5/1M tokens |
| Anthropic | claude-3-haiku | ~$0.25/1M tokens |
| Anthropic | claude-3-sonnet | ~$3/1M tokens |
| Custom | Any OpenAI-compatible | Varies |

**Setup:**

1. Copy `env.example` to `.env.local`
2. Add your API key (choose one):

```bash
# OpenAI (recommended)
OPENAI_API_KEY=sk-your-key-here
OPENAI_MODEL=gpt-4o-mini

# OR Anthropic
ANTHROPIC_API_KEY=sk-ant-your-key-here
ANTHROPIC_MODEL=claude-3-haiku-20240307
```

3. Restart the dev server

### Build for Production

```bash
# Build the application
npm run build

# Start production server
npm start
```

## Project Structure

```
src/
├── app/
│   ├── api/
│   │   └── scan/
│   │       └── route.ts      # Real scan API endpoint
│   ├── deliverables/
│   │   └── page.tsx          # Page D: Deliverables
│   ├── plan/
│   │   └── page.tsx          # Page C: 3-Step Action Plan
│   ├── results/
│   │   └── page.tsx          # Page B: Scan Results
│   ├── globals.css           # Global styles
│   ├── layout.tsx            # Root layout
│   └── page.tsx              # Page A: Home (Input)
├── components/
│   ├── CopyButton.tsx        # One-click copy component
│   ├── LoadingScreen.tsx     # Scan loading animation
│   ├── ScoreRing.tsx         # Animated score circle
│   └── TaskCard.tsx          # Action plan task card
├── lib/
│   ├── scanner.ts            # Web page crawler & parser
│   ├── seo-rules.ts          # SEO check rules (10 rules)
│   ├── geo-rules.ts          # GEO/AI check rules (6 rules)
│   └── ai-generator.ts       # AI content generator
├── types/
│   └── index.ts              # TypeScript type definitions
public/
├── icons/                    # PWA icons
└── manifest.json             # PWA manifest
```

## Pages

1. **Home (/)**: URL input with recent scan history
2. **Results (/results)**: Dual scores with consultant summary
3. **Plan (/plan)**: 3 actionable tasks with completion tracking
4. **Deliverables (/deliverables)**: All optimizations ready to copy

## PWA Features

- Installable on mobile and desktop
- Offline access to last scan results
- Service worker for caching static assets

## Real Scanning Features

The app now performs **real website scanning**:

### SEO Checks (10 rules)
- Missing/short page titles
- Missing meta descriptions
- H1 heading issues (missing/multiple)
- Missing canonical tags
- robots.txt blocking
- Missing sitemap
- Page errors (4xx/5xx)
- Thin content detection
- Meta robots noindex

### GEO/AI Checks (6 rules)
- Answer block quality (first paragraph)
- Content structure (headings/lists)
- FAQ presence detection
- FAQPage schema detection
- Any structured data (JSON-LD)
- AI quotability analysis

### AI Generation
With an AI API key configured:
- Generates personalized title/description suggestions
- Creates contextual FAQ content
- Produces relevant answer blocks

Without AI:
- Uses intelligent rule-based generation
- Still produces useful, actionable content

## Notes

- Icons are SVG placeholders - generate PNGs for production
- Real scanning requires network access to target websites
- Some sites may block the crawler (403 errors)

## License

MIT

