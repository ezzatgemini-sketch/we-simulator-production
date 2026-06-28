# Vercel Deployment Guide

This repo is a Next.js 16 app. The top-level `package.json`, `next.config.ts`, and `src/app` directory are at the repository root.

## Vercel configuration
- `vercel.json` at the repository root configures Vercel to use the project's `package.json` and Next.js builder.

## Build & Run locally
Install dependencies and build:

```bash
npm ci
npm run build
npm run start
```

If using Windows PowerShell and you encounter execution policy issues, run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process -Force
npm run build
```

## Environment
- Ensure `DATABASE_URL` and other env vars are set in Vercel dashboard or using a `.env` file during local testing.

## Notes
- `prisma/schema.prisma` remains at the root and Prisma commands (migrate, generate) should be run from the repo root.
- If Vercel still complains about missing `app` or `pages`, ensure the project root in Vercel settings is set to `/` (root) and no Git subdirectory is configured.
