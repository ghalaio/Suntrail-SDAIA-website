# SECURITY_RULES.md

Security and data-handling rules for the Suntrail app.

---

## Search Input Handling

- Never insert the raw search box value into the page as HTML — use it only for plain-text comparison.
- Trim and lowercase the search term before matching it against place names, tags, and descriptions.
- An empty search field must show all results for the selected category, not an error or a blank grid.
- Treat the search field strictly as text — it must never be evaluated as code, a template, or an expression.

---

## Booking & External Links

- Every "Book Now," "Reserve," and "Get Tickets" button must open in a new tab — never replace the current page.
- All outbound links must use `rel="noopener"` so the destination site cannot access the original window.
- Only link out to the approved domains for this project: Booking.com, OpenTable, Viator, and Google Maps/Search.
- Do not auto-redirect a user to any booking site without a direct click from them.

---

## Favorites & Local Storage

- Only store the minimum needed to display a favorite: place id, name, category, price, image seed, and city.
- Never store personal information — name, email, location, or payment details — in `localStorage`. Suntrail does not collect any.
- If a saved favorite's id no longer exists in the dataset, drop it silently instead of rendering a broken card.
- "Clear all" must require a deliberate click on a visible button — it must never fire automatically.

---

## Place & Review Data Integrity

- Every place in `data.json` must have a working `bookingUrl` and `mapUrl` before it ships.
- Ratings must stay within the 3.9–5.0 range used across the dataset — no negative or out-of-range values.
- Review counts and "days ago" values must always be generated as positive integers.
- All place names, addresses, and reviewer names must remain clearly fictional demo content — never a real, identifiable business or person.

---

## Images & External Assets

- Only load images and fonts from public, keyless sources — Picsum Photos and Google Fonts. No paid or authenticated API without a proper key setup first.
- Every place image must have a descriptive `alt` attribute, both for accessibility and to fail gracefully if the image doesn't load.
- No API key, token, or credential may ever be written into the HTML, JS, or data files — including "free tier" keys.

---

## General

- Suntrail has no backend and no server — nothing typed or saved by a user should ever be transmitted or logged anywhere.
- Any future addition of a real API, accounts, or payments requires a new security pass before it ships — the rules above are for the current, front-end-only version.
