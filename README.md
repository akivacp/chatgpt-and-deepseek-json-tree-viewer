# 🌳 ChatGPT JSON Tree Viewer

**Ever wanted to actually *see* your AI conversations — not just scroll through them?**

This tool takes your exported chat history from ChatGPT, Claude, DeepSeek, and other AI apps and turns it into an interactive map you can explore, search, and read.

**[➜ Open the Viewer](https://akivacp.github.io/chatgpt-json-tree-viewer/)** &nbsp;|&nbsp; [GitHub](https://github.com/akivacp/chatgpt-json-tree-viewer)

![Main UI](docs/screenshot-main.png)

---

## What does it do?

When you chat with an AI, you often go back and try different responses, rewrite your questions, or branch off in different directions. Most chat apps show this as one long scroll — but it's actually a *tree*. Some messages have multiple replies. Some threads go deep. Some branch off and go different places.

This viewer shows you that tree as a visual map. You can:

- **See the full shape** of a conversation at a glance
- **Click any message** to read it in the panel on the right
- **Follow a branch** from start to finish — see the full back-and-forth that led to any response
- **Search** across everything you've ever said or asked — across thousands of chats at once
- **Export** what you find as a readable document, PDF, or file

Everything runs in your browser. Nothing is uploaded anywhere. Your conversations stay on your device.

---

## Who is this for?

**You don't need to know anything about code to use this.** If you've ever exported your ChatGPT history and wondered what to do with the JSON file — this is it.

- 📚 **Researchers and students** — find that conversation where you worked through a problem, see how your thinking branched
- ✍️ **Writers** — revisit brainstorming sessions, compare different directions you explored
- 💼 **Professionals** — review past AI-assisted work, document conversations for records
- 🧑‍💻 **Developers** — inspect conversation structure, export for analysis, or browse your history with a better interface
- 🗃️ **Anyone with a lot of chats** — finally make sense of years of conversations

---

## Why this exists

AI conversations are becoming a form of external memory — brainstorming, research, journaling, coding, problem-solving.

But most interfaces flatten those conversations into endless scrolling.

This tool was built to make those conversations navigable again.

---

## Getting started

### Step 1 — Export your chats

**ChatGPT:** Settings → Data Controls → Export Data. You'll get an email with a ZIP file. Inside is a file called `conversations.json`.

**Claude:** Settings → Export Data. You'll get a `claude_conversations.json` file.

**DeepSeek, Grok, Mistral:** Each has an export option in settings. Download the JSON file.

### Step 2 — Open the viewer

Download `chatgpt-json-tree-viewer.html` from this page and open it in your browser (Chrome, Edge, or Firefox work best). No installation. No account. Just open the file.

### Step 3 — Load your chats

Click **Load File** and select your JSON file, or drag it onto the page. Your conversations appear in the sidebar and the tree map appears in the middle.

---

## How to use it

### Reading a conversation

Click any dot on the map to select it. The right panel shows you that message. Switch between two tabs:

- **Selected Node** — just that one message, with its timestamp and which AI model was used
- **Branch** — the full conversation thread from beginning to end

### Understanding the map

Each dot is a message. Lines show which messages led to which. Colors show who sent it:

- 🔵 **Blue** — you
- 🟢 **Green** — the AI
- ⭕ **Gray dashed** — system messages (usually hidden behind the scenes)
- 🟣 **Purple** — other types

When a conversation branches — like when you regenerated a response or tried a different question — the map splits into multiple paths, showing you all the directions it went.

### Searching

Type anything in the search bar on the left to find messages across your conversations. Matching messages glow on the map and appear as clickable cards. You can search the current conversation or everything loaded at once.

### Working with many conversations

Load as many files as you want — they all appear together in the sidebar. If you load the same conversation twice, duplicates are skipped automatically. If you load an updated version with more messages, it quietly updates the old one.

If your export file is very large (hundreds of megabytes), the app warns you and offers to split it into smaller pieces and import them automatically — no manual work needed.

---

## Themes and customization

Click the colored dots in the top-right corner to switch between Dark, Light, Blue, Green, and Purple themes.

The **rainbow dot ✦** opens a color editor where you can customize every color — backgrounds, text, accents, and individual node colors. Changes apply live and are saved automatically.

---

## Exporting and saving

Whatever you're reading, you can save it:

- **Copy** — copies the text to your clipboard
- **Export** — downloads as a file (styled HTML, Markdown, or JSON)
- **PDF** — opens a clean print window. Use your browser's "Save as PDF" to save it. Looks like a proper document with correct fonts and page margins.
- **Pop-out** — opens the current view in a new browser tab

To save your whole project, use **Export All** in the top bar. This downloads all your loaded conversations as a single file you can reload later. For very large projects it splits into numbered chunk files automatically.

---

## Supported formats

Works with exports from:

| Platform | How to export |
|---|---|
| **ChatGPT / OpenAI** | Settings → Data Controls → Export |
| **Claude (Anthropic)** | Settings → Export Data |
| **DeepSeek** | Settings → Export |
| **Grok / xAI** | Settings → Export |
| **Mistral AI** | Settings → Export |
| **GLM / Zhipu AI** | Settings → Export |

The format is detected automatically — you don't need to tell the app which platform it came from.

---

## Frequently asked questions

**Is my data safe?**
Yes. Everything runs inside your browser. No data is ever sent anywhere. When you close the tab, nothing is stored (except your theme and settings, which stay on your device).

**Can I use it offline?**
Yes, once you've downloaded the HTML file. You need an internet connection the first time to load some libraries, but after that it works offline.

**Do I need to install anything?**
No. It's a single HTML file — open it like any other file on your computer.

**What if my file is too big to open?**
The app will warn you and offer to handle it automatically. It can split huge files and import the pieces one by one.

**Can I load multiple files at once?**
Yes. Load as many as you want. The app handles duplicates intelligently.

**Can I get back a conversation I accidentally deleted from the viewer?**
Yes — deleted conversations go to a recovery pool. Right-click any conversation in the sidebar and choose **Start Over** to restore everything.

---

## Libraries used

| Library | Purpose |
|---|---|
| [D3.js](https://d3js.org) v7.9.0 | Interactive tree map |
| [marked.js](https://marked.js.org) v9.1.6 | Markdown rendering |
| [DOMPurify](https://github.com/cure53/DOMPurify) v3.0.6 | Safe content display |
| [html2canvas](https://html2canvas.hertzen.com) v1.4.1 | Graph image export |
| [jsPDF](https://github.com/parallax/jsPDF) v2.5.1 | PDF support |

Fonts: DM Sans, Literata, JetBrains Mono (SIL Open Font License, via Google Fonts).

---

## License

MIT — free to use, modify, and share. See [LICENSE](LICENSE) for details.

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=akivacp/chatgpt-json-tree-viewer&type=date&legend=top-left)](https://www.star-history.com/#akivacp/chatgpt-json-tree-viewer&type=date&legend=top-left)
