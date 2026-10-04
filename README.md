# G.O.A. Marine Concierge website

Static site (plain HTML/CSS, tiny JS, no build step) for goamarineconcierge.com.

- Pages: `index.html`, `privacy.html`, `terms.html`, `support.html`, `404.html`
- Logo / favicon: swap `assets/logo.png` and `assets/favicon.png` (every page references only these paths; logo.png is also the Open Graph image).
- Styles: `assets/styles.css` · JS: `assets/site.js` (mobile menu + footer year)

## Preview
https://thesonarman850.github.io/goa-website/

## Going live on goamarineconcierge.com (later)
The custom domain is intentionally NOT set yet: once it is set, the github.io preview
redirects to goamarineconcierge.com, which doesn't point here yet.

1. In GoDaddy DNS for goamarineconcierge.com, add:

   | Type  | Name | Value                    | TTL     |
   |-------|------|--------------------------|---------|
   | A     | @    | 185.199.108.153          | 1 hour  |
   | A     | @    | 185.199.109.153          | 1 hour  |
   | A     | @    | 185.199.110.153          | 1 hour  |
   | A     | @    | 185.199.111.153          | 1 hour  |
   | CNAME | www  | thesonarman850.github.io | 1 hour  |

   Remove any conflicting existing `@` A records (e.g. GoDaddy parking) and any existing `www` record first.
2. Add a `CNAME` file at the repo root containing `goamarineconcierge.com` and push, or run:
   `gh api -X PUT repos/thesonarman850/goa-website/pages -f cname=goamarineconcierge.com`
3. After the certificate is issued (can take up to ~1 hour), enable HTTPS:
   `gh api -X PUT repos/thesonarman850/goa-website/pages -F https_enforced=true`

## Placeholders
- `support@goamarineconcierge.com` is used for all contact links; the mailbox still needs to be set up.
