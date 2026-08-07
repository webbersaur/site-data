# site-data

Public JSON feeds for Webbersaurus client sites hosted on webbalog.

Each file in `clients/` is read at runtime by the corresponding site. The
Change Portal writes to these files; a push deploys to Vercel and the sites
pick the change up within ~30 seconds.

**Sites must fetch from the Vercel URL, not raw.githubusercontent.com:**

    https://site-data-rho.vercel.app/clients/<client>.json

Raw GitHub caches per-edge and ignores cache-busting query params, so the
same URL can serve stale content to one visitor and fresh content to
another for minutes. `vercel.json` sets `s-maxage=30` and a real
`Access-Control-Allow-Origin` header instead.

**This repo is public.** Everything in it is visible to anyone. Only
publish content that already appears on the client's public website —
menu specials, event blurbs, image URLs. No contact lists, no keys,
no internal notes.

## What belongs here vs. in the site itself

Content that is **volatile and low-SEO-value** lives here: weekly food
specials, one-off parties, featured flyer images.

Content that is **stable and SEO-critical** stays in the site's own
`site.data` namespace so it is server-rendered into the HTML: the core
food menu, the recurring weekly events lineup, hours, address, phone.

Putting the core menu in this file would remove it from the
server-rendered HTML that search engines read. Don't.
