# Verda — Legal

Verda's public home page and legal documents, served by **GitHub Pages** at
`legal.verdaplatforms.com`. Nothing here runs on AWS except the DNS pointer
(Route 53 CNAME `legal.verdaplatforms.com` → `deeganp.github.io`); the HTTPS certificate is
issued and renewed by GitHub.

| Page | URL |
|---|---|
| Home | https://legal.verdaplatforms.com/ |
| Privacy Policy | https://legal.verdaplatforms.com/privacy/ |
| Terms & Conditions | https://legal.verdaplatforms.com/terms/ |
| Content Guidelines | https://legal.verdaplatforms.com/guidelines/ |

## Everything here is generated — do not hand-edit

`index.html`, `privacy/`, `terms/`, `guidelines/`, `icon.png`, `CNAME`
and this README are all written by `build.mjs`, which **deletes and rewrites
them on every run**. Edit `build.mjs` instead.

The legal documents come from `Legal/*.html` in the
[Verda_react_native](https://github.com/deeganp/Verda_react_native) repo — the
same files the app renders in-app, so the public copies can't drift.

## Updating

```bash
node build.mjs                                    # sibling checkout
APP_REPO=~/Desktop/Verda/Verda_react_native node build.mjs   # or point at it
```

Then review the diff, commit, and push. GitHub Pages redeploys in about a minute.

Run this whenever the legal docs change in the app repo.

## Why the wrapping exists

`PrivacyPolicy.html` and `TermsAndConditions.html` are HTML *fragments* built
for the in-app WebView — no doctype, no charset, no viewport. Published raw they
render with broken punctuation and desktop-width text on a phone. `build.mjs`
wraps them in real documents and adds the shared nav.

## Where these URLs are referenced

Changing the domain means updating all of these:

- Google Play Console → Policy → App content → Privacy policy
- Google Cloud → OAuth consent screen → Branding (home page, privacy, terms)
- App Store Connect
- The `CNAME` constant in `build.mjs` **and** the Route 53 record
