# Vakansiya.az - UI Components

> Современные UI компоненты на базе **Tailwind CSS** с дизайн-системой V2

## 🎨 Дизайн-система

- **Белый фон** - основа для чистоты и минимализма
- **Черный текст** - максимальная читаемость
- **Цветные акценты (10%)** - для важных элементов (кнопки, теги, статусы)
- **Inter/SF Pro** - современная типографика
- **Mobile-first** - адаптивный дизайн для всех устройств

## 📁 Структура проекта

```
/Код
├── components/
│   ├── ui/              # Базовые UI компоненты
│   │   ├── Button.tsx
│   │   ├── SearchBar.tsx
│   │   └── Navigation.tsx
│   ├── job/             # Компоненты вакансий
│   │   ├── JobCard.tsx
│   │   └── JobCardFeatured.tsx
│   └── examples/        # Примеры использования
│       └── HomePage.tsx
├── styles/
│   └── globals.css      # Глобальные стили + Tailwind
├── lib/                 # Утилиты
└── tailwind.config.js   # Конфигурация Tailwind
```

## 🚀 Установка

```bash
# 1. Установите зависимости
npm install

# 2. Установите Tailwind CSS
npm install -D tailwindcss postcss autoprefixer

# 3. Установите дополнительные плагины
npm install tailwindcss-animate

# 4. Инициализируйте Tailwind (если нужно)
npx tailwindcss init -p
```

## 📦 Компоненты

### 1. Button

Универсальная кнопка с 3 вариантами.

```tsx
import { Button } from '@/components/ui/Button';

// Primary (черная)
<Button variant="primary" onClick={handleClick}>
  Axtar
</Button>

// Secondary (белая с обводкой)
<Button variant="secondary">
  Yadda saxla
</Button>

// Accent (синяя для CTA)
<Button variant="accent" size="lg">
  Müraciət et →
</Button>
```

**Props:**
- `variant`: 'primary' | 'secondary' | 'accent'
- `size`: 'sm' | 'md' | 'lg'
- Все стандартные HTML button props

---

### 2. JobCard

Обычная карточка вакансии (белая с hover-эффектами).

```tsx
import { JobCard } from '@/components/job/JobCard';

<JobCard
  id="1"
  title="Frontend Developer"
  company="ABC Tech"
  location="Bakı"
  salary="1500-2000 AZN"
  postedAt="2 saat əvvəl"
  category="it"
  type="full-time"
  isRemote={true}
  tags={['React', 'TypeScript', 'Tailwind']}
  logo="/logos/abc-tech.png"
  onApply={() => console.log('Apply')}
  onSave={() => console.log('Save')}
  isSaved={false}
/>
```

**Props:**
- `id`: string
- `title`: string
- `company`: string
- `location`: string
- `salary?`: string
- `postedAt`: string
- `logo?`: string
- `tags?`: string[]
- `category?`: 'it' | 'marketing' | 'design' | 'sales' | 'management' | 'other'
- `isRemote?`: boolean
- `type?`: 'full-time' | 'part-time' | 'contract' | 'freelance'
- `onApply?`: () => void
- `onSave?`: () => void
- `isSaved?`: boolean

---

### 3. JobCardFeatured

Цветная Premium карточка с градиентом.

```tsx
import { JobCardFeatured } from '@/components/job/JobCardFeatured';

<JobCardFeatured
  id="f1"
  title="Senior Backend Developer"
  company="Google Azerbaijan"
  location="Bakı"
  salary="$4,000-6,000"
  category="it"  // определяет цвет градиента
  type="full-time"
  isRemote={true}
  tags={['Node.js', 'PostgreSQL', 'AWS']}
  isPremium={true}
  onApply={() => console.log('Apply')}
/>
```

**Цвета по категориям:**
- `it` → Синий градиент
- `marketing` → Красный градиент
- `design` → Фиолетовый градиент
- `sales` → Зеленый градиент
- `management` → Оранжевый градиент

---

### 4. SearchBar

Поисковая форма с фильтрами и быстрыми чипсами.

```tsx
import { SearchBar } from '@/components/ui/SearchBar';

<SearchBar
  onSearch={(query, location, category) => {
    console.log({ query, location, category });
  }}
  placeholder="Vəzifə, açar söz..."
  locationPlaceholder="Şəhər seçin"
/>
```

**Функции:**
- Поле поиска по вакансиям
- Выбор города/локации
- Быстрые фильтры (Tam iş günü, Distant, Yeni)

---

### 5. Navigation

Адаптивная навигация с мобильным меню.

```tsx
import { Navigation } from '@/components/ui/Navigation';

<Navigation
  onLogin={() => console.log('Login')}
  onPostJob={() => console.log('Post Job')}
  isAuthenticated={false}
  userName="Fərid"
  userAvatar="/avatars/user.jpg"
/>
```

**Props:**
- `onLogin?`: () => void
- `onPostJob?`: () => void
- `isAuthenticated?`: boolean
- `userAvatar?`: string
- `userName?`: string

---

## 🎨 Стили и утилиты (globals.css)

### Готовые классы компонентов

```css
/* Кнопки */
.btn-primary     /* Черная кнопка */
.btn-secondary   /* Белая с обводкой */
.btn-accent      /* Синяя CTA */

/* Карточки */
.card-base       /* Белая карточка */
.card-featured   /* Цветная Featured */

/* Инпуты */
.input-base      /* Стандартный input */

/* Теги */
.tag-location    /* Зеленый (город) */
.tag-category    /* Синий (категория) */
.tag-type        /* Фиолетовый (тип работы) */
.tag-status      /* Желтый (статус) */
.tag-premium     /* Оранжевый (Premium) */

/* Контейнеры */
.container-main  /* max-w-7xl mx-auto px-6 */
.stat-card       /* Статистические карточки */

/* Навигация */
.nav-link        /* Обычная ссылка */
.nav-link-active /* Активная ссылка */
```

### Градиенты для Featured карточек

```css
.gradient-it         /* Синий */
.gradient-marketing  /* Красный */
.gradient-design     /* Фиолетовый */
.gradient-sales      /* Зеленый */
.gradient-management /* Оранжевый */
```

---

## 🎯 Пример полной страницы

Смотрите `/components/examples/HomePage.tsx` для полного примера главной страницы со всеми компонентами.

```tsx
import HomePage from '@/components/examples/HomePage';

export default function Home() {
  return <HomePage />;
}
```

Страница включает:
- ✅ Навигацию
- ✅ Hero секцию с поиском
- ✅ Статистику (3 карточки)
- ✅ Premium вакансии (цветные)
- ✅ Обычные вакансии (белые)
- ✅ CTA секцию
- ✅ Footer

---

## 🎨 Цветовая палитра Tailwind

```js
// tailwind.config.js

colors: {
  // Основа
  white: '#FFFFFF',
  black: '#000000',

  // Серые
  gray: {
    50: '#F9FAFB',   // Светлый фон
    100: '#F3F4F6',  // Вторичный фон
    200: '#E5E7EB',  // Границы
    400: '#9CA3AF',  // Placeholder
    700: '#404040',  // Вторичный текст
    900: '#1A1A1A',  // Основной текст
  },

  // Акценты (10% использования)
  accent: {
    primary: '#3B82F6',        // Синий
    success: '#10B981',        // Зеленый
    warning: '#F59E0B',        // Оранжевый
    danger: '#EF4444',         // Красный
    info: '#8B5CF6',           // Фиолетовый
  },
}
```

---

## 📐 Spacing & Typography

### Отступы (по правилу 4px/8px)

```
space-1  →  4px
space-2  →  8px
space-3  →  12px
space-4  →  16px
space-6  →  24px
space-8  →  32px
space-12 →  48px
```

### Размеры шрифтов

```
text-5xl → 48px (Hero)
text-4xl → 36px (H1)
text-3xl → 30px (H2)
text-2xl → 24px (H3)
text-xl  → 20px (H4)
text-lg  → 18px
text-base → 16px (основной)
text-sm  → 14px
text-xs  → 12px (теги)
```

---

## 🔧 Кастомизация

### Изменение цветов акцентов

```js
// tailwind.config.js
accent: {
  primary: '#YOUR_COLOR',  // Измените здесь
}
```

### Изменение шрифта

```js
fontFamily: {
  sans: ['Your Font', 'sans-serif'],
}
```

### Добавление новой категории

```tsx
// В JobCardFeatured.tsx
const categoryGradients = {
  // ...существующие
  newCategory: 'gradient-new',  // Добавьте здесь
};
```

```css
/* В globals.css */
.gradient-new {
  @apply bg-gradient-to-br from-[#COLOR1] to-[#COLOR2];
}
```

---

## 📱 Responsive Design

Все компоненты адаптивные:

```
mobile:  < 640px   (sm)
tablet:  768px     (md)
laptop:  1024px    (lg)
desktop: 1280px    (xl)
```

Пример использования:

```tsx
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
  {/* 1 колонка на mobile, 2 на tablet, 3 на desktop */}
</div>
```

---

## ✨ Анимации

Встроенные анимации:

```css
animate-slide-up   /* Появление снизу */
animate-fade-in    /* Плавное появление */
animate-scale-in   /* Масштабирование */
```

Hover эффекты:

```tsx
hover:shadow-lg        /* Увеличение тени */
hover:-translate-y-1   /* Подъем карточки */
active:scale-95        /* Нажатие кнопки */
```

---

## 🐛 Troubleshooting

### Tailwind классы не применяются

1. Проверьте `content` в `tailwind.config.js`:

```js
content: [
  './pages/**/*.{ts,tsx}',
  './components/**/*.{ts,tsx}',
  './app/**/*.{ts,tsx}',
],
```

2. Перезапустите dev сервер:

```bash
npm run dev
```

### Кастомные цвета не работают

Убедитесь, что `tailwind.config.js` правильно импортирован и `globals.css` подключен в `_app.tsx`:

```tsx
import '@/styles/globals.css';
```

---

## 📚 Дополнительные ресурсы

- **Дизайн-система:** `/Основные документы/ДИЗАЙН_СИСТЕМА_V2.md`
- **Tailwind Docs:** https://tailwindcss.com/docs
- **shadcn/ui:** https://ui.shadcn.com (для расширения компонентов)

---

## 🚀 Следующие шаги

1. Интегрируйте компоненты в Next.js проект
2. Подключите реальные данные из Supabase
3. Добавьте формы с React Hook Form
4. Настройте анимации с Framer Motion
5. Реализуйте фильтрацию и поиск

---

## 📝 Лицензия

Проект Vakansiya.az - Все права защищены © 2025

---

**Создано с использованием:**
- Tailwind CSS v3+
- React/TypeScript
- Современные UI паттерны 2025
- Дизайн-система на основе лучших практик Job Portal дизайна
