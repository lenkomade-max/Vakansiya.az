# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Vakansiya.AZ** is a modern job search and vacancy posting platform for Azerbaijan. This repository contains comprehensive planning, architecture, and functional specifications in Russian. The actual codebase is in the `/code` directory.

**Key characteristics:**
- Target market: Azerbaijan job market
- User interface language: Azerbaijani
- Documentation language: Russian
- Target audience: Job seekers and employers (many with low computer literacy)
- Planned domain: vakansiya.az

## Directory Structure

```
/docs        - Core project documentation (architecture, tech stack, etc.)
/design-refs - Initial drafts and primary notes
/rules       - Project-wide rules and guidelines
/code        - Code repository (synced to GitHub)
/journal     - Task completion reports (for AI agents)
/trash       - Temporary files, drafts, and artifacts (never commit to GitHub)
```

## Important Rules

1. **Code Organization**: All code MUST go in `/code` directory only. This directory is for GitHub synchronization.
2. **Keep Root Clean**: Never create temporary/test files in root or `/code`. Use `/trash` for temporary work.
3. **Task Journaling**: After completing significant tasks, create a brief report in `/journal` with filename format: `YYYY-MM-DD_Task_Description.md`
4. **Code Quality**: Code in `/code` must always be in working condition.

## Technology Stack

### Frontend
- **Next.js 15** with App Router
- **React 18+** (Server Components + Client Components)
- **TypeScript** (strict mode)
- **Tailwind CSS** for styling
- **shadcn/ui** (optional) - accessible UI components

### Backend & Database
- **Supabase** (Backend-as-a-Service)
  - PostgreSQL 15+ database
  - Authentication (Google OAuth)
  - Storage for logos/images
  - Edge Functions
  - Row Level Security (RLS)

### Deployment & Hosting
- **Vercel** - Frontend hosting, automatic deploys from GitHub
- **GitHub** - Version control and CI/CD

### Email Marketing
- **Brevo (SendinBlue)** - Transactional and marketing emails
- Alternatives: Mailerlite, ConvertKit, Resend

### AI & Scraping
- **OpenRouter** - Gateway to 300+ AI models for data standardization
  - Primary: DeepSeek Chat v3 (free tier: 50 requests/day)
  - Backup: Google Gemini 2.0 Flash
- **Playwright** - Browser automation for scraping dynamic content
- **Cheerio** - Fast HTML parsing for static content
- **Axios** - HTTP requests

### Package Manager
- **npm** or **pnpm** preferred

## Architecture

**Serverless architecture** based on JAMstack approach:

1. **Presentation Layer**: Next.js app with SSR/SSG/ISR/CSR
2. **Business Logic Layer**: Supabase + Next.js API Routes
3. **Data Layer**: PostgreSQL via Supabase

**Key patterns:**
- Server-Side Rendering (SSR) for SEO-critical pages
- Static Site Generation (SSG) for static content
- Incremental Static Regeneration (ISR) for vacancy pages
- Client-Side Rendering (CSR) for interactive elements

## Database Schema

**Main tables:**
- `users` - User accounts (Google OAuth)
- `companies` - Employer companies
- `vacancies` - Permanent job listings
- `short_jobs` - Short-term gigs (Gündəlik işlər)
- `short_job_responses` - Responses to short-term jobs
- `payments` - Payment transactions (manual processing via agent)
- `user_activity` - User activity tracking
- `email_marketing` - Email subscription management

**Authentication:**
- Google OAuth only via Supabase Auth
- JWT tokens with RLS policies
- Role-based access: 'user', 'employer', 'admin'

## Key Features & Modules

### 1. Authentication
- Google OAuth login only
- Session management with JWT
- Role-based authorization
- Protected routes with middleware

### 2. Vacancies (Permanent Jobs)
- Full-text search with PostgreSQL
- Multi-filter system (city, category, salary, date)
- Contact details visible only to authenticated users
- Free posting limit: 1/month per employer
- Paid premium positioning

### 3. Short-term Jobs (Gündəlik işlər)
- Simplified posting for gigs/freelance work
- Direct response system
- Lower barrier for employers

### 4. Payment System
- Manual payment processing via agent (initial version)
- Future: Stripe, PayPal, local providers (Portmanat, eManat, Payriff)

### 5. Email Marketing
- Automated job alerts based on user preferences
- Transactional emails (confirmations, notifications)
- Unsubscribe management

### 6. Auto-parsing System
- Separate Node.js microservice scrapes competitor sites (Boss.az, Tap.az, etc.)
- Posts to `/api/import-jobs` endpoint
- AI standardization via OpenRouter (DeepSeek/Gemini)
- Duplicate detection
- Runs hourly via cron

## Development Commands

**Note:** The codebase is in `/code`, typical commands are:

```bash
# Install dependencies
npm install

# Development server
npm run dev

# Type checking
npm run type-check

# Linting
npm run lint

# Build for production
npm run build

# Start production server
npm start

# Run tests (when implemented)
npm test
```

## Environment Variables

Required for Vercel deployment:

```bash
# Supabase
NEXT_PUBLIC_SUPABASE_URL=https://xxxxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJxxx...
SUPABASE_SERVICE_ROLE_KEY=eyJxxx... # Keep secret!

# Google OAuth (configured in Supabase)
# Redirect URI: https://xxxxx.supabase.co/auth/v1/callback

# OpenRouter (for AI standardization)
OPENROUTER_API_KEY=sk-or-xxx

# Email (Brevo/SendinBlue)
BREVO_API_KEY=xkeysib-xxx

# App config
NEXT_PUBLIC_SITE_URL=https://vakansiya.az
```

## Code Style & Quality

- **ESLint** for linting
- **Prettier** for code formatting
- **Husky** for pre-commit hooks
- **lint-staged** for checking only changed files
- TypeScript strict mode enabled

## File Structure

Current structure in `/code`:

```
/code
├── app/                # Next.js App Router pages
│   ├── (auth)/        # Auth routes
│   ├── (main)/        # Main app routes
│   ├── api/           # API routes
│   └── layout.tsx
├── components/         # React components
│   ├── ui/            # shadcn/ui components
│   ├── forms/         # Form components
│   └── shared/        # Shared components
├── lib/               # Utilities and helpers
│   ├── supabase/      # Supabase client
│   ├── ai/            # AI standardization
│   └── utils/         # General utilities
├── types/             # TypeScript types
├── public/            # Static assets
├── styles/            # Global styles
└── config/            # Configuration files
```

## API Endpoints (Planned)

All API routes will be in `app/api/`:

- `/api/vakansiyalar/*` - Vacancy operations (CRUD)
- `/api/short-jobs/*` - Short-term job operations
- `/api/payments/*` - Payment processing
- `/api/auth/*` - Additional auth logic
- `/api/email/*` - Email operations
- `/api/import-jobs` - Auto-parsing webhook endpoint

## Security Considerations

- Row Level Security (RLS) enabled on all Supabase tables
- Google OAuth only (no password storage)
- Contact details hidden from non-authenticated users
- CSRF protection via Next.js middleware
- Rate limiting for API routes (consider Upstash Redis)
- Environment variables never in code
- CORS configuration via middleware

## SEO & Performance

- Server-Side Rendering for job listings
- next-seo for meta tags and Open Graph
- Automatic image optimization with Next.js Image
- Sitemap generation
- Google Search Console integration
- Vercel Analytics for Core Web Vitals

## Auto-parsing Implementation Notes

When implementing the scraper microservice:

1. Create separate Node.js project (outside Next.js)
2. Use Playwright for JavaScript-heavy sites
3. Use Cheerio for simple HTML pages
4. Implement retry logic and error handling
5. Use node-cron for scheduling (every hour)
6. Send POST to `/api/import-jobs` with standardized format
7. AI standardization removes emojis, extracts structured data, normalizes categories
8. Check duplicates by URL or title+company hash

## Localization

- UI entirely in Azerbaijani language
- Navigation, buttons, forms, messages all in Azerbaijani
- Documentation in Russian
- Support for Azerbaijani-specific formatting (dates, currency AZN)

## Business Model

1. Free tier: 1 vacancy/month per employer
2. Paid positioning: Premium placement, extended duration
3. Future: Company subscriptions, additional services

## Accessibility

- Large, easy-to-tap buttons (mobile-first)
- High contrast text
- Simple navigation for low computer literacy users
- Sufficient spacing between interactive elements
- Modern minimalist design

## Future Considerations

- PWA functionality with next-pwa
- Internationalization with next-intl (Russian, English)
- Advanced state management (Zustand, React Query)
- Prisma ORM for type-safe queries
- Zod for schema validation
- React Hook Form for form management
- E2E testing with Playwright
- Unit testing with Vitest

## Key Documentation References

Detailed documentation in `/docs`:
- `README.md` - Project overview
- `АРХИТЕКТУРА.md` - System architecture
- `ТЕХНИЧЕСКИЙ_СТЕК.md` - Complete tech stack details
- `БАЗА_ДАННЫХ.md` - Database schema and relationships
- `API_ДОКУМЕНТАЦИЯ.md` - API endpoint specifications
- `ФУНКЦИОНАЛЬНЫЕ_МОДУЛИ.md` - Functional module details
- `ДИЗАЙН_СИСТЕМА.md` - UI/UX guidelines
- `РАЗВЕРТЫВАНИЕ.md` - Deployment instructions
- `ROADMAP.md` - Project roadmap
- `АВТОПАРСИНГ.md` - Auto-parsing system design
- `AI_ИНТЕГРАЦИЯ.md` - AI integration details

## Contact & Support

This is a commercial project for the Azerbaijan market. Refer to documentation files for detailed specifications before implementation.
