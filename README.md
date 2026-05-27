# ⚡ TBHQR

> Privacy-first QR code generator that runs entirely in your browser. No tracking, no storage, no servers processing your data.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Privacy: 100%](https://img.shields.io/badge/Privacy-100%25_Client_Side-green.svg)](#privacy)

## Features

- **7 QR data types**: URL, Text, Wi-Fi, vCard, Email, SMS, Geo-location
- **Full customization**: colors, dot styles, corner styles, sizes, error-correction levels
- **Logo embedding** processed locally (never uploaded)
- **Top + bottom captions** with custom font sizes
- **4 export formats**: PNG, SVG, JPG, PDF
- **Works offline** after first load (PWA)
- **Zero data collection** — verifiable in DevTools

## Quick Start

### Local preview

```bash
# Any static file server works. For example:
npx serve .
# or
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

### Deploy in 2 minutes

Pick any free static host:

| Host                | How                                                                  |
| ------------------- | -------------------------------------------------------------------- |
| **Cloudflare Pages** | Drag the folder to `pages.cloudflare.com` → done                     |
| **Netlify Drop**    | Drag the folder to `app.netlify.com/drop`                            |
| **GitHub Pages**    | Push to a repo → Settings → Pages → Deploy from branch               |
| **Vercel**          | Run `vercel deploy` in the project folder                            |

All four provide free HTTPS automatically.

## Project Structure

```
TBHQR/
├── index.html              # Full app (HTML + CSS + JS)
├── favicon.svg             # Vector favicon
├── robots.txt              # SEO directives
├── sitemap.xml             # Search engine sitemap
├── _headers                # Security headers (CF / Netlify)
├── _redirects              # SPA routing rules
├── manifest.webmanifest    # PWA manifest
├── sw.js                   # Service worker (offline)
├── .gitignore
├── LICENSE
└── README.md
```

## Privacy

TBHQR does not:

- Collect, store, or transmit any user input
- Use analytics, cookies, or trackers
- Have a backend or database
- Require accounts or sign-ups

**How to verify:**

1. Open DevTools → Network tab
2. Generate any QR code with sensitive data
3. Observe: no outbound requests carry your input

After the initial page load, you can disconnect from the internet entirely — TBHQR keeps working.

## Tech Stack

- **Vanilla HTML / CSS / JavaScript** (no frameworks, no build step)
- **[qr-code-styling](https://github.com/kozakdenys/qr-code-styling)** — QR rendering engine
- **[jsPDF](https://github.com/parallax/jsPDF)** — PDF export
- **Service Worker** — offline cache

## Pre-Deploy Checklist

Before you publish:

1. Replace `yourdomain.com` in `robots.txt` and `sitemap.xml`
2. Update the copyright name in `LICENSE`
3. Add the manifest + service-worker registration snippets into `index.html` (see comments in `sw.js` and `manifest.webmanifest`)
4. Verify the security headers loaded correctly using [securityheaders.com](https://securityheaders.com)
5. Test the PWA install prompt on mobile

## License

MIT — see [LICENSE](./LICENSE).

## Contributing

Issues and PRs welcome. The single guiding rule: **no change may introduce data collection, tracking, or server-side processing of user input.**