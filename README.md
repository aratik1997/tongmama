# Tong Mama — Game Hub

A small hub of browser-based multiplayer games, built with PHP, vanilla JavaScript, and no build step. Pick a game from the landing page and play — solo, pass-and-play, or online with friends.

**Live structure:** a single [index.html](index.html) landing page links out to each game. Every game is its own standalone repo, pulled in here as a git submodule.

## Games

| Game | Path | Repo | Description |
|---|---|---|---|
| 🏏 **Reflex Cricket** | [`/cricket`](cricket/) | [aratik1997/cricket](https://github.com/aratik1997/cricket) | A millisecond-timing reflex game — hit the stopwatch at the right instant to score runs. Solo vs. computer, same-screen pass-and-play, online multiplayer, or a full single-player World Cup tournament with groups and knockouts. |
| 🎣 **Go Fish** | [`/gofish`](gofish/) | [aratik1997/gofish](https://github.com/aratik1997/gofish) | The classic card game, "Pond Party" style. Ask opponents for cards, collect sets, and see who reels in the most — with in-game chat and a tiebreak mode. |
| 🃏 **Kolshi** | [`/kolshi`](kolshi/) | [aratik1997/callshow](https://github.com/aratik1997/callshow) | A fast multiplayer card game on Yaniv rules. Build a low-value hand, Call or Show at the right moment, and outlast the table. Real-time play over polling, with a turn timer, host controls, and chat. |

More games are added over time — see the "More games coming soon" tile on the hub for what's in the pipeline.

## Tech stack

- **PHP** (PDO) for server-side game logic — no framework, no build step
- **MySQL/MariaDB** (Cricket) and **SQLite** (Go Fish, Kolshi) for persistence
- **Vanilla JavaScript** for interactive gameplay and AJAX polling (real-time sync without WebSockets)
- **Plain HTML/CSS**, each game self-contained in its own folder

## Getting started (XAMPP)

1. Clone this repo (with submodules) into your XAMPP `htdocs` directory as `tongmama`:
   ```bash
   git clone --recurse-submodules https://github.com/aratik1997/tongmama.git
   ```
   Already cloned without `--recurse-submodules`? Run `git submodule update --init` inside the repo.
2. Start **Apache** (and **MySQL**, for Cricket) from the XAMPP control panel.
3. Visit `http://localhost/tongmama/` for the game hub, or jump straight into a game:
   - `http://localhost/tongmama/cricket/`
   - `http://localhost/tongmama/gofish/`
   - `http://localhost/tongmama/kolshi/`

Each game bootstraps its own database/schema automatically on first load. Kolshi requires copying `kolshi/api/config.example.php` to `kolshi/api/config.php` first — see [`kolshi/README.md`](kolshi/README.md) for details. Cricket and Go Fish need no extra setup beyond default XAMPP credentials.

## Project structure

```
index.html      Game hub landing page — pick a game to play
cricket/        Reflex Cricket (PHP + MySQL)     — submodule: https://github.com/aratik1997/cricket
gofish/         Go Fish (PHP + SQLite)           — submodule: https://github.com/aratik1997/gofish
kolshi/         Kolshi / Yaniv (PHP + SQLite)    — submodule: https://github.com/aratik1997/callshow
```

Each game folder has its own README with gameplay rules and implementation details.

## Requirements

- PHP 8.0+ (PDO, SimpleXML, SQLite extensions enabled — all on by default in XAMPP)
- MySQL or MariaDB (for Cricket only)
