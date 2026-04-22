# evmotive.co.uk

Static website for **EVMOTIVE LTD** — an automotive engineering consultancy specialising in vehicle control systems and wiring harness design.

Hosted on GitHub Pages at [evmotive.co.uk](https://evmotive.co.uk/).

## Structure

```
index.html      # Single-page site: hero, services, about, contact
privacy.html    # UK GDPR privacy policy
terms.html      # Terms of service
404.html        # GitHub Pages 404 page
styles.css      # Hand-crafted CSS — no external dependencies
favicon.svg     # Inline SVG favicon
CNAME           # Custom domain — evmotive.co.uk
robots.txt      # SEO
sitemap.xml     # SEO
```

## Editing

Plain static HTML + CSS. No build step. Edit any file, commit, push — GitHub Pages redeploys in <60s.

## Deployment (one-time setup)

1. Push this repo to `ferguskendall2k/evmotive`.
2. In GitHub → **Settings → Pages**: set source to `Deploy from a branch`, branch `main`, folder `/ (root)`.
3. The `CNAME` file is already present — Pages will set custom domain to `evmotive.co.uk`.
4. DNS (at GoDaddy, for apex domain `evmotive.co.uk`):

   | Type  | Name | Value |
   | ----- | ---- | ----- |
   | A     | @    | 185.199.108.153 |
   | A     | @    | 185.199.109.153 |
   | A     | @    | 185.199.110.153 |
   | A     | @    | 185.199.111.153 |
   | CNAME | www  | ferguskendall2k.github.io |

5. For the `.com` domain (`evmotive.com`) — set up a GoDaddy domain forwarding redirect to `https://evmotive.co.uk` (or add the same GitHub Pages A records and use a second Pages site that redirects, but forwarding is simpler).

6. Once DNS propagates (15 min – 24 hr), enable **"Enforce HTTPS"** in GitHub Pages settings.

## Legal

© 2022–present EVMOTIVE LTD. Company number 14131689, registered in England & Wales.
