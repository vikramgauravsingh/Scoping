# Beskar Engagement Workbench

A single self-contained `index.html` combining two tools:

- **Engagement Scoping & Cost** — SOC 2 / ISO 27001 / HIPAA scoping, requirement
  effort, VAPT and CSPM add-ons, and engagement cost ledger.
- **Statement of Work** — references the MSA and MNDA, captures client and
  signatory details, and generates ready-to-sign filled MNDA/MSA `.docx` files
  entirely in the browser (the two agreement templates and the merge library
  are embedded in the page — nothing is uploaded to a server).

No build step, no dependencies, no backend. It's one static HTML file.

## Deploy to Vercel via GitHub

1. **Create a GitHub repo** and add this folder's contents (just `index.html`,
   this `README.md`, and `vercel.json`) to it, e.g.:
   ```bash
   git init
   git add index.html README.md vercel.json
   git commit -m "Add Beskar Engagement Workbench"
   git branch -M main
   git remote add origin https://github.com/<your-org>/<your-repo>.git
   git push -u origin main
   ```

2. **Import into Vercel**:
   - Go to [vercel.com/new](https://vercel.com/new)
   - Select "Import Git Repository" and choose the repo you just pushed
   - Framework preset: **Other** (it's a static file, no build command needed)
   - Leave Build Command and Output Directory blank
   - Click **Deploy**

   Vercel serves `index.html` at the project's root URL automatically since
   there's no other routing to configure.

3. **Every future push to `main`** redeploys automatically — no further setup
   needed.

## Updating the two governing-document templates

The MNDA and MSA merge fields live as base64-encoded `.docx` inside
`index.html` (`TEMPLATE_MNDA_B64` / `TEMPLATE_MSA_B64` constants near the top
of the first inline `<script>` block). To swap in a revised agreement:

1. Edit the `.docx` in Word, keeping the `{client_name}`, `{client_jurisdiction}`,
   `{client_address}`, `{client_attention}`, `{client_email}`,
   `{client_signatory_name}`, `{client_signatory_title}`,
   `{client_signature_date}`, `{effective_date}`, `{msa_place}`, `{msa_day}`,
   `{msa_month}`, `{msa_year}` merge tags intact (curly-brace syntax,
   docxtemplater's default delimiters).
2. Base64-encode the file and replace the matching constant in `index.html`.

## Local preview

Just open `index.html` directly in a browser — no server required.

## Tabs (v2)
Scoping (SOC 2, ISO 27001, HIPAA, GDPR, CCPA/CPRA, DPDPA + VAPT/CSPM) · SOW · Invoice · MNDA · MSA · Questionnaire.
Each of SOW, Invoice, MNDA and MSA has a **Print / Save as PDF** button that prints only that document (A4, clean, no app chrome). MNDA/MSA also keep the .docx download.
