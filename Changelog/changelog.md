# ChatGPT JSON Tree Viewer — Changelog

---

## v7.2.0 — 2025-05-05 *(Current)*

### 🆕 New
- **Custom theme color picker** — a rainbow ✦ dot after the preset theme dots opens a live color editing panel. Customize backgrounds, text, accent color, borders, and all four node colors individually. Changes apply instantly across the entire UI.
- **Quick presets in custom panel** — one-click buttons to load any of the 5 named themes as a starting point
- **Reset to defaults** — button inside the custom panel restores all colors to Dark theme defaults
- **Custom theme persists** — all custom colors saved to `localStorage` and restored automatically on every visit

---

## v7.1.0 — 2025-05-05

### 🆕 New
- **Claude new export format** — detects and correctly converts Claude.ai's current export format (`chat_messages[]` with `sender` + `parent_message_uuid`). Branching is fully preserved — regenerated responses appear as real branches in the graph, not a flat chain.
- **Reset confirmation** — clicking Reset (main button, or Reset All / Reset Nodes from the dropdown) now asks for confirmation before moving nodes. Reset View has no confirmation since it doesn't move nodes.
- **Graph image export** — camera button at the bottom of the graph controls. Three formats:
  - **PNG** — current viewport at 2× scale, lossless
  - **JPG** — current viewport, compressed
  - **SVG** — full graph as vector (all nodes, regardless of zoom/pan), editable in Inkscape/Figma/Illustrator

### 🐛 Bug Fixes
- **Claude new format misdetected as Mistral** — both formats use `chat_messages[]`; now distinguished by `sender` field (Claude new) vs `role` field (Mistral)

---

## v7.0.8 — 2025-05-04

### 🐛 Bug Fixes
- **Chunk export re-import showed "unknown format / 0 messages"** — `convToOpenAIFormat` was reading `content.text` directly, missing text from non-OpenAI formats (Claude, DeepSeek, Grok, GLM). Now uses `getNodeText()` which handles all formats, with multiple fallbacks.
- **Corrupt or missing mapping crashed entire chunk export** — conversations with malformed `data.mapping` are now skipped with a console warning rather than aborting the whole export
- **`convToOpenAIFormat` guard** — if a conversation has no `data.mapping`, a minimal valid skeleton is returned instead of throwing an unhandled error

### 📚 Help Guide
- Export All section now documents the chunked export flow, the crash warning, re-import compatibility, and the Settings default

---

## v7.0.7 — 2025-05-04

### 🐛 Bug Fixes
- **File splitter failed on non-array JSON** — worker now handles wrapped objects (`{"conversations":[...]}`), single conversation objects, and BOM-prefixed files before splitting

### 🔄 Changed
- **Large file warning threshold raised to 300 MB** — was 50 MB, which triggered too often for normal use

### 🆕 New
- **"Don't warn again" checkbox** — in the large file warning dialog; checking it before clicking Try or Split permanently disables the warning
- **Large file warning toggle in Settings** — on/off toggle plus threshold slider (50–1000 MB). Turning it off grays the slider; turning it back on restores the previous threshold. Persists across sessions.

---

## v7.0.6 — 2025-05-04

### 🔄 Changed
- **Split & Import is now fully automatic** — the primary action in the split dialog splits the file in a background Web Worker and imports all chunks sequentially without any manual steps. Progress is shown per chunk as each one loads.
- **Download Chunks retained as secondary option** — a separate button lets you download the chunk files for portability or re-import on another machine

---

## v7.0.5 — 2025-05-04

### 🆕 New
- **Large file warning** — selecting a file over 50 MB shows a warning before import with two choices: *Try Import Anyway* or *Split into Chunks First*
- **Import error recovery** — if a large file fails to parse, the split dialog reappears automatically with the same file pre-loaded rather than showing a raw error
- **File splitter (Web Worker)** — splits any oversized JSON array into numbered chunk files in a background thread (UI stays responsive). Choose 50 / 100 / 200 MB per chunk. Downloads files named `export_part1of7_500convs.json`. Import chunks one by one — duplicate handling merges everything correctly
- **Help guide updated** — Loading & Unloading topic now has a Large File Handling section

---

## v7.0.4 — 2025-05-04

### 🆕 New
- **Reset dropdown** — the Reset button now has a `▾` arrow that expands three options:
  - **Reset All** — animates nodes back to original positions, then refits the viewport (default action when clicking Reset directly)
  - **Reset Nodes** — restores node positions only; leaves your current zoom/pan intact
  - **Reset View** — refits the viewport to show all nodes without moving any nodes
- **Help guide updated** — Graph & Navigation topic now documents all three reset options

---

## v7.0.3 — 2025-05-04

### 🐛 Bug Fixes
- **Export All failed silently on large projects** — `JSON.stringify` on 1000+ conversations caused memory exhaustion; export now streams each conversation individually into a `Blob` array, eliminating the memory spike. Tested with 3000+ conversations.
- **Export All now includes hidden conversations** — conversations stashed via Show Only were previously excluded from the export; they are now included alongside visible ones
- **Download anchor fix for Firefox** — the anchor element is now appended to the DOM before the programmatic click, fixing a silent no-download in Firefox and some other browsers

---

## v7.0.2 — 2025-05-04

### 🆕 New
- **Smart duplicate handling on import** — when adding files to an existing project, each conversation is matched by `conversation_id`. Same ID with more nodes → updated in place (in whichever pool it lives — visible, hidden, or deleted). Same or fewer nodes → skipped unchanged.
- **Import summary notification** — after every load, a breakdown shows exactly what happened: *3 new, 2 updated, 1 skipped — from conversations.json*
- **Help guide updated** — Loading & Unloading topic now documents the duplicate logic with a re-import tip

---

## v7.0.1 — 2025-05-04

### 🐛 Bug Fixes
- **Metadata level chain showed "undefined" on OpenAI files** — BFS depth calculation was hardcoded to start at `root`; OpenAI files use a UUID as their root node, causing all levels to show as undefined
- **Branch Index depth badges also affected** — same hardcoded root fix applied to the Branch Index depth/position-at-level badges
- **Empty assistant nodes misclassified as system** — the smart system-detection heuristic was incorrectly reclassifying `role: assistant` nodes with empty text (OpenAI placeholder nodes) as system nodes, hiding or collapsing them

---

## v7.0 — 2025-05-04

This is a major release that replaces the original Multiverse Viewer. The tool has been rebuilt from the ground up with a new name, new architecture, and a large set of new features.

### 🆕 New Format Support
- **GLM / Zhipu AI** — auto-detects and converts `chat.history.messages` structure
- **Format badge** — colored pill in the topbar identifies the detected format after loading (OpenAI, DeepSeek, Claude, Grok, Mistral, GLM)

### 🗂 Project & Conversation Management
- **Multi-file loading** — load multiple JSON files at once; each becomes a separate conversation entry
- **Load dialog** — when files are already open, asks to add to the current project or start fresh
- **Show Only** — right-click a conversation to hide all others (non-destructive; others are stashed, not deleted)
- **Restore All** — right-click to bring back all hidden conversations
- **Start Over** — resets every conversation (visible, hidden, and deleted) to its original loaded state; warns before proceeding
- **Deleted conversation recovery** — Delete Conv stashes to a recovery pool that Start Over can restore
- **Close Conversation** — removes only the active conversation; switches to the next if others are loaded
- **Unload All** — clears all conversation pools for a fresh slate

### 🔵 Graph Visualization
- **Interactive D3.js tree** with pan, zoom, and fit-to-screen
- **Drag entire subtree** or Shift+drag to move a single node
- **Reset Layout** — animates all nodes back to their original positions
- **Minimap toggle** — show/hide the minimap overlay; Ctrl+drag to reposition it anywhere in the graph area
- **Node right-click menu** — Copy Message, Select & View, Delete Node directly from the graph
- **Highlight fade on drag** — selection highlights fade while dragging so they don't interfere with repositioning
- **Drag lines stay attached** — fixed: links no longer detach from nodes when dragging
- **System node toggle preserves all branches** — fixed: hiding system/other nodes now correctly promotes all their children instead of dropping sibling branches

### 📄 Selected Node Panel
- Four view modes: **Rendered** (Markdown → HTML) · **Markdown** · **HTML** · **JSON**
- **Node location bar** — shows depth (↳N), `YYYY-MM-DD HH:MM` timestamp, and ancestor breadcrumb
- **Metadata level chain** (M button) — every ancestor level with depth, pos/total, and message preview; scrollable; clicking jumps to that node without closing the branch
- **Search term highlighting** — H toggle highlights every match in yellow; synced with the Branch panel
- Copy, Export (format-matched file), Pop-out (new tab), PDF export

### 🌿 Branch View Panel
- **Role-colored message cards** — blue (user), green (assistant), gray (system), purple (other) with tinted backgrounds and left borders
- **Per-message depth, timestamp, and breadcrumb** in each card header
- **Per-message Copy button** on hover
- **View modes** — Rendered / Markdown / HTML / JSON applied to all messages; export downloads in the matching format
- **Pop-out** — opens the full thread in a new tab with role shading, timestamps, and copy buttons
- **GPT↓** — exports the current conversation as an OpenAI-compatible `conversations.json`
- **Conversation summary** — bottom of branch shows total message count broken down by role
- **Branch jump pulse** — clicking a Branch Index entry scrolls and pulses the target message card with a yellow glow
- **Branch Index levels** — each entry shows depth and position-at-level (e.g. `3,2/5`)
- **Branch Index click** — selecting a branch index entry no longer rebuilds the branch; keeps the current path open
- **Filter bar** (Show · Search · Only in):
  - **Show:** role pills — always hides unchecked roles regardless of search
  - **Search bar** — real-time filtering; non-matching messages are hidden completely; matches highlighted in yellow
  - **Only in:** scope pills — narrows which roles are searched (and hides them from results when searching)

### 🔍 Global Search
- Real-time search across the current conversation or all loaded conversations
- **Result cards** show: role, depth (↳N), timestamp, conversation breadcrumb, and a highlighted preview snippet
- Clicking a result **selects the node, zooms in, and centers the graph** on it — result list stays open for continued browsing
- All matching nodes highlighted with a yellow glow on the graph
- Conversations with matches float to the top of the sidebar with a match count badge
- Search results persist after clicking — only clear when the search query is erased

### 💾 Export Options
- **Export All** (top bar) — exports every loaded conversation as a single OpenAI `conversations.json` array
- **Branch export** — format-matched: Rendered → styled `.html`, Markdown → `.md`, HTML → `.html`, JSON → `.json`
- **GPT↓** — exports the current conversation as a single-item OpenAI array
- **Right-click → Export Conv** — exports one conversation from the sidebar
- Copy, Export file, Pop-out, PDF for the Selected Node panel

### 🎨 Themes & Settings
- **5 themes** — Dark, Light, Blue, Green, Purple with `localStorage` persistence
- **System theme detection** — on first visit, defaults to Light or Dark based on your OS `prefers-color-scheme` setting
- **Settings panel** — toggle system nodes, other nodes, tooltips; adjust tooltip delay (500ms–10,000ms)

### 📚 Help & Documentation
- **Help modal** — 15 detailed topics with full-text search, match highlighting, and clickable result cards
- **What's New** — versioned changelog inside Help
- **License & Credits** — MIT license declaration, all third-party libraries with versions, font credits
- **GitHub signature** — topbar link to this repository

### 🔧 Technical
- All processing is client-side — no data is ever sent to a server
- Libraries: D3.js v7, marked.js, DOMPurify, html2canvas, jsPDF (all via CDN)
- MIT License

---

## v6.0 — 2025-05-01 *(Original release)*

Initial public release of the Multiverse Viewer.

### Features
- Interactive D3.js conversation tree for OpenAI, DeepSeek (3 formats), Claude, Grok, and Mistral AI
- Auto format detection and conversion to unified internal structure
- Left sidebar with search and conversation list; right panel with Selected Node and Branch tabs
- Rendered / Markdown / HTML / JSON view modes
- Branch view with role-colored cards, per-message copy, pop-out, and GPT↓ export
- Role-based node filtering (Show/hide system, other nodes)
- Minimap, pan/zoom, drag nodes, reset layout
- Dark/Light/Blue/Green/Purple themes
- Settings menu, help guide, metadata toggle
- All processing client-side; MIT License

---

*For questions or contributions, visit [github.com/akivacp/chatgpt-json-tree-viewer](https://github.com/akivacp/chatgpt-json-tree-viewer)*
