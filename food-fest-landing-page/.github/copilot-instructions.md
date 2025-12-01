## Quick orientation — Food Fest landing (Vue 3 + Vite)

Short summary
- Small single-page Vue 3 + Vite app that displays ticket tiers as cards.
- App entry: `src/main.js` → `App.vue` (renders tickets) → `src/components/TicketCard.vue` (per-card UI).

Files you should read first
- `src/App.vue` — holds the in-memory `tickets` array and the interaction logic (sorting, favouriting).
- `src/components/TicketCard.vue` — per-ticket card component used by `App.vue`.
- `src/style.css` — shared CSS (grid + card styles). Components may include scoped CSS too.

Current, discoverable contract (must be accurate)
 - Ticket shape used by `App.vue`:
   - name (string), price (number), image (string, optional), benefits (string[]), featured (boolean), favourited (boolean)
 - Component contract (how `TicketCard` and `App.vue` interact):
   - Props: `tier` (object) — see shape above.
   - Emits: `toggle-fav` (payload: the tier object). App.vue handles this in `toggleFavourite` and persists favourited state to localStorage under key `foodfest:favs`.

Why this matters for automated edits
 - Keep the prop names and emitted events stable: App.vue currently expects `tier` and `toggle-fav`.

Quick workflow notes & helpful commands
- Start dev server (inside project folder):
   - Windows PowerShell (no policy change): `npm.cmd run dev` or from workspace root `npm run dev` (forwards to the inner project)
   - Unix / WSL: `npm run dev` inside the project folder
- Build: `npm run build`

If you edit the card component make small, reversible changes and run the dev server to verify the UI and HMR messages in the browser console.

If anything here is unclear or you'd like the instructions expanded (tests, accessibility checks, component patterns), tell me which part to expand.
