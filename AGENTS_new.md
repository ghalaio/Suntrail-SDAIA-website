# AGENTS.md

Engineering rules and instructions for the AI assistant (Claude, via Cowork) working on the Suntrail app.

---

## City & Category Data

- Every city in `data.json` must include all five categories: Hotels, Restaurants, Cafes, Cinemas, Entertainment.
- Each category for each city must contain at least 5 places — never fewer.
- Do not duplicate a place name within the same city and category.
- New cities must follow the existing city object shape: `id`, `name`, `country`, `blurb`, `places`.

---

## Visual Theme

- All new UI elements must use the existing color variables (`--sun`, `--amber`, `--orange`, `--deep-orange`, `--ember`, `--cream`, `--brown`) — never introduce a new hex color outside this palette.
- Headings use Poppins; body text uses Nunito — keep this pairing consistent in any new section.
- Buttons and badges must reuse the existing orange-to-ember gradient style, not a flat single color.
- Keep the sunset/warm tone consistent across the app, the PRD, and all project documentation.

---

## Cards & Modal

- Every place card must show: image, name, price tier, star rating, review count, a short blurb, and at least two tags.
- The place detail modal must always include a working booking link, a map link, and the reviews list — never ship a modal missing one of these.
- The "Top Rated" badge must only appear on the single highest-rated place per category per city, never on more than one.

---

## Search, Sort & Filter

- Search must filter within the currently selected city and category only — never across cities.
- Sorting must never mutate the original dataset order — always sort a copy.
- If a search returns zero results, show the existing empty-state message rather than a blank grid.

---

## Favorites / My Trip

- The favorite (heart) icon must reflect its saved state immediately after clicking, with no page reload required.
- The trip drawer's estimated cost level must recalculate every time a place is added or removed.
- "Clear all" must require a visible confirmation action — never trigger from a single accidental click.

---

## Data Generation Script

- `generate_data.py` is the single source of truth for demo data — never hand-edit `data.json` directly.
- Random generation must use a fixed seed so the dataset stays reproducible between runs.
- Price tiers, ratings, and review counts must stay within the ranges already defined in the script.

---

## Documentation

- Keep `README.md`, `AGENTS.md`, and `SECURITY_RULES.md` updated whenever a feature they describe changes.
- Any new external service (API, font, image source) must be added to the "Technologies & AI Tools Used" section of the README before it's used.
- Never fabricate real, identifiable business names — all place data stays clearly fictional/demo content.
