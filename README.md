# Fast MTG
 
A single-page companion app for a fast, casual, dice-free 2-player *Magic: The Gathering* variant. It handles color assignment, deck-building checklists, life totals, and match history — so setup takes seconds and the table stays focused on playing.
 
## Description
 
 Fast MTG is a lightweight, no-install web app built for players who want quick 1v1 Magic games from a shared card pool without a full draft or deckbuild. It randomly assigns each player two non-overlapping colors, walks them through a structured checklist of how many commons/uncommons/rares/multicolor/colorless cards to pull, then switches into a life counter with custom status counters (poison, energy, etc.), a win animation with sound and vibration, and a persistent match history — all in one self-contained HTML file with no backend, no accounts, and no install.
 
## Features
 
- **Color draw** — a shared 5-color (W/U/B/R/G) deck is shuffled and dealt 2 cards to each player, guaranteeing no shared color and no dice rerolls.
- **Deckbuild checklist** — auto-generated per-player pull list (commons, uncommons, rares, colorless, matching multicolor, land reminder) with checkboxes; the duel can't start until every box is checked.
- **Life counter** — large +/- controls per player, starting life is configurable.
- **Custom counters** — add any named counter (poison, energy, experience, etc.) per player, floored at 0.
- **Win detection** — reaching 0 life triggers a win overlay with a chime and a vibration (where supported), and tallies the round in the running score.
- **Match history** — a scrollable log of every round played, showing both players' colors and the winner, newest first.
- **Reset** — a single confirmed action that wipes names, scores, colors, and history and returns to setup.
- **Persistence** — the current match and history are saved to the browser's local storage, so refreshing or reopening the page picks up where you left off.
- **Light/dark aware** — follows the system color scheme automatically.
## The format
 
1. Each player is dealt 2 colors from a shuffled shared 5-color deck (no overlap possible).
2. Each player builds a deck from their color pool:
   - 10 Commons per color
   - 5 Uncommons per color
   - 2 Rares/Mythics per color
   - 4 Colorless cards (2 Common, 1 Uncommon, 1 Rare/Mythic) — split so both players don't need the same physical card
   - 2 Multicolor cards matching their exact color pair
   - Up to 17 lands
3. Play a round with a normal life total (default 20) to 0.
4. Repeat — colors are redrawn each round, so decks change every game.
## Usage
 
Open the app, no installation required:
 
1. Enter both player names and a starting life total.
2. Tap **Draw colors** — colors are dealt automatically.
3. Each player physically pulls the listed cards from their collection and checks them off.
4. Once every box is checked, tap **Start the duel** to open the life counters.
5. Track life and any status counters during the game.
6. When a player hits 0, the win overlay fires — tap **Next round** to redraw colors and go again.
7. Use **History** anytime to review past rounds, or **Reset** to start a fresh match.
## Tech
 
- Single self-contained `.html` file — HTML, CSS, and vanilla JavaScript, no build step, no dependencies.
- State is kept in a single JS object and persisted to `localStorage` (per-device, never uploaded anywhere).
- Sound is generated on the fly with the Web Audio API; vibration uses the standard `navigator.vibrate` API where the device supports it.
