# Nimbus Notes — Slidev Presentation (Ocean Professional)

This is a Slidev deck that presents the features and architecture of the Nimbus Notes application using the Ocean Professional aesthetic.

Getting Started:
- Install deps: `pnpm install` (or `npm install`, `yarn`)
- Start dev: `pnpm dev` (or `npm run dev`)
- The preview runs on http://localhost:3000 (configured in vite.config.ts)

Key Files:
- slides.md — main deck content
- style.css — imports theme styles (two-step import pattern)
- theme/custom.css — base dark theme styles
- styles/custom.css — Ocean Professional color tokens (primary #2563EB, secondary #F59E0B, error #EF4444, text #111827, background #f9fafb, surface #ffffff)
- components/FeatureCard.vue — reusable feature card
- components/ArchDiagram.vue — architecture diagram (SVG)
- components/DataModel.vue — data model overview
- public/logo.svg — local logo used on the title slide

Notes:
- Use presenter mode by pressing S
- No external APIs or env vars required
- Deployed build: `pnpm build`
