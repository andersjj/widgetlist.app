# widgetlist.app

The files that make shared links open WidgetList, set up for GitHub Pages.
Put them at the root of the Pages site, beside the rest of the website.

- `.well-known/apple-app-site-association` — tells iOS and macOS that
  `https://widgetlist.app/open…` links belong to WidgetList (and, later, its
  App Clip). It must load at exactly
  `https://widgetlist.app/.well-known/apple-app-site-association`, with no
  redirect. No file extension.
- `open.html` — the page someone sees when they open a shared link without
  the app. GitHub Pages serves it at `https://widgetlist.app/open?page=…`
  without a redirect.
- `.nojekyll` — stops GitHub Pages' Jekyll step, which otherwise leaves out
  folders starting with a dot, like `.well-known`.
- `CNAME` — the custom domain, `widgetlist.app`. GitHub Pages then redirects
  `www.widgetlist.app` to it.

## GitHub Pages setup

1. Push these files to the repository that publishes the site (the root of
   its publishing branch or folder).
2. In the repository's Settings → Pages, set the custom domain to
   `widgetlist.app` and turn on Enforce HTTPS once it's offered.
3. At your domain registrar, point `widgetlist.app` at GitHub Pages: A records
   to 185.199.108.153, 185.199.109.153, 185.199.110.153 and 185.199.111.153
   (and AAAA records to 2606:50c0:8000::153, 2606:50c0:8001::153,
   2606:50c0:8002::153 and 2606:50c0:8003::153), plus a CNAME record for
   `www` to `<your-github-username>.github.io`.

## Checking it

- `https://widgetlist.app/.well-known/apple-app-site-association` shows the
  JSON directly, with no redirect.
- Apple's copy: https://app-site-association.cdn-apple.com/a/v1/widgetlist.app
  (Apple caches it, so a change can take up to a day to show here).

Once both work, set `AppLink.sharesWebLinks` to `true` so Share Link sends
`https://widgetlist.app/open?page=…` links.
