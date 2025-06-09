# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

```bash
npm install          # Install dependencies
npm run dev          # Start development server at http://localhost:4321
npm run build        # Build for production to ./dist/
npm run preview      # Preview production build
```

## Architecture Overview

This is a multilingual portfolio website built with Astro, featuring:

- **Static Site Generation**: Pre-renders all pages at build time
- **Internationalization**: English (`/en/`) and Japanese (`/ja/`) with automatic routing
- **Component-Based**: Astro components in `/src/components/` using the i18n translation system
- **Styling**: Tailwind CSS with custom colors (primary: #3b82f6, dark: #111827)

### Key Architectural Patterns

1. **Language Routing**: Pages are generated for each language via `getStaticPaths()` in `/src/pages/[lang]/index.astro`. The root URL redirects to the default language (English).

2. **Translation System**: All text content is stored in `/src/i18n/ui.ts`. Components access translations using:
   ```javascript
   const t = useTranslations(lang);
   const title = t('nav.home');
   ```

3. **Component Structure**: Each section (Hero, About, Skills, etc.) is a separate Astro component that receives the language context and uses translations.

4. **Static Assets**: Images and icons are stored in `/public/` and directly referenced in components.

## Important Notes

- No testing framework is configured
- No linting or formatting tools are set up
- The Works component exists but is currently commented out in the main page
- When adding new content, ensure translations are added for both `en` and `ja` in `/src/i18n/ui.ts`
- All new pages must implement the language routing pattern to maintain multilingual support