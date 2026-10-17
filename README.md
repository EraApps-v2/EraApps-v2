# EraApps

Web application for barcode attendance, employee access, store promotions, and dashboard reporting.

## Files

- `index.html`: application interface and client-side logic.
- `supabase-cloud.js`: Supabase authentication, database, and storage integration.
- `supabase-config.js`: Supabase project URL and publishable key used by the frontend.
- `i18n.js`: interface translations.
- `eraapps-template/`: isolated saleable frontend template and static demo.
- `eraapps-template.zip`: template archive.

## Run locally

Open `index.html` in a browser. Cloud login and data access require the configured Supabase project and its schema, Row Level Security policies, Edge Functions, and Storage buckets.

## Publish with GitHub Pages

GitHub Actions publishes the repository root to GitHub Pages whenever changes are pushed to `main`. No Netlify connection or build service is used.

In VS Code, stage and commit changes, then use **Push** or **Sync Changes**. The configured Pages workflow deploys the site automatically; check the repository's **Actions** tab for deployment status.

The site URL is `https://eraapps-v2.github.io/EraApps-v2/` after GitHub Pages has completed its first deployment.

## Security

The Supabase publishable key is intentionally used in frontend code. Keep database access protected by Row Level Security and server-side authorization. Never place a Supabase service-role key or user passwords in this repository.
