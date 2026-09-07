# Compliance Scoping Workpaper

A single-page, static HTML tool for scoping compliance engagements (SOC 2,
ISO 27001/27701/42001, HIPAA, GDPR, CCPA, DPDPA, RBI, plus VAPT/CSPM add-ons)
and generating client-ready quotations, engagement letters, and Statements of
Work — all computed client-side, no backend required.

## Local use

Just open `index.html` in a browser. No build step, no dependencies.

## Deploying to GitHub Pages

This repo includes a GitHub Actions workflow
(`.github/workflows/deploy-pages.yml`) that publishes `index.html` to GitHub
Pages automatically on every push to `main`.

### One-time setup

1. Push this repo to GitHub (see commands below).
2. On GitHub, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **GitHub Actions**.
4. Push to `main` (or re-run the workflow from the **Actions** tab) — the site
   will be published at:

   ```
   https://<your-username>.github.io/<repo-name>/
   ```

### Pushing this repo for the first time

```bash
cd compliance-scoping-workpaper
git init
git add .
git commit -m "Initial commit: compliance scoping workpaper"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

After the first push, the "Deploy to GitHub Pages" workflow runs automatically
(check the **Actions** tab for progress). Once it finishes, enable Pages as
described above if you haven't already, and your tool is live.

### Updating the site later

Every time you push a new version of `index.html` to `main`, the workflow
redeploys automatically — no manual steps needed.

## Notes

- Saved quotations (via the "Save Quotation (JSON)" button in the app) are
  plain JSON files downloaded to your machine — nothing is stored server-side
  or in this repo.
- The tool's estimates (effort hours, domain checklists) are a starting point
  for scoping conversations, not professional/legal advice — have a subject
  matter reviewer sanity-check figures before they go into a client-facing
  quote.
