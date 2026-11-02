# EMT Canada — Rebuilt Site (Deployment Package)

This package contains the rebuilt EMT Canada site: 8 static HTML pages, a logo asset, and the SEO files search engines look for. No build step, no dependencies — it's ready to upload as-is.

## What's in here

| File | Page |
|---|---|
| `index.html` | Home |
| `basic-courses.html` | Basic & Intermediate First Aid + CPR/AED |
| `advanced-courses.html` | Wilderness First Aid, Advanced (coming soon) |
| `preparamedicine.html` | Pre-Paramedicine flagship program |
| `corporate-training.html` | Corporate & Industry Training |
| `become-a-provider.html` | Teach Our Courses |
| `about.html` | Meet the Team & Our Philosophy |
| `contact.html` | Contact, provider directory, policies |
| `emt-canada-logo.png` | Logo asset (RGB, optimized) |
| `robots.txt` | Tells search engines they're welcome to crawl everything |
| `sitemap.xml` | Lists all 8 pages for search engines |

## How to deploy

Any static host works since there's no server-side code:

1. **Netlify / Vercel (easiest):** drag the whole folder onto netlify.com/drop, or run `vercel` from inside the folder. Live in under a minute.
2. **GitHub Pages:** push the folder to a repo, enable Pages on the `main` branch.
3. **Existing hosting (cPanel/FTP):** upload all files to your web root (`public_html` or similar) via FTP/SFTP.
4. **Replacing the current Wix site:** Wix doesn't support uploading custom static files directly, so this would mean pointing `emtcanada.ca`'s DNS at new hosting (options 1–3) rather than uploading into Wix itself. Worth a conversation with whoever manages the domain before going further.

Once live, submit `sitemap.xml` in Google Search Console so the new pages get indexed quickly.

## Before this goes live — a short checklist

- **Photography:** every photo slot on the site (hero banners, course cards, team portraits) currently holds a custom-built brand-colored illustration instead of a real photo — this environment can't pull licensed photography or hotlink external images into a deployable file. Each illustration is contextual (a CPR scene for CPR pages, a graduation cap for Preparamedicine, portrait-style avatars for Anna Rose and Jeff Frenette, etc.) so the layout and spacing are already correct — swapping in real photography later is a drop-in change, not a redesign.
- **Logo rendering:** each page embeds the logo as a Base64 data URI directly inside the HTML (fixes a broken-image issue from linking to a sibling file). Production-ready either way, but your dev team may prefer swapping to a normal `<img src="emt-canada-logo.png">` reference once it's hosted at a stable URL, for lighter page weight.
- **Become-a-Provider page:** this page was essentially blank on the live site, so the copy here is a fresh starting draft. Worth a pass from your team to confirm the real specifics before publishing.
- **Policies page (`contact.html#policies`):** intentionally left as an honest placeholder rather than fabricated legal text, since the original page was also empty.
- **Social links:** footer icons point to placeholder root URLs — swap in your actual handles.
- **Contact forms:** visual only for now (demo alert on submit). Wire to email/CRM via Netlify Forms, Formspree, or your backend.
- **External link:** the Preparamedicine registration button still points to the Kitchener First Aid partner page from the original site — confirm that's still correct.

## Design approach

This rebuild is intentionally close to the original emtcanada.ca: clean white background, Montserrat headings + Open Sans body (matching the original's sans-serif system), a 4-box course navigation grid mirroring the homepage layout, a client-logo trust strip, and the philosophy copy pulled directly from the live site. Red is used the way the original uses it — for buttons, accents, and small highlights — not as large background panels.

## Brand reference

- Red: `#DA251C` — sampled directly from your logo
- Near-black: `#1A1A1A` — sampled directly from your logo
- Headings: Montserrat · Body: Open Sans (both loaded from Google Fonts, no licensing cost) — chosen to match the clean sans-serif system used on the current site

## SEO/AIO already built in

- Unique `<title>` and meta description per page
- `EducationalOrganization` schema sitewide, `Course` schema on course pages, `Person` schema for Jeff Frenette and Anna Rose, `FAQPage` schema matching the visible FAQ accordions word-for-word
- Semantic headings, `sitemap.xml`, and `robots.txt`
