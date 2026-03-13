# NNTrainer Visualizer — VS Code Extension

Interactive flow graph visualizer for NNTrainer `.ini` model files with `.bin` weight inspection.

---

## Installation (3 steps)

### Step 1 — Install vsce (VS Code Extension packager)
Open a terminal and run:
```bash
npm install -g @vscode/vsce
```

### Step 2 — Package the extension
Navigate to this folder in terminal:
```bash
cd nntrainer-visualizer
vsce package --no-dependencies
```
This creates a file called `nntrainer-visualizer-1.0.0.vsix`

### Step 3 — Install in VS Code
Either:
- Open VS Code → Extensions sidebar → `···` menu → **Install from VSIX** → pick the `.vsix` file

Or from terminal:
```bash
code --install-extension nntrainer-visualizer-1.0.0.vsix
```

---

## How to Use

### Method 1 — Right-click (easiest)
1. Open your NNTrainer project folder in VS Code
2. In the file explorer, right-click any `.ini` model file
3. Select **"Open in NNTrainer Visualizer"**

### Method 2 — Command palette
1. Open a `.ini` file in the editor
2. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
3. Type `NNTrainer: Visualize Model` → Enter

### Method 3 — Keyboard shortcut
1. Open a `.ini` file in the editor
2. Press `Ctrl+Shift+V`

---

## Loading Weight Stats from .bin

Once the graph is open:
- Click **"Load .bin Weights"** — auto-detects a `.bin` file in the same folder as the `.ini`
- Click **"Browse .bin…"** — manually pick any `.bin` file

Once loaded, each node shows a small colored dot indicating weight stats are available.
Click any node → detail panel shows histogram + min/max/mean/std for each weight tensor.

---

## Tested Models
- `simple_fc.ini` — basic fully-connected
- `mnist.ini` — LeNet MNIST (from NNTrainer Applications/MNIST)
- `resnet_skip.ini` — ResNet with skip connections
- `qwen2_0.5b.ini` — Qwen2 0.5B transformer

---

## File Structure
```
nntrainer-visualizer/
├── package.json          ← extension manifest (name, commands, menus)
├── src/
│   └── extension.js      ← main extension code (file I/O, .bin parsing)
├── media/
│   └── visualizer.html   ← full visualizer UI (graph renderer, detail panel)
└── README.md
```
