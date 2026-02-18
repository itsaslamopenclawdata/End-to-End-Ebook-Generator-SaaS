# Open Source Tools & Components - Complete Tech Stack

> **Purpose:** Catalog all open source tools, libraries, and components for building the complete Ebook Generator SaaS
> **Goal:** Build, test, and deploy entire SaaS locally or with minimum cloud spending
> **Repository:** https://github.com/itsaslamopenclawdata/End-to-End-Ebook-Generator-SaaS
> **Last Updated:** 2026-02-18

---

## 🎯 Technology Philosophy

**"Use best-of-breed open source tools. Minimize cloud spending. Deploy locally first, scale when needed."**

**Core Principles:**
1. **Open Source First** - All tools are free and open source
2. **Local Development** - Run everything locally during development
3. **Minimal Cloud Costs** - Only pay for what's absolutely necessary
4. **Self-Host When Possible** - Host databases, APIs, and services locally
5. **Scalable Architecture** - Design for easy migration to cloud when needed

---

## 📋 Tech Stack Overview

| Category | Tool/Library | Version | License | Purpose |
|----------|--------------|---------|---------|---------|
| **Frontend Framework** | Next.js | 15+ | MIT | React framework with App Router |
| **Language** | TypeScript | 5.4+ | Apache 2.0 | Type-safe JavaScript |
| **UI Library** | shadcn/ui | Latest | MIT | Component library built on Radix UI |
| **Styling** | Tailwind CSS | 4+ | MIT | Utility-first CSS framework |
| **Backend Runtime** | Node.js | 22+ | MIT | Server-side JavaScript runtime |
| **Database** | Supabase (PostgreSQL) | Latest | Apache 2.0 | Open source Firebase alternative |
| **ORM** | Prisma | 5.5+ | Apache 2.0 | Type-safe database client |
| **API Platform** | OpenAI API | v4 | Commercial | GPT-4 for content generation |
| **PDF Generation** | Puppeteer/Playwright | Latest | Apache 2.0 | Headless Chrome for PDF |
| **EPUB Generation** | Pandoc | Latest | GPL | Universal document converter |
| **MOBI Generation** | KindleGen | Latest | MIT | Kindle format generator |
| **Word Export** | docx | Latest | MIT | .docx file generation |
| **Cover Generation** | nano-banana-pro (Gemini 3 Pro) | Latest | Commercial | AI image generation |
| **Web Scraping** | Puppeteer | Latest | Apache 2.0 | Headless browser scraping |
| **Search** | Brave Search API | v1 | Commercial | Web search for research |
| **Web Fetch** | Playwright | Latest | Apache 2.0 | Web content extraction |
| **Authentication** | Supabase Auth | Latest | Apache 2.0 | User auth and sessions |
| **Real-time** | Supabase Realtime | Latest | Apache 2.0 | Real-time subscriptions |
| **File Storage** | Supabase Storage | Latest | Apache 2.0 | Object storage for ebooks |
| **CDN** | Cloudflare (Optional) | Free tier | MIT | Global content delivery |
| **CI/CD** | GitHub Actions | Latest | MIT | Automated deployment |
| **Testing** | Playwright + Vitest | Latest | MIT | End-to-end testing |
| **Monitoring** | OpenTelemetry | Latest | Apache 2.0 | Observability and logging |

---

## 🏗️ Frontend Stack

### Next.js 15+ (App Router)

**Description:** React framework with built-in routing, SSR, and API routes
**License:** MIT (Free and Open Source)
**Website:** https://nextjs.org

**Key Features:**
- App Router for file-based routing
- React Server Components for performance
- API Routes for backend endpoints
- Server Actions for form handling
- Image optimization
- Font optimization

**Cost:** $0 (Open Source)

**Installation:**
```bash
npx create-next-app@latest ebook-generator --typescript --tailwind
cd ebook-generator
npm install
```

**Configuration:**
```typescript
// next.config.ts
import type { NextConfig } from 'next'

const nextConfig: NextConfig = {
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: '**',
      },
    ],
  },
  experimental: {
    serverActions: {
      bodySizeLimit: '2mb',
    },
  },
}

export default nextConfig
```

### TypeScript 5.4+

**Description:** Type-safe JavaScript superset for better code quality
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://www.typescriptlang.org

**Key Features:**
- Static type checking
- Interface definitions
- Generics for reusable components
- Strict mode for error catching

**Cost:** $0 (Open Source)

**Installation:**
```bash
npm install --save-dev typescript @types/react @types/node
```

**Configuration:**
```json
// tsconfig.json
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [
      {
        "name": "next"
      }
    ]
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
```

### shadcn/ui

**Description:** Beautifully designed components built on Radix UI and Tailwind CSS
**License:** MIT (Free and Open Source)
**Website:** https://ui.shadcn.com

**Key Features:**
- Pre-built accessible components
- Dark mode support
- Responsive design
- Customizable themes
- TypeScript support

**Available Components:**
- Button, Input, Select, Card, Dialog, Dropdown
- Table, Tabs, Badge, Alert, Toast
- Form, Select, Checkbox, Radio, Switch
- Skeleton, Progress, ScrollArea, Separator

**Cost:** $0 (Open Source)

**Installation:**
```bash
npx shadcn-ui@latest init
npx shadcn-ui@latest add button input card
npx shadcn-ui@latest add dialog dropdown
npx shadcn-ui@latest add table tabs form
```

### Tailwind CSS 4+

**Description:** Utility-first CSS framework for rapid UI development
**License:** MIT (Free and Open Source)
**Website:** https://tailwindcss.com

**Key Features:**
- Utility classes for styling
- Responsive breakpoints
- Dark mode support
- Custom configuration
- JIT compiler for production

**Cost:** $0 (Open Source)

**Configuration:**
```javascript
// tailwind.config.ts
import type { Config } from 'tailwindcss'

const config: Config = {
  darkMode: ['class'],
  content: [
    './pages/**/*.{ts,tsx}',
    './components/**/*.{ts,tsx}',
    './app/**/*.{ts,tsx}',
    './src/**/*.{ts,tsx}',
  ],
  theme: {
    extend: {
      colors: {
        border: 'hsl(var(--border))',
        input: 'hsl(var(--input))',
        ring: 'hsl(var(--ring))',
        background: 'hsl(var(--background))',
        foreground: 'hsl(var(--foreground))',
      },
    },
  },
  plugins: [require('tailwindcss-animate')],
}

export default config
```

---

## 🗄️ Backend Stack

### Node.js 22+

**Description:** JavaScript runtime for server-side code execution
**License:** MIT (Free and Open Source)
**Website:** https://nodejs.org

**Key Features:**
- Event-driven architecture
- NPM ecosystem
- Fast I/O operations
- Cross-platform compatibility

**Cost:** $0 (Open Source)

**Version:**
```bash
node --version
# v22.16.0
```

### Supabase (PostgreSQL)

**Description:** Open source Firebase alternative with PostgreSQL database
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://supabase.com

**Key Features:**
- PostgreSQL database (free tier: 500MB)
- Authentication and user management
- Real-time subscriptions
- File storage (1GB free)
- Edge functions
- Row-level security policies

**Free Tier Limits:**
- Database: 500MB
- Auth: Unlimited users
- Storage: 1GB
- Bandwidth: 2GB/month
- Edge Functions: 500,000 invocations/month

**Paid Tiers:**
- Pro: $25/month (8GB DB, 100GB storage)
- Team: $599/month (unlimited projects, priority support)

**Installation:**
```bash
npm install @supabase/supabase-js
```

**Configuration:**
```typescript
// lib/supabase.ts
import { createClient } from '@supabase/supabase-js'

const supabaseUrl = process.env.NEXT_PUBLIC_SUPABASE_URL!
const supabaseAnonKey = process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!

export const supabase = createClient(supabaseUrl, supabaseAnonKey)

// Types
export type Database = {
  public: {
    Tables: {
      users: {
        Row: { id: string; email: string; created_at: string }
      }
      ebooks: {
        Row: { id: string; user_id: string; title: string; content: string }
      }
    }
  }
}
```

### Prisma 5.5+

**Description:** Type-safe database ORM for PostgreSQL
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://www.prisma.io

**Key Features:**
- Type-safe database queries
- Automatic migrations
- Schema visualization
- Seed data management
- Connection pooling

**Cost:** $0 (Open Source for development, $20/mo for Prisma Cloud optional)

**Installation:**
```bash
npm install prisma @prisma/client
npx prisma init
```

**Schema:**
```prisma
// prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id        String   @id @default(cuid())
  email     String   @unique
  createdAt DateTime @default(now())
  ebooks    Ebook[]
}

model Ebook {
  id          String   @id @default(cuid())
  title       String
  topic       String
  content     String   @db.Text
  formats     Json     // { pdf: string, epub: string, mobi: string, word: string }
  metadata    Json     // { word_count: int, page_count: int, author: string }
  userId      String
  user        User     @relation(fields: [userId], references: [id])
  status      String   @default("generating") // generating, completed, failed
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt

  @@index([userId])
}
```

---

## 🤖️ AI & Content Generation Stack

### OpenAI API (GPT-4)

**Description:** Leading AI model for content generation and quality assurance
**License:** Commercial (API pricing)
**Website:** https://platform.openai.com

**Pricing (2026):**

| Model | Input Cost | Output Cost | Context | Use Case |
|-------|-----------|-------------|---------|-----------|
| GPT-4 Turbo | $10/1M tokens | $30/1M tokens | 128k tokens | Fast generation |
| GPT-4 | $30/1M tokens | $60/1M tokens | 128k tokens | High-quality generation |
| GPT-4o | $5/1M tokens | $15/1M tokens | 128k tokens | Multimodal (text + images) |

**Usage Estimates (50,000-word ebook):**
- Research: ~50,000 tokens (input)
- Outline: ~5,000 tokens (input + output)
- Writing: ~100,000 tokens (input + output)
- Editing: ~30,000 tokens (input + output)
- **Total:** ~185,000 tokens
- **Cost:** ~$6-15 per ebook

**Cost Optimization Strategies:**
1. Use GPT-4 Turbo for initial drafts
2. Use GPT-4 for final editing only
3. Cache common responses
4. Use shorter, more focused prompts
5. Batch requests when possible

**Installation:**
```bash
npm install openai
```

**Configuration:**
```typescript
// lib/openai.ts
import OpenAI from 'openai'

const openai = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY!,
})

export const generateContent = async (prompt: string) => {
  const response = await openai.chat.completions.create({
    model: 'gpt-4-turbo',
    messages: [{ role: 'user', content: prompt }],
    temperature: 0.7,
    max_tokens: 4000,
  })

  return response.choices[0].message.content
}

export const editContent = async (content: string) => {
  const response = await openai.chat.completions.create({
    model: 'gpt-4', // Use GPT-4 for quality
    messages: [{ role: 'user', content: `Edit and improve: ${content}` }],
    temperature: 0.3,
    max_tokens: 4000,
  })

  return response.choices[0].message.content
}
```

### nano-banana-pro (Gemini 3 Pro)

**Description:** AI image generation for ebook covers
**License:** Commercial (API pricing)
**Website:** Via OpenClaw skill

**Pricing:**
- Free tier: Limited images/month
- Pro tier: Enhanced quality and volume

**Usage:**
- 1 cover image per ebook
- Generate 3 variations, select best
- Use AI to create themed, professional covers

---

## 📄 Document Generation Stack

### Puppeteer / Playwright

**Description:** Headless browser for PDF generation with professional rendering
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://playwright.dev

**Key Features:**
- Generate PDF from HTML/CSS
- Control page size and orientation
- Add headers and footers
- Table of contents and bookmarks
- High-quality rendering

**Cost:** $0 (Open Source)

**Installation:**
```bash
npm install puppeteer
# OR
npm install playwright
```

**PDF Generation Code:**
```typescript
// lib/pdf-generator.ts
import puppeteer from 'puppeteer'

export const generatePDF = async (html: string, outputPath: string) => {
  const browser = await puppeteer.launch()
  const page = await browser.newPage()

  await page.setContent(html, { waitUntil: 'networkidle0' })

  await page.pdf({
    path: outputPath,
    format: 'A4',
    printBackground: true,
    margin: {
      top: '1cm',
      right: '1cm',
      bottom: '1cm',
      left: '1cm',
    },
    displayHeaderFooter: true,
  })

  await browser.close()
}
```

### Pandoc

**Description:** Universal document converter for EPUB and other formats
**License:** GPL (Free and Open Source)
**Website:** https://pandoc.org

**Key Features:**
- Convert between formats (Markdown → EPUB)
- Support for multiple output formats
- Table of contents generation
- Metadata preservation

**Installation:**
```bash
# Install Pandoc
# Windows: Download installer from pandoc.org
# macOS: brew install pandoc
# Linux: sudo apt-get install pandoc

npm install pandoc
```

**EPUB Generation Code:**
```typescript
// lib/epub-generator.ts
import { exec } from 'child_process'

export const generateEPUB = async (markdown: string, outputPath: string) => {
  return new Promise((resolve, reject) => {
    exec(
      `pandoc -f markdown -t epub3 -o ${outputPath} -`,
      (error, stdout, stderr) => {
        if (error) {
          reject(error)
        } else {
          resolve(outputPath)
        }
      }
    )
  })
}
```

### KindleGen

**Description:** Kindle format (.mobi) generator for e-readers
**License:** MIT (Free and Open Source)
**Website:** https://github.com/kevingillette/KindleGen

**Key Features:**
- Generate .mobi files from HTML
- Add table of contents
- Support for images
- Kindle-compatible formatting

**Installation:**
```bash
npm install kindlegen
```

**MOBI Generation Code:**
```typescript
// lib/mobi-generator.ts
import { exec } from 'child_process'

export const generateMOBI = async (html: string, outputPath: string) => {
  return new Promise((resolve, reject) => {
    exec(
      `kindlegen ${outputPath}`,
      { encoding: 'utf8' },
      (error, stdout, stderr) => {
        if (error) {
          reject(error)
        } else {
          resolve(outputPath)
        }
      }
    )
  })
}
```

### docx

**Description:** Generate .docx (Word) files for editing
**License:** MIT (Free and Open Source)
**Website:** https://github.com/dolanmiu/docx

**Key Features:**
- Create editable Word documents
- Support for formatting (bold, italic, headers)
- Add tables and lists
- Preserve metadata

**Installation:**
```bash
npm install docx
```

**Word Export Code:**
```typescript
// lib/word-generator.ts
import { Document, Packer, Paragraph, TextRun, HeadingLevel } from 'docx'

export const generateWord = async (title: string, chapters: string[]) => {
  const doc = new Document({
    sections: [
      {
        properties: {},
        children: chapters.map(chapter => new Paragraph({
          text: chapter,
          heading: HeadingLevel.HEADING_1,
        })),
      },
    ],
  })

  const buffer = await Packer.toBuffer(doc)

  return buffer
}
```

---

## 🌐 Web Scraping & Research Stack

### Puppeteer

**Description:** Headless Chrome browser for web scraping and content extraction
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://pptr.dev

**Key Features:**
- Render JavaScript-heavy sites
- Navigate pages programmatically
- Extract content and data
- Handle dynamic content

**Cost:** $0 (Open Source)

**Scraping Code:**
```typescript
// lib/scraper.ts
import puppeteer from 'puppeteer'

export const scrapeContent = async (url: string) => {
  const browser = await puppeteer.launch()
  const page = await browser.newPage()

  await page.goto(url, { waitUntil: 'networkidle0' })

  const content = await page.evaluate(() => {
    return {
      title: document.title,
      text: document.body.innerText,
      html: document.body.innerHTML,
    }
  })

  await browser.close()

  return content
}
```

### Brave Search API

**Description:** Web search API for research and content discovery
**License:** Commercial (API pricing)
**Website:** https://brave.com/search/api

**Pricing:**
- Free tier: 2,000 requests/month
- Pro tier: $25/month for 10,000 requests/month

**Usage Estimates:**
- 20 searches per ebook generation
- 50 sources to validate
- ~70 searches/month per active user

**Installation:**
```bash
npm install brave-search
```

**Configuration:**
```typescript
// lib/brave-search.ts
const BRAVE_API_KEY = process.env.BRAVE_API_KEY!

export const searchBrave = async (query: string) => {
  const response = await fetch(
    `https://api.search.brave.com/res/v1/web/search?q=${encodeURIComponent(query)}&count=10`,
    {
      headers: {
        'Accept': 'application/json',
        'X-Subscription-Token': BRAVE_API_KEY,
      },
    }
  )

  const data = await response.json()

  return data.web.results
}
```

### Playwright (Web Fetch)

**Description:** Modern browser automation for web content fetching
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://playwright.dev

**Key Features:**
- Multi-browser support (Chromium, Firefox, WebKit)
- Network interception and mocking
- Fast, reliable, headless execution
- Mobile device emulation

**Web Fetch Code:**
```typescript
// lib/web-fetch.ts
import { chromium } from 'playwright'

export const fetchWebContent = async (url: string) => {
  const browser = await chromium.launch()
  const page = await browser.newPage()

  await page.goto(url)
  const content = await page.content()

  await browser.close()

  return content
}
```

---

## 🔐 Authentication & Security Stack

### Supabase Auth

**Description:** Authentication and user management system
**License:** Apache 2.0 (Free via Supabase)
**Website:** https://supabase.com/docs/guides/auth

**Features:**
- Email/password authentication
- Social login (Google, GitHub)
- Password reset
- Email verification
- Session management
- Row-level security (RLS)

**Auth Code:**
```typescript
// app/api/auth/[...nextauth]/route.ts
import { createRouteHandlerClient } from '@supabase/auth-helpers-nextjs'
import { cookies } from 'next/headers'
import { createClient } from '@supabase/supabase-js'

export async function POST(req: Request) {
  const supabase = createClient(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
    {
      cookies: {
        getAll() { return cookies() },
      },
    },
  )

  const { data, error } = await supabase.auth.signInWithPassword({
    email,
    password,
  })

  return Response.json({ data, error })
}
```

### Row-Level Security (RLS)

**Description:** Database-level security policies to ensure users can only access their own data
**License:** Apache 2.0 (Free via Supabase)

**Policies:**
```sql
-- RLS Policies
-- Ensure users can only access their own ebooks

-- Users can only create their own ebooks
CREATE POLICY "Users can create their own ebooks"
  ON ebooks FOR INSERT
  WITH CHECK (auth.uid() = user_id);

-- Users can only view their own ebooks
CREATE POLICY "Users can view their own ebooks"
  ON ebooks FOR SELECT
  USING (auth.uid() = user_id);

-- Users can only update their own ebooks
CREATE POLICY "Users can update their own ebooks"
  ON ebooks FOR UPDATE
  USING (auth.uid() = user_id);

-- Users can only delete their own ebooks
CREATE POLICY "Users can delete their own ebooks"
  ON ebooks FOR DELETE
  USING (auth.uid() = user_id);

-- Enable RLS
ALTER TABLE ebooks ENABLE ROW LEVEL SECURITY;
```

---

## 📁 File Storage & Delivery Stack

### Supabase Storage

**Description:** Object storage for ebook files and user uploads
**License:** Apache 2.0 (Free via Supabase)
**Website:** https://supabase.com/docs/guides/storage

**Free Tier Limits:**
- 1GB storage
- 2GB bandwidth/month
- Unlimited public buckets

**Storage Code:**
```typescript
// lib/storage.ts
import { createClient } from '@supabase/supabase-js'

const supabase = createClient(
  process.env.NEXT_PUBLIC_SUPABASE_URL!,
  process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
)

export const uploadEbook = async (file: File, userId: string) => {
  const fileName = `${userId}/${Date.now()}-${file.name}`

  const { data, error } = await supabase.storage
    .from('ebooks')
    .upload(fileName, file, {
      cacheControl: '3600',
      upsert: false,
    })

  return { data, error }
}

export const getEbookURL = async (fileName: string) => {
  const { data } = supabase.storage
    .from('ebooks')
    .getPublicUrl(fileName)

  return data?.publicUrl
}
```

### GitHub API

**Description:** Save ebooks to GitHub repositories
**License:** MIT (API usage, free for public repos)
**Website:** https://docs.github.com/rest

**Free Tier:**
- Unlimited public repositories
- 500MB per file limit
- 100MB recommended for releases
- Rate limits: 5,000 requests/hour

**GitHub Integration Code:**
```typescript
// lib/github.ts
import Octokit from 'octokit'

const octokit = new Octokit({
  auth: process.env.GITHUB_TOKEN!,
})

export const createGitHubRepo = async (userId: string, ebookTitle: string) => {
  const repoName = `ebook-${userId}-${Date.now()}`

  const { data } = await octokit.rest.repos.createForAuthenticatedUser({
    name: repoName,
    description: `Ebook: ${ebookTitle}`,
    auto_init: false,
    private: false, // Can be true for premium users
  })

  return data
}

export const uploadEbookFiles = async (owner: string, repo: string, files: any[]) => {
  for (const file of files) {
    await octokit.rest.repos.createOrUpdateFileContents({
      owner,
      repo,
      path: file.name,
      message: `Add ${file.name}`,
      content: Buffer.from(file.content).toString('base64'),
    })
  }
}
```

### Google Drive API

**Description:** Save ebooks to Google Drive folders
**License:** Commercial (API pricing)
**Website:** https://developers.google.com/drive

**Pricing:**
- Free tier: 15GB storage
- Paid tiers: $1.99/100GB, $9.99/2TB

**Google Drive Integration Code:**
```typescript
// lib/google-drive.ts
import { google } from 'googleapis'

const drive = google.drive({ version: 'v3', auth })

export const createDriveFolder = async (userId: string) => {
  const folderMetadata = {
    name: `Ebooks-${userId}`,
    mimeType: 'application/vnd.google-apps.folder',
  }

  const { data } = await drive.files.create({
    resource: folderMetadata,
  })

  return data
}

export const uploadEbookToDrive = async (folderId: string, file: File) => {
  const fileMetadata = {
    name: file.name,
    parents: [folderId],
  }

  const media = {
    mimeType: file.type,
    body: file.stream(),
  }

  const { data } = await drive.files.create({
    resource: fileMetadata,
    media,
    fields: 'id',
  })

  return data
}
```

---

## 🧪 Testing Stack

### Playwright

**Description:** Modern end-to-end testing framework
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://playwright.dev

**Key Features:**
- Multi-browser support
- Fast execution
- Auto-waiting
- Network interception
- Mobile device emulation

**Cost:** $0 (Open Source)

**Installation:**
```bash
npm install -D @playwright/test
npx playwright install
```

**Test Example:**
```typescript
// tests/ebook-generation.spec.ts
import { test, expect } from '@playwright/test'

test('should generate complete ebook', async ({ page }) => {
  await page.goto('http://localhost:3000/generate')

  await page.fill('input[name="topic"]', 'Quantum Machine Learning')
  await page.click('button[type="submit"]')

  // Wait for generation
  await page.waitForSelector('[data-testid="ebook-complete"]', { timeout: 120000 })

  // Verify formats available
  await expect(page.locator('[data-testid="download-pdf"]')).toBeVisible()
  await expect(page.locator('[data-testid="download-epub"]')).toBeVisible()
  await expect(page.locator('[data-testid="download-mobi"]')).toBeVisible()
})
```

### Vitest

**Description:** Fast unit testing framework
**License:** MIT (Free and Open Source)
**Website:** https://vitest.dev

**Key Features:**
- Fast execution
- Native ES modules support
- TypeScript support
- Mock functions

**Cost:** $0 (Open Source)

**Unit Test Example:**
```typescript
// tests/agent/research-agent.test.ts
import { describe, it, expect } from 'vitest'
import { ResearchAgent } from '@/agents/research-agent'

describe('ResearchAgent', () => {
  it('should validate sources', async () => {
    const agent = new ResearchAgent()
    const sources = await agent.gatherSources('Quantum ML')

    expect(sources).toBeDefined()
    expect(sources.length).toBeGreaterThanOrEqual(5)
  })
})
```

---

## 🚀 CI/CD Stack

### GitHub Actions

**Description:** Automated deployment and testing on GitHub
**License:** MIT (Free for public repos, 2,000 free minutes/month for private)
**Website:** https://github.com/features/actions

**Free Tier (Public Repos):**
- Unlimited minutes
- Unlimited parallel jobs
- Free artifacts storage (500MB, 90-day retention)

**Workflow File:**
```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '22'

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Build
        run: npm run build

      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v20
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.ORG_ID }}
          vercel-project-id: ${{ secrets.PROJECT_ID }}
```

---

## 📊 Monitoring & Observability Stack

### OpenTelemetry

**Description:** Observability framework for metrics, logs, and traces
**License:** Apache 2.0 (Free and Open Source)
**Website:** https://opentelemetry.io

**Key Features:**
- Metrics collection
- Distributed tracing
- Log aggregation
- Vendor-agnostic

**Cost:** $0 (Open Source, paid backends optional)

**Integration:**
```typescript
// lib/telemetry.ts
import { trace, Span } from '@opentelemetry/api'

export const trackAgentExecution = (agentName: string, duration: number) => {
  const tracer = trace.getTracer('ebook-generator')

  const span = tracer.startSpan('agent_execution')

  span.setAttributes({
    'agent.name': agentName,
    'execution.duration_ms': duration,
    'success': true,
  })

  span.end()
}
```

---

## 💰 Cost Summary

### Open Source Tools (FREE)
| Category | Tool | Monthly Cost |
|----------|------|-------------|
| Frontend | Next.js, TypeScript, shadcn/ui, Tailwind | $0 |
| Backend | Node.js, Prisma | $0 |
| Database | Supabase (free tier) | $0 |
| Auth | Supabase Auth (free) | $0 |
| Storage | Supabase Storage (1GB) | $0 |
| PDF Generation | Puppeteer | $0 |
| EPUB/MOBI | Pandoc, KindleGen | $0 |
| Word Export | docx | $0 |
| Scraping | Puppeteer, Playwright | $0 |
| Testing | Playwright, Vitest | $0 |
| CI/CD | GitHub Actions | $0 |
| **Total Open Source** | **ALL** | **$0/month** |

### Paid Services (MINIMAL)
| Service | Tier | Monthly Cost | Usage Limit |
|---------|------|-------------|-------------|
| OpenAI API | GPT-4 Turbo | $10-30/mo | 1M tokens |
| Brave Search | Free | $0 | 2,000 requests/mo |
| Google Drive | Free | $0 | 15GB storage |
| GitHub API | Free | $0 | 500MB files |
| Cover Images | nano-banana-pro | TBD | TBD |
| **Total Paid** | **MINIMAL** | **$10-30/month** |

### Scalability Options (When Needed)
| Service | Upgrade | Monthly Cost | When to Upgrade |
|---------|---------|-------------|----------------|
| Supabase Pro | $25/mo | When DB > 500MB |
| Vercel Pro | $20/mo | When traffic > 100GB/mo |
| Cloudflare CDN | $5/mo | When global distribution needed |
| **When to Scale** | - | - | When paying > 100 customers |

---

## ✅ Setup Checklist

### Development Environment

- [ ] Install Node.js 22+
- [ ] Install TypeScript 5.4+
- [ ] Install Next.js 15+
- [ ] Install Tailwind CSS 4+
- [ ] Install shadcn/ui
- [ ] Install Prisma 5.5+
- [ ] Install Supabase CLI
- [ ] Install Puppeteer
- [ ] Install Pandoc
- [ ] Install KindleGen
- [ ] Install docx
- [ ] Install Playwright
- [ ] Install Vitest
- [ ] Configure GitHub Actions
- [ ] Set up OpenAI API key
- [ ] Set up Brave Search API key
- [ ] Set up Google Drive credentials
- [ ] Set up GitHub token

### Local Deployment

- [ ] Set environment variables (.env.local)
- [ ] Configure Supabase project
- [ ] Set up PostgreSQL database locally
- [ ] Configure authentication providers
- [ ] Set up storage buckets
- [ ] Test all API routes locally
- [ ] Run full e2e tests
- [ ] Verify all formats (PDF, EPUB, MOBI, Word)
- [ ] Test delivery integrations (GitHub, Drive)

### Production Deployment (When Ready)

- [ ] Deploy to Vercel (free tier)
- [ ] Configure custom domain
- [ ] Set up monitoring
- [ ] Enable error tracking
- [ ] Configure CDN (if needed)
- [ ] Set up rate limiting
- [ ] Enable caching
- [ ] Configure backup strategy

---

## 🎯 Development Workflow

1. **Local Development**
   - Run Next.js dev server locally
   - Use local PostgreSQL or Supabase
   - Test all features locally first

2. **Automated Testing**
   - Run unit tests on every save
   - Run e2e tests before commits
   - GitHub Actions run on every push

3. **Staging Deployment**
   - Deploy to Vercel preview URL
   - Test with beta users
   - Monitor logs and metrics

4. **Production Deployment**
   - Merge to main branch
   - Automatic deploy via GitHub Actions
   - Monitor and respond to issues

---

## 📝 Notes

**Key Principles:**
- **Open Source First:** All tools are free and open source
- **Local Development:** Everything runs locally first
- **Minimal Cloud Spend:** Only pay for what's needed (OpenAI API)
- **Scalable Architecture:** Design for easy cloud migration when needed
- **Self-Host Options:** Supabase provides free auth, database, storage

**Cost Optimization:**
- Use Supabase free tier (500MB DB, 1GB storage)
- Use OpenAI GPT-4 Turbo (faster, cheaper than GPT-4)
- Use GitHub Actions free tier (unlimited for public repos)
- Self-host as much as possible before scaling

**Deployment Options:**
1. **Local Only:** Complete local development and testing
2. **Vercel Free:** Frontend deployment with global CDN
3. **Supabase Free:** Backend, database, auth, storage
4. **Optional Scale:** Upgrade to paid tiers only when needed

---

**Last Updated:** 2026-02-18
**Next Review:** Before starting development (Task T1.1 in roadmap)

---

*All open source tools cataloged. Minimum spend. Maximum capability.*
