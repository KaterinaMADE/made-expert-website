# made.expert — production site

This is the production build of made.expert, assembled from Kate's approved HTML
mockups. It is a plain static site: no build step, no npm dependencies, no
framework. Every page is self-contained HTML with inline `<style>` and inline
base64 images, matching the mockups it was built from.

## Structure

```
index.html                                            homepage
how-to-work.html                                      How to Work page
about.html                                             About Me page
insights/index.html                                    Insights listing page
insights/how-b2b-consultants-attract-clients-on-linkedin.html   article
insights/personal-brand-energy-club-interview.html     article (Energy Club interview, republished with permission)
legal/impressum.html
legal/datenschutzerklarung.html
legal/agb.html
assets/images/                                          favicons + shared OG image
robots.txt / llms.txt / sitemap.xml / site.webmanifest / CNAME
```

## Deploying to GitHub Pages

1. Push this directory as the root of a GitHub repo (e.g. `made-expert-site`).
2. In the repo's Settings → Pages, set the source to the branch you pushed
   (root, not `/docs`).
3. The `CNAME` file already contains `made.expert`, so GitHub Pages will pick
   up the custom domain automatically once DNS is confirmed.
4. DNS: Kate's GoDaddy DNS is already pointed at GitHub Pages per her prior
   setup — no DNS changes should be needed, just verify in GitHub's Pages
   settings that the custom domain shows as verified with HTTPS enforced.

## Legal text source of truth

The German legal copy (Impressum, Datenschutzerklärung, AGB) baked into
`legal/*.html` was generated from `/home/claude/legal-texts-draft.md`
(outside this repo) plus the corresponding Notion doc ("Website. Legal
pages"). **Future edits to the legal text should update both** the Notion
doc and `legal-texts-draft.md`, then be re-applied to the HTML here — the
HTML itself is not the source of truth.

## Cookie consent / analytics

Every page ships a lightweight vanilla-JS cookie consent banner (see the
HTML comment above it in each page) that gates Google Analytics and the
LinkedIn Insight Tag behind consent. It's a placeholder for CookieYes,
which Kate plans to use for the real launch. Before going live:

- Replace `REPLACE_WITH_GA4_ID` with the real GA4 measurement ID.
- Replace `REPLACE_WITH_LINKEDIN_PARTNER_ID` with the real LinkedIn partner ID.
- Swap the vanilla banner for the CookieYes embed once Kate's CookieYes
  account/site ID exists, if she wants to move off the placeholder.

## Still needed before real launch

- Kate's actual CookieYes site ID (if replacing the placeholder banner).
- Real GA4 measurement ID.
- Real LinkedIn Insight Tag partner ID.
- GitHub repo created and this code pushed to it.
- DNS/HTTPS confirmed working end-to-end in GitHub Pages settings.
