# Temperature Test Analyzer
A lightweight, browser-based tool for parsing MCGS/Radwin CSV exports to analyze thermal test phases.

### 📌 Overview
This tool provides a fast, dependency-free way to visualize and extract key timing data from temperature test logs. Simply drag and drop a .csv file into the browser to automatically calculate the duration, start/end times, and rate of change for each thermal phase.

### ✨ Features
- **Drag & Drop Interface**: Instantly load .csv files directly in the browser.
- **Robust CSV Parsing**: Automatically detects delimiters (Comma, Semicolon, Tab) and handles various timestamp formats.
- **Automated Phase Analysis**: Automatically detects and extracts data for:
  - -40 Dip
  - -40 Soak
  - 70 Rise
  - 70 Soak
  - 25 Dip
- **Rate Calculation**: Calculates the exact temperature rate of change (°C/min) for the ramp phases.
- **Total Test Runtime**: Aggregates the total duration of the test from start to finish.
- **Interactive Charting**:
  - Visualizes PV (Process Value) and SV (Set Value).
  - Custom Zoom & Pan: Scroll to zoom in/out, click and drag to pan, and double-click to reset the view. (Built without external zoom plugins for maximum stability).
  - Phase Highlighting: Color-coded background bands for each phase with custom floating labels.
- **Export Options**:
  - **Save Chart Image**: Export the current chart view as a high-contrast, clean `.png` image.
  - **Copy/Save Report**: Copy the generated text report to your clipboard or save it as a `.txt` file.
- **UI/UX**: Fully responsive layout with a Light/Dark mode toggle.

### 🚀 Usage
1. Clone or download this repository.
2. Open `index.html` in any modern web browser (Chrome, Edge, Firefox, Safari).
3. Drag and drop your `.csv` file into the designated area (or click to browse).
4. Review the extracted phase cards and interact with the chart.
5. Use the toolbar at the bottom to export images, copy the report, or clear the current data.

*No server, Node.js, or installation required. It runs entirely in the browser.*

### 🛠️ Built With
- HTML5 / CSS3 / Vanilla JavaScript
- [Chart.js (v4)](https://www.chartjs.org/) - For chart rendering
- [Chart.js Annotation Plugin](https://github.com/chartjs/chartjs-plugin-annotation) - For phase highlighting

### 🧠 Architecture Notes
- **Custom Zone Label Plugin**: A custom Chart.js plugin (`zoneLabelPlugin`) is used to draw the phase labels perfectly centered inside the colored bands. It dynamically adjusts colors based on whether the chart is being viewed in Light/Dark mode or being exported as an image.
- **Zero-Dependency Zoom**: Standard Chart.js zooming requires external plugins (like `chartjs-plugin-zoom`), which can cause initialization crashes and timing issues. This tool features a custom, native zoom engine built with vanilla JavaScript. It captures wheel and mouse events on the canvas and dynamically updates the chart's `min` and `max` scales.
- **Dynamic DOM Injection**: To prevent the chart from crashing due to `0px` height when hidden, the chart container is injected into the DOM only after a file is successfully parsed. A `50ms` timeout allows the browser to calculate the container's physical dimensions before rendering.
- **Image Export Fallback**: To ensure the exported PNG is always readable regardless of the current theme, the export function temporarily forces the chart to light-mode colors (dark text) and draws it to an off-screen canvas before downloading.

### 📄 License
Internal / Proprietary (or update with your preferred license).
