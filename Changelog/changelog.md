# ChatGPT JSON Tree Viewer — Changelog

---

## v7.0 — 2025-05-04 *(Current)*

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
