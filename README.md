# site-data

Public JSON feeds for Webbersaurus client sites hosted on webbalog.

Each file in `clients/` is read at runtime by the corresponding site. The
Change Portal writes to these files; the sites fetch them on load with a
cache-busting query param, so edits appear within seconds.

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
