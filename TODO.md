# To-do

## How we work
1. `git pull` before you start.
2. Tick only the items **in your own section** (`- [ ]` → `- [x]`), in the same commit as the work.
3. Commit with your own GitHub account (`git config user.email`).
4. Keep the repository lean: only README, TODO, code and the deliverable PDFs.

---

## Milestone 1 · Design and architecture
Screens are in the Figma file **FBD · Screens** (Cover, Mockups, Wireframes, Prototype pages); components are in the **FBD · Design System** library.

**Screens:** S1 Create club · S2 Crest editor · S3 Home (Play) · S4 Keeper boosts · S5 Matchmaking · S6 Draft (+ 6b/6c/6d) · S7 Plan · S8 Match commentary · S9 Penalties and result · T1 Club · T2 Matches · T3 Rules

### K1 · Design language · Owner: Kadir Burak Semerci
- [x] K1.1 · Colour palette and typography
- [x] K1.2 · Figma library (FBD · Design System, published)
- [x] K1.3 · `docs/design-justification.pdf`
- [x] K1.4 · Mockups: S3, S6 (+3 states), S7, S8, S9
- [x] K1.5 · Wireframes: T1 Club, T2 Matches, T3 Rules

### K2 · User flow + onboarding screens · Owner: İlayda Sokur
- [x] K2.1 · `docs/user-flow.pdf` (with decision points)
- [x] K2.2 · Mockups: S1, S2
- [x] K2.3 · Wireframes: S1, S2, S3

### K3 · Keeper + matchmaking · Owner: Yakup Akarsu
- [x] K3.1 · Mockups: S4, S5 (searching / opponent found)
- [x] K3.2 · Wireframes: S4, S5, S6

### K4 · Tabs · Owner: Behlül Kendirli
- [x] K4.1 · Mockups: T1 Club, T2 Matches, T3 Rules
- [x] K4.2 · Wireframes: S7, S8, S9

### K5 · Architecture + prototype + submission · Owner: Emre Şahin Atak
- [x] K5.1 · `docs/architecture-and-protocols.pdf` (MVVM, interfaces, protocols, layer and sequence diagrams)
- [x] K5.2 · Figma prototype (S1 → S2 → S3 → S5 → S6 → S7 → S8 → S9 → S3, tabs)
- [x] K5.3 · README: wireframe and prototype links, roles table

---

## Code: shared setup (after Milestone 1)
- [x] O1 · GitHub repository created, teammates added as collaborators
- [x] O2 · `flutter create`, folder structure, `.gitignore`, `analysis_options.yaml` (Kadir Burak, Flutter 3.47.9)
- [ ] O3 · `main` branch protected, 1 approval required on pull requests (E)
- [ ] O4 · Draft model classes on `main` so everyone can start with fake data (A)
- [ ] O5 · Everyone has a clean `flutter doctor` and has run the app on their own device (each person ticks their own box)
  - [ ] A · [ ] B · [ ] C · [ ] D · [ ] E

---

## A · Game core (`lib/core/`) · Owner: ______
- [ ] A1 · Models: `PlayerCard`, `Position`, `PlayStyle`, `Team`, `Formation`, `Tactic` (+ `fromJson` / `toJson`)
- [ ] A2 · Fictional player data: `assets/data/players.json`, 150–200 players (name, position, style, overall, DEF, ATK, PAS)
- [ ] A3 · Pool generator: 12 cards, varying position mix, 2–3 stars / 5–6 mid / 3–4 low; reproducible with a seed
- [ ] A4 · Auction engine (pure Dart, clock injected): 3 s opener window, 5 s window that resets on every bid, the last bidder cannot bid twice in a row, an unopened card goes free to the opener
- [ ] A5 · Slot and balance rules: once a squad has 6 cards the rest go to the other side; no bid without enough coins
- [ ] A6 · Unit tests: every edge case of A3–A5
- [ ] A7 · Keeper model and the list of 20 boosts (name, effect, unlock condition)

## B · Simulation (`lib/core/sim/`) · Owner: ______
- [ ] B1 · Position penalty table (natural 0, neighbour −3, one line away −8, two lines away −15) + tests
- [ ] B2 · Chemistry (0–3 per player, 0 to +4 for the team) + tests
- [ ] B3 · Tactic matchup (Press > Possession > Counter > Press, ±1.5) + tests
- [ ] B4 · Team score function (using A's models)
- [ ] B5 · Poisson score generation (μ = 1.6, β = 0.115), reproducible with a seed
- [ ] B6 · Penalty shootout (ATK + keeper boosts)
- [ ] B7 · Calibration test: over 10,000 matches Δ=5 → 70 % ± 2, Δ=1 → 54 % ± 2
- [ ] B8 · Narration generator: minute-by-minute events (goal, chance, save, card) + English text templates (at least 40)

## C · Draft and match screens (`lib/features/draft/`, `lib/features/match/`) · Owner: ______
- [ ] C1 · Player card widget (overall, position, style, DEF / ATK / PAS)
- [ ] C2 · Draft screen skeleton: card in the centre, both teams' balances and signed cards
- [ ] C3 · Bid buttons (+1, +5, custom amount) and countdown bar (3 s / 5 s)
- [ ] C4 · Animation of the card moving to the winner when bidding closes
- [ ] C5 · Match screen: minute timeline, commentary feed, live score
- [ ] C6 · Penalty screen and match summary
- [ ] C7 · Widget tests (card, countdown)

## D · Club identity and plan (`lib/features/team/`, `lib/features/plan/`) · Owner: ______
- [ ] D1 · Create club: name, code, validation (length, profanity, real club names blocked)
- [ ] D2 · Crest editor: shape, pattern, two colours, icon, text; live preview with `CustomPainter`; saved as JSON
- [ ] D3 · Crest parts: shapes, patterns, icons (as in the design system)
- [ ] D4 · Plan screen: formation choice (2-3-1, 3-2-1, 2-2-2, 3-1-2)
- [ ] D5 · Drag players onto positions; show position penalty and chemistry live (B's functions)
- [ ] D6 · Tactic choice and plan countdown; opponent's players visible, formation hidden
- [ ] D7 · Keeper screen: pick 3 boosts

## E · Online and app shell (`lib/app/`, `lib/services/`, `functions/`) · Owner: ______
- [ ] E1 · Navigation and theme (launch → club → matchmaking → draft → plan → match → result)
- [ ] E2 · `GameService` interface + fake (local) implementation so everyone can test without the backend
- [ ] E3 · Firebase project, anonymous sign-in, saving the club profile
- [ ] E4 · Matchmaking queue and room creation (Firestore)
- [ ] E5 · Server-side bid validation (Cloud Functions): timer, balance, no double bid, card ownership
- [ ] E6 · Run the simulation on the server and write the result for both players (no cheating)
- [ ] E7 · Disconnects: automatic pass when the timer ends; a player who leaves the match loses
- [ ] E8 · Bot opponent when nobody is found (simple bidding strategy using A4 and B)

---

## Later deliverables
- [ ] Final presentation and demo video
