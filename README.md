# BADI — landing page

Landing page for **badishoes.com**. One HTML file, no build step.

```
index.html      the page (styles and script inline)
BadiLogo.png    wordmark
badishoe01.png  hero shoe sketch
badishoe02.png  second shoe sketch
favicon.svg     browser tab icon
CNAME           custom domain
.nojekyll       serve files as-is
```

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

## Fonts

Anton, Inter, EB Garamond and Caveat, loaded from Google Fonts.
