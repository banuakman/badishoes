# BADI — landing page

Static landing page for **badishoes.com**. One HTML file, no build step.

```
index.html      the page (styles and script inline)
BadiLogo.png    wordmark (transparent PNG; used as a CSS mask so it can be recolored)
badishoe01.png  hero shoe sketch (transparent PNG)
badishoe02.png  second shoe sketch (transparent PNG)
favicon.svg     browser tab icon
CNAME           custom domain for GitHub Pages
.nojekyll       tells GitHub Pages to serve files as-is
```

The two shoe PNGs are large (0.6 MB and 1 MB). They work as-is, but if you
want a faster first load, export them as WebP or run them through an
optimizer such as Squoosh (https://squoosh.app) and keep the same file names.

## Email capture

The form on the page posts directly into the Google Form
<https://forms.gle/AMSR2Z3HmGQWkH1X6>, so every signup lands in that form's
Responses tab / linked Google Sheet. The page styles its own fields so it
matches the brand; Google's own form UI is not shown.

Field mapping (Google Form field ID → page input):

| Google Form field | `name` attribute   |
|-------------------|--------------------|
| First Name        | `entry.150833369`  |
| Last Name         | `entry.1113314196` |
| Email Address     | `entry.2132081416` |
| Zip Code          | `entry.535801220`  |

If you add, remove, or rename fields in Google Forms, the IDs change. To get
the new ones: open the form's public link, view page source, and search for
`entry.` — or use the browser's network tab while submitting a test response.

Keep the Google Form set to **"Anyone with the link"** (no sign-in required),
otherwise submissions from the site will be rejected. Do not turn on
"Collect email addresses" in the form settings; that mode requires sign-in.

A "Prefer Google? Open the form directly" link under the form is a fallback
that always works.

## Publishing on GitHub Pages

GitHub Pages on a **private** repository requires GitHub Pro, Team, or
Enterprise. On a Free plan the repo must be public for Pages to work.

1. Create the private repo on GitHub (e.g. `badishoes`).
2. Push this folder:

   ```bash
   git init -b main
   git add .
   git commit -m "Add BADI landing page"
   git remote add origin git@github.com:<your-org>/badishoes.git
   git push -u origin main
   ```

3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy
   from a branch**, branch `main`, folder `/ (root)`. Save.
4. Under **Custom domain**, enter `badishoes.com` (this matches the `CNAME`
   file) and tick **Enforce HTTPS** once the certificate is issued.

## DNS for the custom domain

At your DNS provider:

| Type  | Host | Value                         |
|-------|------|-------------------------------|
| A     | @    | 185.199.108.153               |
| A     | @    | 185.199.109.153               |
| A     | @    | 185.199.110.153               |
| A     | @    | 185.199.111.153               |
| CNAME | www  | `<your-org>.github.io`        |

To use `www.badishoes.com` as the primary URL instead, change the contents of
`CNAME` to `www.badishoes.com` and set the same value in Settings → Pages.

## Fonts

Brand type is Knockout HTF (headlines) and Suisse Int'l (body). Both are
licensed, so the page loads free stand-ins from Google Fonts (Anton, Inter,
EB Garamond, Caveat). The CSS font stacks list the brand fonts first; if you
own licenses, add `@font-face` rules pointing at self-hosted files and the
brand fonts take over without any other change.

## Local preview

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.
