# SEO Scout - Website SEO Analysis Tool

A comprehensive, real-time SEO analysis tool that helps website owners, marketers, and developers identify and fix SEO issues to improve search engine rankings.

## Demo

<video controls preload="metadata">
  <source src="./SEO-Scout.preview.mp4?raw=1" type="video/mp4" />
</video>

Full video: [download](./SEO-Scout.mp4?raw=1)

## What is SEO Scout?

SEO Scout is a web-based application that analyzes any website URL and provides actionable insights across multiple SEO dimensions. Simply enter a URL, and receive a detailed audit report with scores, issues, and recommendations.

## Key Features

### Core Analysis Capabilities

- **SEO Score Overview** - Overall health score with breakdown by category
- **Sitemap Analysis** - Parse and validate XML sitemaps, detect missing pages
- **Meta Tags Audit** - Check title, description, keywords, and other meta information
- **OpenGraph & Twitter Cards** - Social media preview optimization
- **On-Page SEO** - Headings structure, image alt texts, internal/external links
- **Indexability Check** - Robots.txt, canonical tags, noindex directives

### Advanced Detection (12 Categories)

| Category | What We Check |
|----------|---------------|
| Security | HTTPS implementation, mixed content |
| URL Structure | Length, underscores, special characters |
| Twitter Cards | Card type, required meta tags |
| AI Crawlers | GPTBot, Claude-Web blocking detection |
| Multilingual | hreflang tags, language declarations |
| Structured Data | JSON-LD, Schema.org markup |
| HTML Structure | Tables, lists, semantic elements |
| External Links | Nofollow attributes, link quality |
| Performance | Lazy loading, resource optimization |
| Content Quality | Word count, heading hierarchy |
| JavaScript | Client-side rendering detection |
| Technical | Viewport, favicon, charset |

### Issue-Based Reporting

Following professional SEO tools like Ahrefs and Semrush:
- **Errors** (Critical) - Issues that significantly impact SEO
- **Warnings** - Potential improvements to consider
- **Passed** - Correctly implemented SEO elements

## Problems It Solves

1. **Time-Consuming Manual Audits** - Automates the tedious process of checking dozens of SEO factors
2. **Technical Complexity** - Translates technical SEO issues into understandable recommendations
3. **Scattered Information** - Consolidates sitemap, meta, content, and technical SEO in one dashboard
4. **Missed Opportunities** - Identifies SEO improvements you might not know about
5. **Social Media Visibility** - Ensures your content looks great when shared on social platforms

## User Journey

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER JOURNEY                              │
└─────────────────────────────────────────────────────────────────┘

1. ENTER URL
   ┌─────────────────────────────────────┐
   │  🔗 Enter website URL               │
   │  [https://example.com    ] [Analyze]│
   └─────────────────────────────────────┘
                    │
                    ▼
2. WAIT FOR ANALYSIS (2-5 seconds)
   ┌─────────────────────────────────────┐
   │  ⏳ Fetching and analyzing...       │
   │  ████████████░░░░░░░░ 60%           │
   └─────────────────────────────────────┘
                    │
                    ▼
3. VIEW RESULTS
   ┌─────────────────────────────────────┐
   │  📊 SEO Score: 78/100               │
   │  ┌───────┬───────┬───────┬───────┐  │
   │  │Overview│Sitemap│On-Page│ Meta │  │
   │  └───────┴───────┴───────┴───────┘  │
   │                                     │
   │  ❌ 3 Errors  ⚠️ 5 Warnings  ✅ 12  │
   └─────────────────────────────────────┘
                    │
                    ▼
4. EXPLORE DETAILED ISSUES
   ┌─────────────────────────────────────┐
   │  Error: Missing meta description    │
   │  → Add a 150-160 character desc...  │
   │                                     │
   │  Warning: Images without alt text   │
   │  → Add descriptive alt attributes...│
   └─────────────────────────────────────┘
                    │
                    ▼
5. TAKE ACTION
   ┌─────────────────────────────────────┐
   │  ✓ Fix issues on your website       │
   │  ✓ Re-analyze to verify fixes       │
   │  ✓ Improve your search rankings     │
   └─────────────────────────────────────┘
```

## Data Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                      DATA WORKFLOW                               │
└─────────────────────────────────────────────────────────────────┘

                    ┌──────────────┐
                    │   Browser    │
                    │  (Frontend)  │
                    └──────┬───────┘
                           │
                           │ 1. POST /api/analyze
                           │    { url: "https://..." }
                           ▼
                    ┌──────────────┐
                    │   Express    │
                    │   Server     │
                    └──────┬───────┘
                           │
         ┌─────────────────┼─────────────────┐
         │                 │                 │
         ▼                 ▼                 ▼
┌─────────────┐   ┌─────────────┐   ┌─────────────┐
│ SSRF Check  │   │ Fetch HTML  │   │Fetch Sitemap│
│ (Security)  │   │  (Cheerio)  │   │  (xml2js)   │
└──────┬──────┘   └──────┬──────┘   └──────┬──────┘
       │                 │                 │
       │    ┌────────────┴────────────┐    │
       │    │                         │    │
       │    ▼                         ▼    │
       │ ┌─────────┐           ┌─────────┐ │
       │ │  Parse  │           │  Parse  │ │
       │ │  HTML   │           │   XML   │ │
       │ └────┬────┘           └────┬────┘ │
       │      │                     │      │
       │      └──────────┬──────────┘      │
       │                 │                 │
       │                 ▼                 │
       │    ┌─────────────────────────┐    │
       │    │    Analysis Engine      │    │
       │    │                         │    │
       │    │  • Meta Tags Extraction │    │
       │    │  • OpenGraph Parsing    │    │
       │    │  • Heading Structure    │    │
       │    │  • Link Analysis        │    │
       │    │  • Image Alt Checks     │    │
       │    │  • Security Checks      │    │
       │    │  • Structured Data      │    │
       │    └────────────┬────────────┘    │
       │                 │                 │
       │                 ▼                 │
       │    ┌─────────────────────────┐    │
       │    │    Issue Generator      │    │
       │    │                         │    │
       │    │  Categorize findings:   │    │
       │    │  • Errors (critical)    │    │
       │    │  • Warnings (improve)   │    │
       │    │  • Passed (correct)     │    │
       │    └────────────┬────────────┘    │
       │                 │                 │
       │                 ▼                 │
       │    ┌─────────────────────────┐    │
       │    │    Score Calculator     │    │
       │    │                         │    │
       │    │  Weighted scoring by:   │    │
       │    │  • Category importance  │    │
       │    │  • Issue severity       │    │
       │    └────────────┬────────────┘    │
       │                 │                 │
       └────────────────►│◄────────────────┘
                         │
                         ▼
                ┌─────────────────┐
                │  JSON Response  │
                │                 │
                │ {               │
                │   score: 78,    │
                │   issues: [...],│
                │   meta: {...},  │
                │   sitemap: {...}│
                │ }               │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │    Frontend     │
                │   Rendering     │
                │                 │
                │  • Score Card   │
                │  • Issue Lists  │
                │  • Tab Panels   │
                │  • Charts       │
                └─────────────────┘
```

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React 18, TypeScript, Tailwind CSS, shadcn/ui |
| Backend | Express.js, Node.js |
| HTML Parsing | Cheerio |
| XML Parsing | xml2js |
| State Management | TanStack Query |
| Routing | Wouter |
| Validation | Zod |

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/seo-scout.git

# Install dependencies
npm install

# Start development server
npm run dev
```

The application will be available at `http://localhost:5000`

## Security

SEO Scout implements comprehensive SSRF (Server-Side Request Forgery) protection:

- Protocol whitelist (HTTP/HTTPS only)
- Port restrictions (80, 443)
- Private IP range blocking
- DNS resolution validation
- Credential blocking in URLs

## License

MIT License - See LICENSE file for details

## Contributing

Contributions are welcome! Please read our contributing guidelines before submitting a pull request.

---

Built with care for the SEO community.
