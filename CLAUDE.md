# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Next.js 16 application using React 19, TypeScript, and Tailwind CSS v4. The project is bootstrapped with create-next-app and includes a comprehensive shadcn/ui component library setup with the "new-york" style variant.

## Development Commands

```bash
# Start development server at http://localhost:3000
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run linting
npm run lint
```

## Architecture & Structure

### Directory Layout

```
src/
├── app/                    # Next.js App Router
│   ├── layout.tsx         # Root layout with Geist fonts
│   ├── page.tsx           # Home page
│   └── globals.css        # Global styles and Tailwind theme
├── components/
│   └── ui/                # shadcn/ui components (50+ components)
├── hooks/
│   └── use-mobile.ts      # Mobile detection hook
└── lib/
    └── utils.ts           # Utility functions (cn helper)
```

### Key Technologies

- **Next.js 16**: App Router with React Server Components (RSC)
- **React 19.2**: With React Compiler enabled (`reactCompiler: true` in next.config.ts)
- **Tailwind CSS v4**: Using new CSS-first configuration via `@import` in globals.css
- **TypeScript 5**: Strict mode enabled
- **shadcn/ui**: Extensive UI component library pre-installed

### Path Aliases

Configured in tsconfig.json and components.json:
- `@/*` → `./src/*`
- `@/components` → `./src/components`
- `@/lib` → `./src/lib`
- `@/hooks` → `./src/hooks`
- `@/components/ui` → `./src/components/ui`

### Styling System

- **Tailwind CSS v4** with CSS-first configuration (no tailwind.config.js)
- Theme defined inline in `src/app/globals.css` using CSS custom properties
- Uses OKLCH color space for theme colors
- Base color: neutral
- CSS variables enabled for theming
- Dark mode support with `.dark` class
- Custom variant: `@custom-variant dark (&:is(.dark *))`

### Component Architecture

- All UI components from shadcn/ui are in `src/components/ui/`
- Components use:
  - Radix UI primitives for accessibility
  - `class-variance-authority` for variant management
  - `cn()` utility from `@/lib/utils` for className merging
  - React Hook Form + Zod for form validation

### Adding shadcn/ui Components

Since shadcn/ui is configured (components.json exists), add new components with:

```bash
npx shadcn@latest add [component-name]
```

Components will be automatically placed in `src/components/ui/` with proper path aliases.

## Important Configuration Details

- **React Compiler**: Enabled in Next.js config for automatic optimization
- **Fonts**: Geist Sans and Geist Mono loaded via next/font/google
- **ESLint**: Uses Next.js ESM config with flat config format (eslint.config.mjs)
- **Icons**: Lucide React is the primary icon library
- **Package Manager**: Uses pnpm (pnpm-lock.yaml present)

## Pre-installed Libraries

The project includes comprehensive UI packages:
- Form handling: react-hook-form, @hookform/resolvers, zod
- UI primitives: 30+ @radix-ui packages
- Charts: recharts
- Notifications: sonner
- Theming: next-themes
- Utilities: date-fns, cmdk, embla-carousel-react
