# Copilot Instructions

Before modifying itinerary pages, read `PROCESS.md`.

This repo is the hosted itinerary layer. Treat every GitHub Pages page as public-by-link, including unlisted pages. Keep all hosted HTML sanitized and share-safe. Private confirmations, record locators, driver phone numbers, booking details, exact private lodging addresses, and sensitive logistics belong in LifeOS/Obsidian, not hosted HTML.

Use these repo surfaces consistently:

- `index.html` is the unlisted itinerary index; it is not private.
- `menu.html` is the public Trip Pages menu.
- `next/index.html` is the backend target for `bit.ly/vic-next`; rotate this file instead of editing Bitly.
- `<trip-slug>/index.html` is the standard folder pattern for each trip page.

Before recommending travel logistics, check the LifeOS notes `[[Travel Preferences]]` and `[[Drivers & Car Services]]`. If a driver is selected, put the driver name, phone number, rate, and booking notes in the private LifeOS project `.md`; public HTML should only mention sanitized transport status when useful.
