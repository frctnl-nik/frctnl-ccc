# Cash Conversion Cycle Illustrator (Frctnl Finance)

A static, single-page tool. No build step, no server, no database. All calculations run in the visitor's browser and nothing they enter is stored or sent.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS, JavaScript, and the logo as an inline image) |
| `vendor/jspdf.umd.min.js` | jsPDF 2.5.1, used for "Download results as PDF" (hosted locally, no CDN) |
| `vercel.json` | Clean URLs, security headers, and permission to embed the page on frctnl.biz |
| `favicon.svg` | Browser tab icon |
| `logo-plum.png` | Your logo with a transparent background, in plum |
| `robots.txt` | Allows search engines |

The page loads two Google Fonts (Figtree and Newsreader) from fonts.googleapis.com. Everything else is self-contained.

## Deploy

**Option A: Vercel CLI (quickest)**

```bash
cd frctnl-ccc
npx vercel          # first run: log in, accept the defaults to get a preview URL
npx vercel --prod   # publish to production
```

When asked, choose "Other" as the framework and leave the build command and output directory empty (or `.`).

**Option B: Git**

1. Put this folder in a GitHub repository.
2. In Vercel choose Add New, then Project, and import the repository.
3. Framework preset: Other. Build command: none. Output directory: `.` (the root). Deploy.

**Option C: Drag and drop**

Use Vercel's dashboard import for a local folder, or the CLI as in Option A.

## Use your own domain

In the Vercel project, open Settings, then Domains, and add something like `cash.frctnl.biz`. Vercel shows the DNS record to add (usually a CNAME to `cname.vercel-dns.com`).

## Embed on frctnl.biz

`vercel.json` allows the page to be embedded only on frctnl.biz and www.frctnl.biz. Example:

```html
<iframe src="https://cash.frctnl.biz/" title="Cash conversion cycle illustrator"
        style="width:100%;min-height:1700px;border:0" loading="lazy"></iframe>
```

If you embed it, link to the full page as well, as the page is long and the iframe height is fixed. Remove the `Content-Security-Policy` header from `vercel.json` if you also want other sites to embed it.

## Things you may want to edit (all in `index.html`)

- **Booking link and email:** search for `calendar.google.com` and `hello@frctnl.biz`.
- **Benchmark ranges:** search for `var SECTORS`. Debtor-day ranges are informed by Novuna Business Cash Flow payment-time data (May 2025, updated March 2026). The other ranges are rules of thumb.
- **Example figures:** search for `var EX`.
- **Privacy policy:** the footer currently points to frctnl.biz. Replace it with your privacy policy URL when you have one.

## Optional extras

- **Social sharing image:** add a 1200x630 image and an `og:image` meta tag with its full URL.
- **Analytics:** a privacy-friendly option such as Vercel Web Analytics or Plausible avoids a cookie banner. If you add any analytics, update the privacy statement in the footer, which currently says nothing is stored.
