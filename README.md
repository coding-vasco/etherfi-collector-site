# Etherfi Collector information website

Public, static application information for Google OAuth Branding. No collector
code, credentials, account records, wallet addresses or workbook IDs belong in
this repository. No JavaScript, frameworks, analytics, cookies or backend.

Deploy only this directory to the dedicated repository
`coding-vasco/etherfi-collector-site`, independently of all other projects.

## Render configuration

- New **Static Site**, preferred name `etherfi-collector`.
- Source: this repository, branch `main`.
- Build command: `true`; publish directory: `public`.
- Environment: `SKIP_INSTALL_DEPS=true`; no secrets.
- Automatic deployment: off. No paid compute plan, custom domain or collector.
- Rewrite `/privacy` to `/privacy.html` (do not use a catch-all homepage rewrite).
- `render.yaml` includes these settings and static response headers.

The Render create-static-site connector cannot configure rewrite rules. If used,
add the exact rewrite in the new site's Redirects/Rewrites settings, or use this
repository's Blueprint. Do not assume a schema file in a repository is applied
when a service is created through the separate connector action.

Static hosting has no paid instance; Render's shared bandwidth/build allowances
still apply. No workspace upgrade, add-on or paid service is authorized.

## Before entering URLs in Google

1. Wait for the new static site's successful deployment. Use the actual hostname
   returned by Render; the preferred name may be unavailable.
2. Verify GET `/` and GET `/privacy` return HTTP 200 with distinct intended pages
   and a homepage link to `/privacy`. Check mobile/desktop rendering.
3. In the existing Google project's Branding page, enter that homepage and
   privacy URL. Do not publish the OAuth app, grant consent or change scopes.
4. If Google requires domain ownership, check which exact host it requests.
   `onrender.com` is on the Public Suffix List; Google's documented top-private-
   domain rule therefore suggests the assigned subdomain may be the relevant
   authorized domain. This is an inference, not proof of Google acceptance.
5. Search Console URL-prefix verification may offer an HTML file or meta tag
   for a host you control. A project owner/editor must complete any required
   account/verification approval. No verification token is included here.
6. Stop if the required ownership cannot be verified. Do not buy a domain,
   change providers, create another service or claim ownership of `onrender.com`.

Creating this website does not authorize deploying the financial collector.
Existing `production/OAUTH_SETUP.md` and its restrictions remain unchanged.

Official references checked 15 November 2026:

- https://render.com/docs/static-sites.md
- https://render.com/docs/redirects-rewrites.md
- https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification
- https://publicsuffix.org/list/public_suffix_list.dat
