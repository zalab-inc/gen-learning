# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Next.js 16 application using React 19, TypeScript, and Tailwind CSS v4. The project is bootstrapped with create-next-app and includes a comprehensive shadcn/ui component library setup with the "new-york" style variant.

**Key Stats:**
- 53 pre-installed shadcn/ui components
- React Server Components (RSC) enabled
- React 19 Compiler optimization enabled
- TypeScript strict mode
- Package manager: pnpm

## Development Commands

```bash
# Start development server at http://localhost:3000
pnpm dev
# Alternative: npm run dev

# Build for production
pnpm build

# Start production server
pnpm start

# Run linting
pnpm lint
```

## Architecture & Structure

### Directory Layout

```
/
├── public/                 # Static assets (SVGs, icons)
│   ├── file.svg
│   ├── globe.svg
│   ├── next.svg
│   ├── vercel.svg
│   └── window.svg
└── src/
    ├── app/                # Next.js App Router
    │   ├── layout.tsx      # Root layout with Geist fonts
    │   ├── page.tsx        # Home page
    │   ├── globals.css     # Global styles and Tailwind v4 theme
    │   └── favicon.ico
    ├── components/
    │   └── ui/             # shadcn/ui components (53 components)
    ├── hooks/
    │   └── use-mobile.ts   # Mobile detection hook (768px breakpoint)
    └── lib/
        └── utils.ts        # Utility functions (cn helper)
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

**Tailwind CSS v4** (CSS-first configuration):
- No `tailwind.config.js` - configuration is CSS-based
- PostCSS setup with `@tailwindcss/postcss` package
- Animation utilities via `tw-animate-css` package
- Theme defined in `src/app/globals.css` using `@theme inline` directive

**Color System:**
- OKLCH color space for better color perception
- Base color: neutral (high contrast, accessible)
- CSS custom properties for dynamic theming
- Comprehensive color tokens: primary, secondary, muted, accent, destructive, chart (1-5), sidebar
- Border radius system: sm, md, lg, xl (based on `--radius: 0.625rem`)

**Dark Mode:**
- Class-based dark mode (`.dark` class on root element)
- Custom variant: `@custom-variant dark (&:is(.dark *))` for nested dark mode
- Full theme color overrides in dark mode
- Alpha channel support for borders and inputs in dark mode

**Typography:**
- Font variables: `--font-geist-sans` and `--font-geist-mono`
- Applied via Tailwind's font-sans and font-mono utilities

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

### Core Configuration

- **React Compiler**: Enabled (`reactCompiler: true` in next.config.ts) for automatic React optimizations
- **Fonts**: Geist Sans and Geist Mono loaded via `next/font/google` with CSS variables
- **Package Manager**: pnpm (lockfile: pnpm-lock.yaml)
- **Icons**: Lucide React v0.553.0 is the primary icon library

### ESLint Configuration

- Flat config format using `eslint.config.mjs` (ESLint v9+)
- Extends: `eslint-config-next/core-web-vitals` and `eslint-config-next/typescript`
- Global ignores: `.next/`, `out/`, `build/`, `next-env.d.ts`
- Run with: `pnpm lint` or `eslint .`

### TypeScript Configuration

- Target: ES2017
- Module: ESNext with bundler resolution
- Strict mode enabled
- JSX: react-jsx (automatic runtime)
- Path alias: `@/*` → `./src/*` (configured in tsconfig.json)
- Includes Next.js plugin for enhanced type checking

## Pre-installed Libraries

### UI & Component Libraries

**Core UI System:**
- **shadcn/ui**: 53 pre-installed components (new-york style)
- **Radix UI**: 30+ primitive packages for accessibility (@radix-ui/react-*)
- **class-variance-authority** (v0.7.1): Type-safe component variants
- **Lucide React** (v0.553.0): Icon library

**Form & Validation:**
- **react-hook-form** (v7.66.0): Performant form library
- **@hookform/resolvers** (v5.2.2): Validation resolvers
- **zod** (v4.1.12): TypeScript-first schema validation

**Advanced Components:**
- **recharts** (2.15.4): Composable charting library
- **react-day-picker** (v9.11.1): Date picker component
- **embla-carousel-react** (v8.6.0): Carousel/slider
- **cmdk** (v1.1.1): Command palette
- **sonner** (v2.0.7): Toast notifications
- **vaul** (v1.1.2): Drawer component
- **input-otp** (v1.4.2): OTP input
- **react-resizable-panels** (v3.0.6): Resizable panel layouts

**Theming & Styling:**
- **next-themes** (v0.4.6): Dark mode support
- **Tailwind CSS** (v4): Utility-first CSS
- **tailwind-merge** (v3.4.0): Merge Tailwind classes without conflicts
- **clsx** (v2.1.1): Conditional className utility
- **tw-animate-css** (v1.4.0): Animation utilities

**Utilities:**
- **date-fns** (v4.1.0): Date utility library

### Development Dependencies

- **TypeScript** (v5): Type safety
- **@tailwindcss/postcss** (v4): PostCSS integration
- **babel-plugin-react-compiler** (1.0.0): React 19 compiler plugin
- **ESLint** (v9): Code linting with Next.js config

## Installed shadcn/ui Components

The following 53 components are pre-installed in `src/components/ui/`:

**Layout & Navigation:**
accordion, breadcrumb, card, carousel, collapsible, menubar, navigation-menu, resizable, scroll-area, separator, sidebar, sheet, tabs

**Forms & Inputs:**
button, button-group, checkbox, field, form, input, input-group, input-otp, label, radio-group, select, slider, switch, textarea, toggle, toggle-group

**Feedback:**
alert, alert-dialog, badge, empty, progress, skeleton, spinner, toast, toaster, tooltip

**Overlays:**
dialog, drawer, dropdown-menu, hover-card, popover, context-menu

**Data Display:**
aspect-ratio, avatar, calendar, chart, kbd, table

**Advanced:**
command, date-picker, pagination, sonner

## Best Practices

### Component Usage

1. **Import shadcn/ui components** from `@/components/ui`:
   ```tsx
   import { Button } from "@/components/ui/button"
   import { Card, CardHeader, CardContent } from "@/components/ui/card"
   ```

2. **Use the `cn()` utility** for conditional classes:
   ```tsx
   import { cn } from "@/lib/utils"

   <div className={cn("base-class", condition && "conditional-class")} />
   ```

3. **Form validation** with react-hook-form + Zod:
   ```tsx
   import { useForm } from "react-hook-form"
   import { zodResolver } from "@hookform/resolvers/zod"
   import { z } from "zod"
   ```

### Styling Guidelines

- Use Tailwind utility classes for styling
- Leverage CSS variables for theming (e.g., `bg-background`, `text-foreground`)
- Use semantic color tokens: `primary`, `secondary`, `muted`, `accent`, `destructive`
- For charts, use `chart-1` through `chart-5` color tokens
- Maintain accessibility with proper contrast ratios (OKLCH color space helps)

### File Organization

- Place reusable hooks in `src/hooks/`
- Place utility functions in `src/lib/`
- Keep page-specific components in `src/app/[route]/` directories
- Share global components in `src/components/` (not in `ui/`)

## Troubleshooting

### Common Issues

**TypeScript errors after adding new components:**
```bash
# Restart TypeScript server in your editor
# Or regenerate Next.js types
rm -rf .next && pnpm dev
```

**Tailwind classes not applying:**
- Ensure the class is valid Tailwind v4 syntax
- Check that CSS variables are defined in `globals.css`
- Verify the element is within the layout that imports `globals.css`

**Dark mode not working:**
- Ensure you're using `next-themes` ThemeProvider in your layout
- Apply the `.dark` class to the root element (usually via ThemeProvider)
- Check that dark mode color variables are defined in `globals.css`

**Component not found errors:**
- Verify the component exists in `src/components/ui/`
- Check that path aliases are configured in `tsconfig.json` and `components.json`
- Ensure imports use `@/` prefix: `import { Button } from "@/components/ui/button"`

## Deployment

This is a standard Next.js application that can be deployed to:

- **Vercel** (recommended): Zero-config deployment
- **Other platforms**: Ensure Node.js 20+ and pnpm support
- Build command: `pnpm build`
- Start command: `pnpm start`
- Output: `.next/` directory

### Environment Variables

No environment variables are required for the base setup. Add any API keys or secrets to:
- `.env.local` (for local development, git-ignored)
- Platform environment variable settings (for production)

## Additional Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [shadcn/ui Documentation](https://ui.shadcn.com)
- [Tailwind CSS v4 Documentation](https://tailwindcss.com/docs)
- [Radix UI Primitives](https://www.radix-ui.com/primitives)
- [React Hook Form](https://react-hook-form.com)
- [Zod Documentation](https://zod.dev)
