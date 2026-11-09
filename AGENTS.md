# Agent guide — Football Blind Draft

Instructions for AI coding agents (Claude Code, Codex, Copilot, Cursor…) used by our team members. Reply to the user in the language they write in (usually Turkish).

## The project
- MTM4681 Mobile Programming semester project, 5-person team (see `README.md`).
- Real-time 1v1 football game: 12 fictional cards revealed blind, open-auction bidding, 6-player squads, planning phase, simulated match narrated minute by minute.
- **`docs/TASARIM.md` is the source of truth for game rules and formulas.** Do not invent or change rules; if something is missing or contradictory, ask the user to raise it with the team.
- **`TODO.md` is the task list.** Each section has an owner.

## Current phase
- **Milestone 1 (due 12 Nov 2026, 23:00): design and architecture only, no app code required.** Deliverables: design justification PDF, user flow PDF, architecture & protocols PDF, Figma wireframes / mockups / prototype, README with Figma links. Deliverables are in English.
- App code (sections A–E in `TODO.md`) starts after Milestone 1.

## Work only on your user's section
- First find out which section your user owns (ask if `TODO.md` does not say). Only edit files of that section.
- Each member must write and understand their own part; the instructor reviews commit history per person. Help your user understand any code before it is committed.
- Need a change in someone else's section? Tell your user to coordinate with that owner instead of editing it.

## Tech
- Flutter 3.47.9 or newer stable, Dart. Pattern: **MVVM** (Model = `lib/core`, View = screens, ViewModel = per-screen `ChangeNotifier`, services behind interfaces).
- Folder map: `lib/app` (navigation, theme) · `lib/core` (models, auction engine; pure Dart) · `lib/core/sim` (team score, Poisson match, narration) · `lib/features/{draft,match,team,plan}` · `lib/services` (`GameService` interface, fake + Firebase implementations).
- Keep game logic in `lib/core` free of Flutter imports so it can be unit-tested.
- Before every commit: `flutter analyze` (no issues) and `flutter test` (all pass).

## Git workflow
1. `git pull` before starting.
2. Commits must be authored by your user's own GitHub account: check `git config user.email` matches their GitHub email or their `ID+username@users.noreply.github.com` address.
3. Ask your user before committing or pushing.
4. Work on a branch (`name/short-topic`), open a pull request, one teammate reviews. **Merge with a normal merge, never squash** someone else's PR.
5. Local commits that were never pushed may be squashed into one before pushing. **Never rewrite history that is already on GitHub** (no force push).
6. Tick the finished `TODO.md` item (`- [ ]` → `- [x]`) in the same commit as the work. Only tick your user's own items.
7. AI-assisted commits end with a `Co-Authored-By:` trailer naming the assistant (see the AI assistance note in `README.md`).

## Never commit
- Secrets: `.env` files, API keys, tokens, passwords, Firebase service-account keys, keystores / `key.properties`.
- Real football data: real player or club names, logos, kits, photos, or FIFA/EA ratings. All players are **fictional**.
- Build output (`build/`, already in `.gitignore`).
