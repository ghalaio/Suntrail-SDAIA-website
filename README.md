# Suntrail — Find Your Next Favorite Place

Suntrail is a single-page travel companion website. Pick a city, and it shows you the best-rated hotels, restaurants, cafes, cinemas, and entertainment spots in that city — with reviews, tags, and a one-click link to actually book or reserve. It was built as my final project for the SDAIA Academy Vibe Coding course.

---

## 1. Project Overview

I travel (or hope to!) and every time I land somewhere new, I end up with six browser tabs open just trying to find a decent hotel and somewhere good to eat. Suntrail is my attempt at fixing that: one page, one city at a time, with the best spots already sorted to the top.

You pick a city from the home screen, browse by category (Hotels, Restaurants, Cafes, Cinemas, Entertainment), search or sort the results, and click into any place to see photos, star ratings, real-style traveler reviews, the address, and a **Book Now** button that opens the real booking site (Booking.com, OpenTable, Viator, or Google, depending on the category). You can also heart your favorite spots and they'll show up in a **My Trip** side panel that remembers what you saved even after you close the browser.

The whole thing is one self-contained HTML file — no server, no build step, no installs. Open it, and it works.

## 2. Project Structure

```
suntrail/
├── suntrail-travel-guide.html   # The actual app — open this in a browser to run it
├── generate_data.py             # Python script that generates the demo place/review data
├── data.json                    # The generated dataset (169 places across 6 cities)
├── Suntrail_PRD.pdf             # Product Requirements Document
├── README.md                    # This file
├── AGENTS.md                    # Engineering rules the AI assistant followed while building this
└── SECURITY_RULES.md            # Security rules followed, and how they apply to this project
```

Everything the browser needs — HTML, CSS, and JavaScript, plus the data itself — lives inside `suntrail-travel-guide.html`. The `generate_data.py` script and `data.json` file are included so you can see (and regenerate) exactly where the sample data came from.

## 3. Technologies & AI Tools Used

- **HTML5 / CSS3** — layout, theming, and responsive design, using CSS custom properties for the yellow-and-orange color palette
- **Vanilla JavaScript** — all interactivity (filtering, search, sorting, modals, the trip planner) with no external JS framework
- **`localStorage`** — saves the user's favorited places in the browser between visits
- **Python 3** — a small script (`generate_data.py`) that procedurally generates the realistic sample dataset (places, ratings, reviews, addresses, booking links)
- **Google Fonts** (Poppins & Nunito) and **Picsum Photos** — for typography and placeholder photography
- **Claude (Anthropic)**, used inside Cowork mode, as the AI pair-programmer for this entire project — from brainstorming features, to writing the HTML/CSS/JS, to generating this documentation, following the Vibe Coding approach taught in the course
- **ReportLab** (Python) — used to generate the themed PRD PDF

## 4. Installation & Run Instructions

No installation is actually required to use the app — that's the point.

1. Download or clone this repository.
2. Open `suntrail-travel-guide.html` by double-clicking it, or right-click → **Open with** → your browser.
3. That's it — the app runs entirely in the browser, with all data bundled in.

If you want to regenerate the sample data yourself:

```bash
pip install --break-system-packages -r requirements.txt   # only needs the standard library, no packages required
python3 generate_data.py
```

This produces a fresh `data.json`. If you want to update the live app with new data, copy the JSON into the `const DATA = ...` line inside `suntrail-travel-guide.html`.

## 5. How to Use the Application

1. **Pick a city** from the home screen — Paris, Rome, Dubai, New York, Tokyo, or Bali.
2. **Browse categories** using the pill tabs (Hotels, Restaurants, Cafes, Cinemas, Entertainment) or leave it on "All."
3. **Search or sort** using the search box and dropdown (Top Rated, Most Reviewed, Price, Name).
4. **Click any place card** to open its full details — photos, rating, price, address, tags, and traveler reviews.
5. **Click "Book Now"** (or "Reserve," "Get Tickets," depending on the category) to open the real booking page in a new tab.
6. **Click the heart icon** on any card to save it to **My Trip**. Open the trip drawer from the top-right button to see everything you've saved, copy the list, or clear it.
7. **Feeling indecisive?** Hit **Surprise Me** to open a random top pick for the city you're browsing.

## 6. Future Improvements

- Connect to a real, live places API (e.g. Google Places) instead of the curated demo dataset, so ratings and reviews stay current
- Add user accounts so trip lists sync across devices instead of living only in the browser
- Add more cities and let users request a city that isn't listed yet
- Add a simple day-by-day itinerary builder on top of the My Trip list
- Add filters for things like price range, opening hours, or accessibility
- Add real-time availability checking before sending users to the booking link
- Turn it into a proper Progressive Web App (PWA) so it can be "installed" on a phone and used offline

---

### Course Reference

This project was built for the **SDAIA Academy** Vibe Coding course final project.
SDAIA Academy GitHub: [https://github.com/SDAIAAcademy](https://github.com/SDAIAAcademy)
