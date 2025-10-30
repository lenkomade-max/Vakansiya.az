# Vakansiya.az - Job Portal for Azerbaijan

> Modern job search platform built with Next.js 15, TypeScript, and Tailwind CSS

## 🚀 Quick Start

### Installation

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Open http://localhost:3000
```

### Build for production

```bash
# Create production build
npm run build

# Start production server
npm start
```

## 📁 Project Structure

```
/Код
├── app/                    # Next.js App Router
│   ├── layout.tsx         # Root layout
│   └── page.tsx           # Home page
├── components/
│   ├── ui/                # Base UI components
│   │   ├── Button.tsx
│   │   ├── SearchBar.tsx
│   │   └── Navigation.tsx
│   └── job/               # Job-related components
│       ├── JobCard.tsx
│       └── JobCardFeatured.tsx
├── styles/
│   └── globals.css        # Global styles + Tailwind
├── public/                # Static assets
├── tailwind.config.js     # Tailwind configuration
└── next.config.js         # Next.js configuration
```

## 🎨 Design System

- **White background** (90%) + **colored accents** (10%)
- **Inter font** for modern typography
- **Black text** for maximum readability
- **Colored gradients** for Premium job cards
- **Mobile-first** responsive design

See `/Основные документы/ДИЗАЙН_СИСТЕМА.md` for full specs.

## 🛠 Tech Stack

- **Next.js 15** - React framework with App Router
- **TypeScript** - Type safety
- **Tailwind CSS** - Utility-first styling
- **React 18** - UI library

### Planned Integration

- **Supabase** - Backend (PostgreSQL + Auth + Storage)
- **Vercel** - Deployment & hosting
- **Brevo** - Email marketing
- **OpenRouter** - AI for job standardization

## 🌐 Environment Variables

Copy `.env.example` to `.env.local`:

```bash
cp .env.example .env.local
```

Required variables:
```env
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
OPENROUTER_API_KEY=
BREVO_API_KEY=
NEXT_PUBLIC_SITE_URL=
```

## 📦 Available Scripts

```bash
npm run dev         # Start development server
npm run build       # Build for production
npm start           # Start production server
npm run lint        # Run ESLint
npm run type-check  # Run TypeScript type checking
```

## 🎯 Features

### Current (MVP)

- ✅ Modern UI with design system
- ✅ Job cards (regular + Featured/Premium)
- ✅ Search bar with quick filters
- ✅ Responsive navigation
- ✅ Mobile-first design
- ✅ Azerbaijani language UI

### Planned

- [ ] Supabase authentication (Google OAuth)
- [ ] Job listings CRUD
- [ ] Advanced search & filters
- [ ] User profiles
- [ ] Employer dashboard
- [ ] Payment processing
- [ ] Email notifications
- [ ] Auto-parsing from competitors

## 🚀 Deploy to Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/lenkomade-max/Vakansiya.az)

### Manual Deployment

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Deploy to production
vercel --prod
```

### Environment Variables (Vercel)

Add these in Vercel dashboard:
- `NEXT_PUBLIC_SUPABASE_URL`
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`
- `SUPABASE_SERVICE_ROLE_KEY`
- `OPENROUTER_API_KEY`
- `BREVO_API_KEY`
- `NEXT_PUBLIC_SITE_URL`

## 📐 Components Usage

### Button

```tsx
import { Button } from '@/components/ui/Button'

<Button variant="primary" onClick={handleClick}>
  Axtar
</Button>
```

### JobCard

```tsx
import { JobCard } from '@/components/job/JobCard'

<JobCard
  title="Frontend Developer"
  company="ABC Tech"
  location="Bakı"
  salary="1500-2000 AZN"
  category="it"
  tags={['React', 'TypeScript']}
  onApply={handleApply}
/>
```

### JobCardFeatured

```tsx
import { JobCardFeatured } from '@/components/job/JobCardFeatured'

<JobCardFeatured
  title="Senior Developer"
  company="Google"
  location="Bakı"
  salary="$5,000"
  category="it"  // determines gradient color
  isPremium={true}
  onApply={handleApply}
/>
```

## 🎨 Customization

### Colors

Edit `tailwind.config.js`:

```js
colors: {
  accent: {
    primary: '#3B82F6', // Change primary color
  },
}
```

### Typography

```js
fontFamily: {
  sans: ['Your Font', 'sans-serif'],
}
```

## 📚 Documentation

- **Design System:** `/Основные документы/ДИЗАЙН_СИСТЕМА.md`
- **Architecture:** `/Основные документы/АРХИТЕКТУРА.md`
- **Database:** `/Основные документы/БАЗА_ДАННЫХ.md`
- **API Docs:** `/Основные документы/API_ДОКУМЕНТАЦИЯ.md`

## 🐛 Issues & Contributing

Report issues: [GitHub Issues](https://github.com/lenkomade-max/Vakansiya.az/issues)

## 📄 License

Commercial project © 2025 Vakansiya.az

---

Built with ❤️ for Azerbaijan job market
