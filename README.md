# Vakansiya.az - Job Portal for Azerbaijan

> Modern job search platform built with Next.js 15, TypeScript, and Tailwind CSS

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/lenkomade-max/Vakansiya.az)

## 🚀 Quick Start

### For Vercel Deployment

**IMPORTANT:** Set Root Directory to `Vakansiya.az/code` in Vercel project settings!

```
Project Settings → General → Root Directory: Vakansiya.az/code
```

Configuration:
- **Framework Preset:** Next.js (auto-detected)
- **Root Directory:** `Vakansiya.az/code`
- **Build Command:** `npm run build` (auto)
- **Output Directory:** `.next` (auto)
- **Install Command:** `npm install` (auto)

### Local Development

```bash
cd code
npm install
npm run dev
# Open http://localhost:3000
```

## 📁 Project Structure

```
/
├── code/                   # Next.js application (ROOT FOR VERCEL!)
│   ├── app/                # Next.js App Router
│   ├── components/         # React components
│   ├── styles/             # Global styles
│   └── package.json        # Dependencies
├── docs/                   # Full documentation
├── design-refs/            # Design references
├── journal/                # Task reports
└── rules/                  # Project rules
```

## 🎨 Features

- ✅ Next.js 15 with App Router
- ✅ TypeScript & Tailwind CSS
- ✅ Modern white design with colored accents (90-10 rule)
- ✅ Responsive UI components
- ✅ Azerbaijani language interface
- ✅ Job cards (regular + Featured/Premium with gradients)
- ✅ Search with quick filters
- ✅ Mobile-first design

## 🌐 Live Demo

Once deployed on Vercel: `https://vakansiya-az.vercel.app`

## 📚 Documentation

Full documentation in `/docs/`:
- `ДИЗАЙН_СИСТЕМА.md` - Design system V2
- `АРХИТЕКТУРА.md` - Architecture
- `БАЗА_ДАННЫХ.md` - Database schema
- `API_ДОКУМЕНТАЦИЯ.md` - API docs
- `РАЗВЕРТЫВАНИЕ.md` - Deployment guide

## 🛠 Tech Stack

- **Next.js 15** - React framework
- **TypeScript** - Type safety
- **Tailwind CSS** - Styling
- **Supabase** (planned) - Backend
- **Vercel** - Hosting

## 🚀 Vercel Deployment Instructions

### Option 1: Import from GitHub

1. Go to [vercel.com/new](https://vercel.com/new)
2. Import `lenkomade-max/Vakansiya.az`
3. **Configure Root Directory:**
   ```
   Root Directory: Код
   ```
4. **Framework Preset:** Next.js (auto-detected)
5. Click **Deploy**

### Option 2: Vercel CLI

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy from code directory
cd code
vercel

# Or deploy from root with config
vercel --cwd code
```

### Option 3: Deploy Button

Click the button at the top of this README!

## 🔧 Environment Variables

Create `.env.local` in `/code/`:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
NEXT_PUBLIC_SITE_URL=https://vakansiya.az
```

## 📦 Build Commands

```bash
# Development
npm run dev

# Production build
npm run build

# Start production server
npm start

# Type checking
npm run type-check

# Linting
npm run lint
```

## 🎯 Pages

- `/` - Home page with job listings
- `/jobs` - All jobs (planned)
- `/companies` - Companies (planned)
- `/short-jobs` - Short-term jobs (planned)

## 🎨 Design System

- **90% neutral colors** (white, black, gray)
- **10% colored accents** (blue, green, yellow, red, purple)
- **Inter font** for typography
- **Gradient cards** for Premium jobs by category
- **Mobile-first** responsive design

## 📄 License

Commercial project © 2025 Vakansiya.az

---

Built with ❤️ for Azerbaijan job market

## 🐛 Troubleshooting

### 404 Error on Vercel?

Make sure Root Directory is set to `code`:
1. Go to Project Settings
2. General → Root Directory
3. Enter: `code`
4. Redeploy

### Build Fails?

Check:
- Node version: v18+ required
- All dependencies installed: `npm install`
- TypeScript compiles: `npm run type-check`
- Build works locally: `npm run build`
