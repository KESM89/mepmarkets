# MEP Markets

Delayed quotes, earnings dates, news, and long-term analysis for publicly traded companies in the mechanical, electrical, plumbing, and building systems sectors.

**Live site:** [mepmarkets.com](https://mepmarkets.com)

---

## Site structure

```
/
├── index.html          Main watchlist page
├── about.html          About the site
├── manage.html         Browser-based watchlist manager
├── stocks.json         Editable company list
├── analysis/
│   └── index.html      Analysis / blog post listing
│   └── [post].html     Individual posts (add as needed)
└── README.md
```

---

## Adding companies to the watchlist

### Option 1 — Edit stocks.json (permanent, affects all visitors)

Open `stocks.json` in GitHub's web editor and add an entry:

```json
{ "symbol": "XYZ", "name": "Company Name", "sector": "Your Sector", "ir": "https://ir.example.com" }
```

Fields:
- `symbol` — NYSE/NASDAQ ticker (required)
- `name` — Full company name (required)
- `sector` — Your sector label, e.g. "OEM / Equipment" (optional)
- `ir` — Investor relations URL (optional)

Commit the change. GitHub Pages will rebuild in under a minute and the new company will appear on the watchlist automatically.

### Option 2 — Use the Manage page (browser only, personal)

Go to `/manage.html` on the live site. Enter a ticker, name, sector, and optional IR link. The company is saved to your browser's localStorage and merged into your personal watchlist. This does not affect other visitors.

---

## Publishing a blog post

1. Create a new file in `/analysis/` — e.g. `analysis/wso-watsco-hvac-distribution.html`
2. Use any existing analysis post as a template
3. Add a link to the new post in `analysis/index.html`
4. Commit both files

---

## GitHub Pages setup

1. Create a new repository named `mepmarkets` (or any name)
2. Upload all files maintaining the folder structure
3. Go to **Settings → Pages → Branch: main → / (root)**
4. Save — site goes live at `https://yourusername.github.io/mepmarkets/`
5. Add a custom domain in Settings → Pages → Custom domain → `mepmarkets.com`
6. Update DNS at your registrar:
   - Add four A records pointing to GitHub's IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Add a CNAME record: `www` → `yourusername.github.io`

---

## Data sources

- **Quotes, P/E, earnings dates, analyst targets** — Yahoo Finance (unofficial API, delayed)
- **News headlines** — Yahoo Finance search API
- **IR links** — Manually maintained in stocks.json
- **SEC links** — Auto-generated from ticker symbol via EDGAR

All data fetched client-side via [corsproxy.io](https://corsproxy.io). No server required.

---

## Disclaimer

Not investment advice. Delayed quotes. For informational purposes only.
