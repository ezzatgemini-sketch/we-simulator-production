# Vercel Deployment Checklist

Quick steps to ensure successful Vercel deployment for this repo:

- Project Root: Ensure Vercel Project Root is `/` (repository root).
- Framework Preset: Select `Next.js` in Vercel settings.
- Install Command: `npm ci` (or `npm install`).
- Build Command: `npm run build`.
- Output Directory: leave empty for standard Next.js builds; if using standalone, set to `.next/standalone`.
- Vercel Config: `vercel.json` is present at repo root to enforce builder behavior.
- Root Files: Confirm `package.json`, `next.config.ts`, `src/app`, and `prisma/schema.prisma` are at repo root.
- Environment Variables: Add production values in Vercel for `DATABASE_URL`, `NEXTAUTH_URL`, `NEXT_PUBLIC_*` keys, and any other secrets.
- Prisma: Ensure the Prisma client is generated during build (`prisma generate`) or add `postinstall` to `package.json`.
- Node Version: Set Node version in Project Settings or add `engines` in `package.json`.
- Ignore Files: Add `.vercelignore` if you need to skip large/unnecessary files.
- Preview Deploys: Enable Git integration for preview deployments on pull requests.

Post-push verification:
- Check the deployment log for `@vercel/next` build steps.
- Confirm the app serves from routes defined in `src/app` and that serverless functions under `src/app/api` deploy correctly.

Local sanity commands (run before pushing):

```bash
npm ci
npm run db:generate   # if using Prisma
npm run build
```
