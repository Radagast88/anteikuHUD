# anteikuHUD — feature overview

**HUD statistics for Broken Ranks**: an overlay on top of the game that shows farming statistics, expenses, goals and events in real time. All data is stored locally in an SQLite database — history accumulates between launches.

[Русский](README.md) · **English** · [Polski](README.pl.md)

---

## 1. Capture and game connection

- **Network packet capture** via Npcap — the program sees game events in real time (fights, loot, etc.).
- **Capture device selection** (menu "Capture device…") — if traffic goes through VPN or another network adapter, you can point it to the right one; VPN adapters are marked with a badge in the list.
- **Switching capture device** — the program restarts correctly.
- Packet capture requires running **as administrator** (mandatory on first launch).

## 2. Main HUD window

- **Live session and fight statistics** — shards, psycho experience, gold, essences.
- **Loot** — dropped items tracking with value calculation (including the +30% inhibitor bonus).
- **"Expenses" line** — session spending (purchases, entry fees, NPC operations).
- **Rare items counter** — "mine/others" rares, sets, epics.
- **Rare streaks** — streak statistics.
- **Rare drop sound** — separate sound files for personal and party drops, volume control; the "Play (test)" button in the "Rare sound" menu lets you check the selected mp3 at the current volume without waiting for a rare drop.
- **Location rating** — shards/psycho/gold per hour for instances.
- **Goals with progress bars** — shard/psycho/gold goals with progress; set a goal by right-clicking the "Rating" line in the main window.
- **Display settings** of the main window: fonts and sizes, opacity, colors, row order.
- **Hotkeys:**
  - `Ctrl+F2` — hide/show HUD;
  - `Ctrl+F3` — hide/show event timers (they automatically appear 15 minutes before the start, even when hidden).
- The HUD window is visible **only above the active game window** (attached to BrokenRanks.exe); auto-collapse and quick expand are supported.

<img src="images/hud.png" alt="Main HUD window" width="347">

## 3. Statistics windows

Windows with period filters: **today, 24 hours, 7/30 days, game week** (starts Monday 00:00) and **game month** (starts the 1st at 00:00) — by Polish (server) time, plus character filters.

- **Statistics** — rares, artifacts, no-rare streaks, no-rare streaks per boss.
- **Analytics** — instance statistics. Tabs:
  - **Summary** — overall instance statistics;
  - **Runs** — what dropped and from where, per instance;
  - **Total** — loot for time periods;
  - **Boss fees** — actual payments for boss entries;
  - **Arena** — arena statistics and entry fees by level.

<img src="images/stats.png" alt="Statistics window" width="498">

<img src="images/analytics.png" alt="Analytics window" width="735">

## 4. Goals and progress

- **Goal progress bars** — a separate window with a bar for each goal.
- **Live goal: desired item set** — set a list of items and the HUD will hint what has already dropped/collected; item selection via a picker window.
- **Goal ETA** — estimated time to reach the goal; for limited locations — a calendar deadline; respects the rare chance cap.
- Goals can be set for shards, psycho, gold and item sets.

<img src="images/goals.png" alt="Goal progress bars" width="446">

## 5. Storage

- **Chest viewer** — contents of all storage chests with icons.
- **"All storages" view** — a common list with an "All" highlight.
- **Tiles** of items with icons (equipment — from packet fields), chest number in the tile corner, bound orb icons (all 10 tiers), number under the chest number.
- **Filters and categories** — search (including without apostrophes), "Bound" checkbox, golden border for the selection, gold and platinum icons.
- Items outside combat are shown as well ("+N" icon for incoming items).

<img src="images/storage.png" alt="Storage" width="381">

## 6. Assembly

- **"Assembly" window** — what can already be combined from chest contents (drifts, orbs, synergistics) by the game rules: drifts compared by size, orbs grouped by level category, synergistics summarized by rank.
- **Tile view** with names from the packet, page-by-page switching.
- "Synergistics" tab — composition info by ranks.

<img src="images/assembly.png" alt="Assembly window" width="381">

## 7. Favorites and notifications

- **Favorites** — mark valuable items, orbs and drifts, equipment for visual notification when looted.
- **Popup notifications** — loot/expense icons appear to the right of the HUD header on a transparent background; icon size, opacity and display time are adjustable.

<img src="images/notifications.png" alt="Favorites and notifications" width="440">

## 8. Events

- **Event selection** — choose which events to show; requires opening the map in the game.
- **Event timers** — round timers on screen (appear 15 minutes before the start, auto-extend for Hawk/Wendigo).
- **Display** — standard: text; experimental: round icons with visual timer countdown like on the in-game map.
- **Screen edge snapping** and mirror layout (for multiple monitors); circle size is remembered.

<img src="images/events.png" alt="Event timers" width="420">

## 9. Data and import

- **Import from BrokenHud** — migrate sessions from a third-party tool.
- **Import of our database** and the **"Merge characters"** window — merge character statistics.

## 10. Interface and languages

- **Languages**: Russian, English, Polish (language switch requires a restart).
- **Window themes** — dark-gold context menus, unified list and scrollbar styles.
- **Display settings** — font and text sizes, window opacity, item display, melt/break settings.
- Links to useful resources in the main menu.

---

## System requirements

- **Windows 10/11**
- **Npcap** (network packet capture driver) — download at [npcap.com](https://npcap.com/)
- .NET is not required — the runtime is bundled into the installer

## Installation and launch

1. Download `anteikuHUD_setup.exe` from the **Releases** page.
2. Run the installer (installs to the user folder, no administrator rights needed).
3. Launch anteikuHUD and, if necessary, right-click → "Run as administrator".
4. After the HUD starts, launch **Broken Ranks** and log in as a character.

## Status

The project is under active development. Changes and minor inconsistencies are possible.
The source code is not published.
