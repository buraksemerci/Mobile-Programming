# Football Blind Draft

MTM4681 Mobile Programming — Semester Project · Yıldız Technical University · Fall 2026

Repository: https://github.com/buraksemerci/Mobile-Programming

A real-time 1v1 mobile football game. Twelve fictional player cards are revealed one at a time; both players bid on each card without knowing what comes next, each building a six-player squad with a fixed budget. After a timed planning phase (formation, positions, tactics), the match is simulated and narrated minute by minute.

## Team

| Member | GitHub | Milestone 1 role |
|---|---|---|
| Kadir Burak Semerci | [@buraksemerci](https://github.com/buraksemerci) | K1 · Design language & design justification  |
| Behlül Kendirli | [@Behlul-Kendirli](https://github.com/Behlul-Kendirli) | K4 · Tab screens & plan/match/result wireframes |
| Yakup Akarsu | [@yakupakarsu](https://github.com/yakupakarsu) | K3 · Keeper & matchmaking screens |
| İlayda Sokur | [@ilaydasokur0](https://github.com/ilaydasokur0) | K2 · User flow & onboarding screens |
| Emre Şahin Atak | [@emresahinatak](https://github.com/emresahinatak) | K5 · Architecture, prototype & submission |

### AI assistance

Parts of the planning, documentation and design work were done with [Claude Code](https://claude.com/claude-code) (Anthropic) as an assistant. Commits it helped with carry a `Co-Authored-By: Claude` trailer; each team member remains responsible for their own section.

## Milestone 1 — Design & Architecture

| Deliverable | Link |
|---|---|
| Design justification (PDF) | [docs/design-justification.pdf](docs/design-justification.pdf) |
| User flow diagram (PDF) | [docs/user-flow.pdf](docs/user-flow.pdf) |
| Architecture & protocols (PDF) | [docs/architecture-and-protocols.pdf](docs/architecture-and-protocols.pdf) |
| Design system library (Figma) | [FBD · Design System](https://www.figma.com/design/bgRDmCYy631F1EfBLtXsdc) |
| Wireframes (Figma) | [FBD · Screens → Wireframes](https://www.figma.com/design/UUI6I7TsTDcTG6pM34elUJ?node-id=1-2) |
| Mockups (Figma) | [FBD · Screens → Mockups](https://www.figma.com/design/UUI6I7TsTDcTG6pM34elUJ?node-id=0-1) |
| Prototype (Figma) | [Play the prototype](https://www.figma.com/proto/UUI6I7TsTDcTG6pM34elUJ?node-id=62-1525&starting-point-node-id=62%3A1525) |

## Getting started

Requirements: Flutter 3.47.9 or newer (stable), Git, an editor with the Flutter extension (VS Code or Android Studio).

```bash
git clone https://github.com/buraksemerci/Mobile-Programming.git
cd Mobile-Programming
flutter pub get
flutter run
```

## Repository

- `docs/` — Milestone deliverables (PDF)
- `lib/` — Flutter app (MVVM: `app`, `core`, `core/sim`, `features`, `services`)
- `TODO.md` — team task list
