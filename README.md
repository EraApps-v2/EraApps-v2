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

## Deploy with Netlify

This repository is configured to publish the repository root as a static site. Connect the GitHub repository to the existing Netlify project `eraapps`, use branch `main`, and leave the build command empty. Future pushes to `main` will start deployments when the Netlify team is allowed to deploy.

From VS Code, stage and commit the changes, then use **Push** or **Sync Changes** to send them to GitHub. Netlify deploys automatically after the repository is connected.

## Security

The Supabase publishable key is intentionally used in frontend code. Keep database access protected by Row Level Security and server-side authorization. Never place a Supabase service-role key or user passwords in this repository.
