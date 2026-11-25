# App Store Review Explorer

A zero-backend, single-file web application for fetching, caching, analyzing, and exporting Apple App Store customer reviews for **any** iOS/macOS app using the public iTunes RSS/JSON feed API.

**Live site (GitHub Pages):** https://siuvoniazzi.github.io/appstorereviews/

## Features

- **Save Any App in IndexedDB**: Add apps by numeric Apple App ID (e.g. `389801252`), `id`-prefixed ID, or full App Store URL (`https://apps.apple.com/.../id...`). App names and preferred storefronts are stored locally in your browser's IndexedDB.
- **Incremental Delta Sync**: Reviews are cached per `(App ID, Storefront)` in IndexedDB. On subsequent refreshes, the app fetches only unseen reviews and stops early once it reaches already-cached entries.
- **Analytics & Trends**:
  - Total unique reviews, average star rating, positive sentiment share (`≥ 4★`), and interactive 5★–1★ distribution bars.
  - Weekly rating average & review volume chart (ISO calendar weeks).
- **Filtering & Search**: Filter by keyword, author, app version, and star rating; sort by newest, oldest, highest rated, or lowest rated.
- **Exports & Fallbacks**:
  - Export filtered reviews as **Excel-ready CSV** (UTF-8 BOM), **JSON**, or **Markdown**.
  - Built-in CORS proxy fallback (`Auto`, `Direct`, `AllOrigins`, `CorsProxy.io`) and manual **Paste Raw JSON/XML** import.
  - Dynamic **Dart / Flutter** snippet generator synced with your current App ID, storefront, and sort order.

## GitHub Pages Deployment

This repository is preconfigured to deploy automatically via GitHub Actions (`.github/workflows/deploy-pages.yml`):

1. Push the changes to the `main` branch.
2. In your GitHub repository, open **Settings → Pages**.
3. Under **Build and deployment → Source**, select **GitHub Actions**.
4. The workflow will publish `index.html` to `https://siuvoniazzi.github.io/appstorereviews/` on every push to `main` (or via manual **Actions → Deploy to GitHub Pages → Run workflow**).

## Local Usage

No build step is required—open `index.html` directly in any modern browser or serve the directory with any static file server:

```bash
python3 -m http.server 8080
```