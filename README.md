# Hyderabad rental shortlist

2 and 3 BHK rentals for a family of four in Himayatnagar, Narayanguda, Kachiguda, Ashok Nagar, VST, Gandhi Nagar, Kavadiguda and RTC X Roads, collected from NoBroker, SquareYards and RealEstateIndia on 26 Oct 2026 and rechecked on 27 Oct 2026.

- `docs/report.html`: the detailed shortlist page (open it in a browser). It covers listings whose photos show an Indian-style toilet, clean listings to ask about, the full filterable list, and a checklist for the visit.
- `docs/index.html`: a compact, phone-friendly version with tap filters, a posted-date range, copy buttons (as a message or spreadsheet rows) and saved collections. Collections stay in the browser; turning on sync (Manage → Turn on sync) gives a private link that keeps them the same on other phones and browsers, stored in Supabase.
- `listings.csv`: all 199 listings with rent, deposit, size, floor, water, lift, power backup, owner name, link, whether an Indian-style toilet appears in the photos, and a condition note.

The site is hosted on Vercel at https://rcheck-cyan.vercel.app (project `rcheck`, root directory `docs`, no build step); every push to this branch redeploys it. The same `docs` folder also works with GitHub Pages (Settings → Pages, deploy from this branch's `/docs` folder).

Phone numbers are not included: both sites show them only to logged-in users ("Get Owner Details" on NoBroker, "View Number" on SquareYards).

## Collection sync

Sync uses the `roadfix-hyderabad` Supabase project: one table, `rentals.collection_sync`, reachable only through the `rentals_get_collections` and `rentals_save_collections` functions. A row is keyed by the SHA-256 of the sync code, so the code itself is never stored. Anyone holding a sync link can read and change that link's collections, so share it only with family.
