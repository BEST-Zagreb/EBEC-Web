# EBEC

Static archive of the website that ran at **best.hr/ebec** until 2026-09-10, when the WordPress server
behind it was retired. Every page here is plain HTML. There is no database, no PHP and nothing to
keep patched.

Home: **https://ebec.best.hr/**

- 14 published pages, 131 files, 18.9 MB
- Verified: every page and asset requested over HTTP, 118 URLs, **0 failures**
- Verified: every page rendered in a browser, **0 broken images**

## Looking at it locally

    python3 -m http.server 8000

Then open <http://127.0.0.1:8000/>. Any static file server works, and so does dragging the folder
into Cloudflare Pages or Netlify.

## How it was made

Mirrored with `wget`, then checked against the site's own database rather than by clicking around,
because a crawler only finds pages that something links to. The full method, the tooling and the
verification results live in the migration notes alongside this archive.

## What deliberately differs from the original

This is a faithful copy with three exceptions, all of them deliberate.

### Links were made relative

Every reference to `best.hr` that pointed at a file in this archive was rewritten to a relative
path, so the site is self-contained and does not call a server that no longer exists. Links to
genuinely external sites are untouched.

### Personal contact details were replaced

Named personal email addresses and mobile phone numbers were replaced with the organisation's role
address, **ebec@best.hr**. This archive is public and outlives the students named in it. People's names
stay, as credit; their private contact details do not.

### Links that led nowhere were repaired or removed

Some links were already broken on the live site. Where the target still existed under a different
address it was repointed; where it existed nowhere the link was removed and the surrounding
content left in place.

### Two pages were rebuilt, not copied

`about-us/faq-en/` and `best-team/jury/` returned 404 at every address on the old server,
including `?page_id=`, so no crawler could reach them. Their content was intact in the database,
so both were rebuilt from their Croatian counterpart's page shell with the English content
substituted in. Every other page here came off the live site verbatim.

### The English menu was repointed

64 menu links pointed at `/ebec/en/<page>/` addresses that all returned 404 on the old server.
Each now points at the page that actually holds that content.

### Most inner pages were already empty

`about-us`, `press-kit`, `o-nama` and `organizacijski-tim` serve navigation and no content. That
is how the old server served them too, verified in a browser before freezing. Only the front
page, `o-nama/faq/`, `organizacijski-tim/ziri/` and the two rebuilt English pages have content.

## Licence

The content, images and copy belong to BEST Zagreb. Third-party theme and plugin assets under
`wp-content/` remain under their own licences and are included only because the pages need them to
render as they originally did.

## Hosting

Live at <https://ebec.best.hr/>, served by Cloudflare Workers as static files straight from this repository.
This repository is archived and read-only: the site it holds is finished. If something must change, unarchive it, push to `main`, and Workers Builds redeploys within a minute or two.

## Wayback Machine

The site ran at <https://best.hr/ebec/>. The Internet Archive's calendar for it is <https://web.archive.org/web/*/https://best.hr/ebec/*>.
Checked on 2026-09-11: captures run from 2012-07-28 (the static EBEC Zagreb 2012 site that came before this one) to at least 2025-11-04, with 50 distinct HTML pages answering 200. A fresh capture of every published page was requested on 2026-09-11.
This repository is the complete copy of the site as it was frozen; the archive is a partial, independent second copy.
