# G Labs — legal site

Public privacy policies for G Labs apps, served by GitHub Pages.

**Live:** https://galangajisusanto.github.io/glabs-legal/

This repo is public *only* so GitHub Pages can serve it on the free plan — app source lives in its
own private repo. Keep nothing here that isn't meant to be read by the whole internet.

## Why plain HTML

GitHub Pages without Jekyll serves a `.md` file as raw text, and a privacy policy that renders as
raw Markdown is a documented Google Play rejection ("does not link to a valid privacy policy page").
`.nojekyll` turns the build step off entirely, so what you commit is exactly what a reviewer sees.

Don't add Markdown pages here expecting them to render.

## Layout

```
.nojekyll                     # no Jekyll build — serve files verbatim
index.html                    # hub: lists every app, links to each policy
assets/style.css              # shared styling for all pages (app-neutral)
kasira/index.html             # Kasira POS privacy policy
iqro-ummah/index.html         # Iqro Ummah privacy policy
iqro-ummah/terms/index.html   # Iqro Ummah terms & conditions
budgetku/index.html           # Budgetku privacy policy
```

GitHub Pages maps a directory to its `index.html`, so `kasira/index.html` is served at
`/glabs-legal/kasira/`.

## Adding a policy for a new app

1. Copy the `kasira/` folder to `<your-app>/` and rewrite the content. Keep the structure — the
   section list (what's stored, permissions and why, identifiers, what leaves the device, payments,
   what we don't do, children, your control, security, changes, contact) is what Google's reviewers
   look for.
2. Add a card to the `<ul class="apps">` list in `index.html`.
3. Commit and push. Pages redeploys in about a minute.

Two rules that keep it Play-compliant:

- **Name the app and "G Labs" in the text.** Play requires the entity from the store listing, or the
  app itself, to appear in the policy.
- **Describe what the app actually does.** Every permission the app declares needs a reason here,
  and the Data safety form in Play Console must agree with this page. A mismatch between the two is
  a rejection.

Don't touch `assets/style.css` for app-specific tweaks — it's shared by every page.

## Google Play requirements this satisfies

An active, publicly accessible, non-geofenced URL; HTML rather than PDF; non-editable by visitors;
and the developer entity named in the policy. The URL also has to be entered in **Play Console → App
content → Privacy policy**, and linked from inside the app — Kasira does that from
Settings → About → Privacy Policy.

## Deployment

Settings → Pages → Source *Deploy from a branch* → branch `main`, folder `/ (root)`. Every push to
`main` republishes.
