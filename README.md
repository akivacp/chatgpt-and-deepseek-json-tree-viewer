
# 🌳 ChatGPT JSON Tree Viewer

*A standalone, offline, multi-platform conversation explorer and branching tree visualizer.*

## Live Demo

👉 Try the HTML viewer directly in your browser:  
https://htmlpreview.github.io/?https://github.com/akivacp/chatgpt-json-tree-viewer/blob/main/chatgpt-json-tree-viewer.html


## 📷 Screenshots

![Main UI](docs/screenshot-main.png)

---

## 🧭 Overview

**ChatGPT JSON Tree Viewer** is a **single-file HTML application** that loads exported AI conversation data and converts it into an **interactive branching tree**, complete with metadata inspection, Markdown rendering, multi-format compatibility, full-text search, and a developer-grade UI.

Everything runs **100 percent locally**, right inside your browser.\
No servers, no uploads, no telemetry.

This tool supports exports from:

- **ChatGPT Multiverse exports**
- **ChatGPT conversations.json** (many conversations in one file)
- **DeepSeek Chat** & **DeepSeek Exporter**
- **Claude (Anthropic)**
- **xAI Grok**
- **Mistral AI**
- And arbitrary JSON structures that can be normalized into OpenAI-style node maps

The viewer auto-detects format, auto-converts it, and presents it visually.

---

## 🚀 Features

### 🔍 **Universal Format Detection**

The viewer intelligently identifies and converts many AI export formats:

- **OpenAI Multiverse**
- **OpenAI conversations.json**
- **DeepSeek Chat (mapping format)**
- **DeepSeek Exporter**
- **Claude (chunked contentChunks)**
- **xAI Grok conversation objects**
- **Mistral AI chat\_messages format**

It reconstructs:

- Parent/child mapping
- Assistant/user/system roles
- Timestamps
- Conversation titles
- Linear or branching structure

If needed, you can disable auto-detection in **Developer Tools**.

---

### 🌳 **Interactive Graph Viewer**

- Force-directed layout optimized for chat trees
- Drag nodes to reorganize branches
- Zoom & pan with trackpad/mouse wheel
- Automatic centering & focus on selected nodes
- Themed node colors (User, Assistant, System, Other)
- Highlight ancestors, descendants, search matches, and selected node
- Dimming non-relevant parts when a node is highlighted
- Smooth animated pulses for selected/ancestor/descendant nodes

---

### 📑 **Right-Panel Message Viewer**

Tabbed content modes:

- **Rendered Markdown → HTML**
- **Raw Markdown**
- **HTML source**
- **Original JSON fragment**

Each mode includes:

- **Copy**
- **Export**
- **Pop-Out window**
- **PDF generation** (via jsPDF + html2canvas)

Sticky UI ensures tools always stay visible.

---

### 📂 **Branch Reconstruction Sidebar**

A unique feature of your viewer:

- Shows the **entire linear branch** from the selected node back to the root
- Each item clickable
- Local branch search built-in
- Auto-scroll and highlight the current position
- Collapsible sidebar mode (tiny icon mode)

---

### 🔎 **Global Search Engine**

Search every message across:

- ChatGPT multiverse files
- Multi-conversation conversations.json
- Claude messages
- Grok responses
- DeepSeek exports
- Mistral conversations

The search UI shows:

- Snippets
- Role labels
- Conversation match count badges
- Click to instantly jump to that node, even across different conversations

---

### 🗂️ **Conversation List (for conversations.json)**

When you load a **conversations.json**, the left sidebar becomes a selector UI:

- Sorts conversations by date
- Shows date, title, message count
- Indicates which conversations contain search matches
- Click to switch instantly
- “Close Conversation” button to return to multi-conversation mode

---

### 🎨 **Built-in Themes**

Users can switch seamlessly between:

- **Dark** (default)
- **Light**
- **Blue**
- **Green**
- **Purple**

Themes apply to:

- Graph
- Sidebar
- Right-panel viewer
- Tooltips
- Minimap
- Search UI
- Buttons

No reload required.

---

### 🛠️ **Developer Tools Panel**

Options include:

- Show/hide **system nodes**
- Toggle **auto-format detection**
- Toggle **tooltips**
- Adjust tooltip linger duration (500 ms to 10 seconds)

---

### 🗺️ **Minimap**

A live-updating minimap renders the entire graph shape.\
Your current viewport rectangle is shown in real time.

Great for huge multiverse branches.

---

### ↔️ **Resizable Panels**

Drag handles allow resizing:

- Left sidebar
- Right message viewer

Perfect for ultra-wide monitors or portrait screens.

---

## 📥 Installation

No installation required.\
Just download and open in your browser:

```
chatgpt-json-tree-viewer.html
```

Everything runs locally.

> Works best on Chrome, Edge, Brave, or Firefox.

---

## 📘 Usage Guide

### 1. **Load a JSON File**

Click:

**Load Conversation JSON**

Works with:

- ChatGPT export folders
- ChatGPT multiverse exports
- DeepSeek Chat exports
- conversations.json
- Claude message arrays
- Mistral / Grok chat files

You can also **drag and drop** onto the button.

---

### 2. **Explore the Graph**

- Scroll to zoom
- Drag empty space to pan
- Drag nodes to reposition
- Hover to see live tooltips
- Click a node to open its message

---

### 3. **Search Messages**

#### Global Search

Use the search bar in the left sidebar.

Results display:

- Conversation
- Preview text
- Role
- Highlighted match

#### Branch Search

Open the Branch tab and use the branch search bar.

---

### 4. **Inspect Message Content**

Choose a viewer tab:

- Rendered
- Markdown
- HTML
- Original JSON

Then use:

- **Copy**
- **Export**
- **Pop-Out**
- **PDF**

---

### 5. **Switch Conversations**

When loading `conversations.json`:

- All conversations appear in the sidebar
- Click to open any of them instantly
- “Close Conversation” returns to overview mode

---

### 6. **Use Developer Tools**

Click **Developer Tools** to toggle advanced controls.


## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=akivacp/chatgpt-json-tree-viewer&type=date&legend=top-left)](https://www.star-history.com/#akivacp/chatgpt-json-tree-viewer&type=date&legend=top-left)
