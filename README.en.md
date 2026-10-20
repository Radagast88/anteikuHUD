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
- **HUD display:** the overlay can be shown **only above the active game window** (set in the settings); auto-collapse and quick expand are supported.

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

## 5. Deposit

- **Chest viewer** — contents of all chests in the Deposit with icons (refreshed when you enter the Deposit in game, each chest separately).
- **"All deposits" view** — a common list with an "All" highlight.
- **Tiles** of items with icons (equipment — from packet fields), chest number in the tile corner, bound orb icons, number under the chest number.
- **Filters and categories** — search (including without apostrophes), "Bound" checkbox, golden border for the selection, gold and platinum icons.
- Items outside combat are shown as well ("+N" icon for incoming items).

<img src="images/storage.png" alt="Deposit" width="381">

## 6. Assembly

- **"Assembly" window** — what can already be combined from chest contents (drifts, orbs, synergistics) by the game rules: drifts compared by size, orbs grouped by level category, synergistics summarized by rank.
- **Tile view** with names from the packet, page-by-page switching.
- "Synergistics" tab — composition info by ranks.

<img src="images/assembly.png" alt="Assembly window" width="381">

## 7. Favorites and notifications

- **Favorites** — mark valuable items, orbs and drifts, equipment for visual notification when looted.
- **Popup notifications** — loot/expense icons appear to the right of the HUD header on a transparent background; icon size, opacity and display time are adjustable.

<img src="images/notifications.png" alt="Favorites and notifications" width="440">

## 8. Champion tracking (respawn tracker)

- **Champion catalogue** — every Broken Ranks champion with its respawn time, grouped by
  location; the window has three tabs: **"Running"**, **"Favorites"** and **"All"**.
- **Respawn timers** — click a tile to start a countdown to the champion's respawn. The
  countdown uses the time from the catalogue (for champions with a range — the minimum).
- **"Running" tab** — only live timers: both those still counting down to respawn and those
  whose respawn has already happened (the green window). The list updates itself as time passes.
- **Green respawn window** — when the countdown hits zero, the tile switches to a green
  "RESPAWN M:SS" counter: the respawn is already possible and lasts that long (the difference
  between the minimum and maximum time). When the window closes, the timer resets.
- **"Respawn soon" warning** — 5 minutes before the champion respawns.
- **Badges in the notification bar by the HUD** — champion readiness is shown as an icon next
  to the main window; clicking the badge opens the tracker window.
- **Favorites** — the ★ star on a tile adds the champion to favorites; when such a champion is
  killed, a "Start timer?" bubble pops up — the timer starts with a single click.
- **Doubled champions** — Tomb and Nixoflower live in a location as two copies: each gets two
  tiles with separate timers.
- **Tile tooltip** — the respawn time and a hint of how long the champion stays before vanishing.
- **Multiple monitors** — timers and badges work correctly at any HUD position.

<img src="images/champ_tracker.png" alt="Champion tracking window" width="520">

## 9. Chat

- **In-game chat tracking** — the "Chats" window (menu "Chats") records game messages in
  real time, searches for keywords and shows notifications.
- **Main switch** — "Record and process chat"; the chat is **off** by default. While the
  checkbox is off, messages are not saved, not checked for trigger words and produce no
  notifications. The state is remembered between launches.
- **Message log** — table "Time · Nick · Message", newest on top; your nick mention is
  highlighted in gold, a fired trigger in orange. Auto-scroll, search by nick/text,
  right-click copy (nick / message / all), clear the file and open the log in an editor.
- **Character filter** — show only checked characters; **ignore** — hide the selected ones
  from the log and mute their notifications (messages are still written to the file).
- **Trigger words** — a list of keywords that pop up a notification: add, edit in place
  (double-click), delete and an **enable/disable checkbox** — unchecked temporarily turns
  the search off, the word stays in the list and is dimmed.
- **Fuzzy search** — catches inflections and typos: the first letter must match, an exact
  match from the start of the word, otherwise 1–2 typos are allowed (words shorter than
  4 letters — exact only; triggers not starting with a letter — exact match). A word
  combination fires when all words are present in any order.
- **Notifications** — a popup toast in the bottom-right corner (7 seconds) and a sticky
  unread badge with a counter in the notification bar until the "Chats" window is opened.
- **Log file** — `chat_log.txt` next to the program, UTF-8 without BOM; the last 3000
  messages are kept in memory, all of them in the file ("Full history" checkbox reads the
  file for all days).
- **Localization** — Russian, English, Polish.

<img src="images/chat.png" alt="Chats window" width="520">

## 10. Events

- **Event selection** — choose which events to show; requires opening the map in the game.
- **Event timers** — round timers on screen (appear 15 minutes before the start, auto-extend for Hawk/Wendigo).
- **Display** — standard: text; experimental: round icons with visual timer countdown like on the in-game map.
- **Screen edge snapping** and mirror layout (for multiple monitors); circle size is remembered.

<img src="images/events.png" alt="Event timers" width="420">

## 11. Data and import

- **Import from BrokenHud** — migrate sessions from a third-party tool.
- **Import of our database** and the **"Merge characters"** window — merge character statistics.

## 12. Interface and languages

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
