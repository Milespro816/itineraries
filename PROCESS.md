# Itinerary Workflow

This repo is the public-facing itinerary layer. Use it for polished, share-safe HTML pages and stable links. Keep private trip data in LifeOS/Obsidian. Even "unlisted" pages in this repo are public-by-link.

## Canonical surfaces

| Surface | File/path | Purpose |
|---|---|---|
| Unlisted itinerary index | `index.html` | Vic-facing click-through list of active, planning, and archived trips; still public-by-link |
| Public trips page | `menu.html` | Shareable list of only the trips that are safe for others to see |
| Current trip alias target | `next/index.html` | Stable backend route for `bit.ly/vic-next`; rotate this file, not Bitly |
| Trip HTML page | `<trip-slug>/index.html` | Mobile-first trip guide or planning page |
| Private system of record | LifeOS/Obsidian | Confirmations, driver phone numbers, costs, sensitive logistics |

## Standard trip folder pattern

Folder roles:

| Role | Location | Notes |
|---|---|---|
| Pre-trip planning | LifeOS `10-Calendar/Travel/` and `20-Projects/` | Private working notes, tasks, costs, contacts, open decisions |
| Public page | This repo, `<trip-slug>/index.html` | Sanitized HTML for sharing or showing |
| Private page/data | LifeOS `.md` files only | Not hosted; includes confirmations, driver phone numbers, and private logistics |
| Archive | Remove from `menu.html`; keep or move to Archived in `index.html` | Old pages can remain available but should not be promoted |

Create one folder per hosted trip:

```text
<trip-slug>/
  index.html
```

Examples:

```text
milwaukee-aug6/index.html
ireland-2026/index.html
las-vegas-2026/index.html
```

Only add supporting files if the trip truly needs them. Prefer one self-contained `index.html`.

## Public vs. private rule

Treat every GitHub Pages URL as public-by-link. Do not put sensitive travel data in hosted HTML.

Safe for public or semi-public HTML:

- City, broad dates, trip vibe
- Public restaurant/activity/venue details
- High-level timing and meeting plans
- Hotel name or general lodging area when useful
- Curated recommendations and logistics notes

Keep private in LifeOS/Obsidian:

- Confirmation numbers and record locators
- Ticket barcodes, QR codes, reservation IDs
- Exact lodging address when private residence/Airbnb
- Driver phone numbers and direct contact info
- Loyalty numbers, payment info, personal identifiers
- Home-away details that imply the house is empty

## LifeOS private planning files

For each significant trip, maintain a LifeOS trip note and, when needed, a project note.

Recommended private locations:

```text
/Users/vicmiles/Obsidian/LifeOS/10-Calendar/Travel/<Trip Name Year>.md
/Users/vicmiles/Obsidian/LifeOS/20-Projects/<Trip Name Year>/<Trip Name Year> Project.md
```

Use the project `.md` for operational data Vic may need later:

- Booking confirmations
- Driver name and phone number
- Vendor contacts
- Private costs
- Open decisions
- Internal notes that should not be published

Use a task/action `.md` when the trip has multiple moving parts:

```text
/Users/vicmiles/Obsidian/LifeOS/20-Projects/<Trip Name Year>/<trip-slug>-actions.md
```

Open tasks should use checkboxes:

```markdown
- [ ] Book airport transfer
- [ ] Confirm dinner reservation window
- [ ] Move trip from planning to public menu when sanitized
```

## Travel preferences and drivers

Before recommending flights, hotels, restaurants, or ground transport, check:

- [[Travel Preferences]]
- [[Drivers & Car Services]]

Ground transport rule:

1. Prefer a private driver/car service when the city has a known driver or the trip has meaningful logistics.
2. Put the driver name, phone number, rate, and booking notes in the private LifeOS project `.md`.
3. In public HTML, say only something like "private transfer planned" or "driver arranged" if needed.
4. If a new driver is found, add them to [[Drivers & Car Services]] after the trip note is updated.

## Publishing workflow

1. Build or update the private LifeOS trip/project note first.
2. Create or update the sanitized hosted trip page in `<trip-slug>/index.html`.
3. Add the trip to `index.html` as Active or Planning.
4. Add the trip to `menu.html` only when it is safe to share.
5. Point `next/index.html` to the current trip when it becomes the active "next" trip.
6. After the trip, remove it from `menu.html`, move it to Archived in `index.html`, and rotate `/next/` to the next active trip.

## Decommissioning a trip page

Vic decides when a trip is no longer active. The itinerary agent handles the repo edits when asked to "decommission," "archive," or "retire" a trip.

Default decommissioning means **delist and archive, not delete**:

1. Remove the trip card from `menu.html` so it no longer appears on the public Trip Pages menu.
2. Move the trip from Active or Planning to Archived in `index.html`.
3. If `next/index.html` points to that trip, rotate `/next/` to the new current trip before publishing.
4. Leave the trip folder in place unless Vic explicitly asks to delete it or the page contains sensitive data that should not remain hosted.
5. If the LifeOS project/action note has open publishing tasks, mark them resolved or add a note that the page was archived.
6. Verify the public surfaces after publishing: `menu.html`, `index.html`, and `/next/`.

Deletion is a separate action. Only delete a hosted trip folder when Vic explicitly asks for removal or when the page should come down for privacy/security reasons.

## Link conventions

Only create Bitly shortcuts for shareable or rotating public surfaces. The unlisted internal itinerary index does not need a vanity link; bookmark the raw GitHub Pages URL if needed.

Recommended Bitly targets:

| Bitly | Target |
|---|---|
| `bit.ly/vic-trips` | `https://milespro816.github.io/itineraries/menu.html` |
| `bit.ly/vic-next` | `https://milespro816.github.io/itineraries/next/` |

Do not edit the Bitly target for `vic-next` during normal operations. Rotate the backend by editing `next/index.html`.

## Page tone

Hosted pages are for general guidance and showing off the experience:

- Mobile-first
- Dark mode
- Clean, minimal UI
- Specific recommendations, not generic travel filler
- Costs surfaced at a useful level, but not private booking detail
- No secrets, no tokens, no private confirmation artifacts

## Weather in day headers

When a trip is inside the reliable forecast window, put the current daily forecast in each day header using the compact pill format:

```text
☁️ 78°/65° 30%
```

Use high/low temperature plus rain chance. Keep it short enough for mobile. If the trip is too far out or weather is unavailable, show `Forecast pending` rather than guessing.

## Printable itinerary pages

Hosted trip pages should support printing from the same URL. Prefer a small `Print itinerary` button near the hero and an `@media print` stylesheet over creating a separate print-only page. The print view should use white background, dark text, simplified borders, hidden decorative/footer clutter, and avoid page breaks inside day cards.
