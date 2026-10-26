# Bayan Prospect website

Static one-page site for GitHub Pages. No build step.

## Publish on GitHub Pages
1. Copy everything in this folder into the root of your GitHub Pages repo, replacing the old files: `index.html`, `assets/`, `data/`, `scripts/` and the hidden `.github/` folder.
2. Keep your existing `CNAME` file so bayanprospect.com stays linked.
3. Commit and push.

## Live "Tax & financial updates" section
The site has country tabs (**UAE · Jordan · Oman · Qatar**). Each tab shows **tax authority news** and **financial news**, kept up to date automatically:

- `.github/workflows/update-news.yml` runs every 3 hours on GitHub, for free.
- It runs `scripts/fetch-news.mjs`, which reads these feeds and saves the headlines to `data/news.json`:

| Country | Tax news | Financial news |
|---|---|---|
| UAE | Federal Tax Authority (official RSS) | The National, Khaleej Times (UAE finance stories only), Argaam UAE |
| Jordan | Google News search for ISTD / Jordan income & sales tax (the ISTD website has no feed) | Google News search for Jordan economy, Central Bank of Jordan, Amman Stock Exchange |
| Oman | Google News search for Oman Tax Authority / VAT / income tax / e-invoicing | Google News search for Oman economy, Central Bank of Oman, Muscat Stock Exchange |
| Qatar | Google News search for General Tax Authority / Dhareeba / income & withholding tax | Google News search for Qatar economy, Qatar Central Bank, Qatar Stock Exchange |

**One-time setup after the first push:**
1. In the repo, go to **Settings → Actions → General → Workflow permissions** and choose **Read and write permissions**.
2. Go to the **Actions** tab, open **Update news feed**, and click **Run workflow** to load the first headlines.

If a feed is ever unavailable, the site keeps the last headlines it had for that panel, and each panel always shows quick links (FTA, ISTD, Oman Tax Authority, Qatar GTA and the news sites).

To add or remove a source, edit the `FEEDS` list at the top of `scripts/fetch-news.mjs`.

## Editing
- Contact form opens the visitor's email app addressed to admin@bayanprospect.com.
- Brand colours are CSS variables at the top of the `<style>` block in `index.html`.
