# sprinklesandsurprises.co.za

Informational website for **Sprinkles & Surprises**, a sweet shop and party pack store at 208 Nigel Road, Selcourt.

Plain static HTML/CSS/JS. No build step, no database.

## Layout

```
public/            ← everything here is the live website (web root)
  index.html       ← home page
  404.html
  .htaccess        ← HTTPS + non-www redirect, caching, security headers
  assets/css/style.css
  assets/js/main.js
  assets/img/      ← logo (webp + png), favicons, social share image
  robots.txt, sitemap.xml, site.webmanifest
.cpanel.yml        ← tells cPanel how to deploy public/ into public_html
```

## Deploying on cPanel (Git™ Version Control)

1. Edit `.cpanel.yml` and replace `CPANELUSER` with the cPanel username. Commit.
2. In cPanel → **SSH Access** → generate a key (no passphrase), then view the public key.
3. In GitHub → repo **Settings → Deploy keys** → add that public key (read-only).
4. In cPanel → **Git™ Version Control** → **Create** → Clone URL
   `git@github.com:bigricza/sprinklesandsurprises-site.git`, repository path e.g.
   `/home/CPANELUSER/repositories/sprinklesandsurprises-site`. Do **not** clone into `public_html` itself.
5. **Manage → Pull or Deploy → Update from Remote**, then **Deploy HEAD Commit**.

Repeat step 5 after every change pushed to `main`.

## Editing content

All copy lives in `public/index.html`. Things to update once known:
- Opening date and trading hours (Visit section + announcement bar)
- Party pack names, contents and prices (Party packs section)
- Social media links (footer)

When CSS/JS changes, bump the `?v=1` on their links in the HTML so browsers pick up the new file.
