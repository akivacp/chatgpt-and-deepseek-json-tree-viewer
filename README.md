# ChatGPT JSON Tree Viewer

**A simple, client-side HTML viewer for exploring and visualizing ChatGPT conversation exports in a tree format.**

This project allows you to visualize exported JSON data from ChatGPT conversations in an interactive, tree-based format. The viewer helps you navigate and understand the hierarchical structure of conversation data easily, offering a user-friendly interface for both developers and non-technical users.

## Features

- **Interactive Tree View**: Explore JSON data as a navigable tree, zooming and panning through conversation data.
- **Multiple Viewing Modes**: View your data in various formats including markdown, raw JSON, rendered HTML, and more.
- **Search & Filter**: Quickly search through large conversation datasets.
- **Export Options**: Export conversation content in markdown, HTML, or raw JSON format.
- **Client-Side Only**: No server required! All processing happens directly in your browser.

## Installation

You can use this viewer by simply opening the `chatgpt-json-tree-viewer.html` file in your browser. There is no need to install anything.

### Steps:
1. Clone or download this repository to your local machine.
2. Open `chatgpt-json-tree-viewer.html` in your web browser.
3. Click the **"Load JSON"** button to upload a ChatGPT conversation export.
4. Use the interactive tree to explore the conversation's data structure.

## Usage

1. **Loading JSON**: Click the **"Load JSON"** button and select a JSON file from your local machine. The file should contain data in a format compatible with the viewer (e.g., ChatGPT conversation exports).
2. **Navigating the Tree**: Use your mouse to click and drag nodes. Zoom in/out using the mouse wheel.
3. **Viewing Content**: Click on a node to open the detailed message view in the right panel.
4. **Exporting Data**: You can export the displayed content in different formats: raw JSON, HTML, or Markdown.

## Demo

To see the viewer in action, simply download the repository and open the `chatgpt-json-tree-viewer.html` file in any modern web browser.

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! If you have ideas for new features, improvements, or bug fixes, feel free to fork the repository and submit a pull request.  

### How to Contribute:
1. Fork this repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit them (`git commit -am 'Add new feature'`).
4. Push to your branch (`git push origin feature/your-feature`).
5. Create a pull request with a description of your changes.

## Acknowledgements

- This project uses the following open-source libraries:
  - **[D3.js](https://d3js.org/)**: JavaScript library for producing dynamic, interactive data visualizations.
  - **[Marked.js](https://marked.js.org/)**: A fast markdown parser and compiler.
  - **[DOMPurify](https://github.com/cure53/DOMPurify)**: A DOM-based XSS sanitizer for modern browsers.

## Disclaimer

This project is an **independent** tool and is not affiliated with or endorsed by OpenAI. It is designed to help users interact with **ChatGPT** exported conversation data.

---

### Need Help?

If you run into issues or have any questions, feel free to open an issue on the GitHub repository, and I'll do my best to assist you.

