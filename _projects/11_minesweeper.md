---
layout: page
title: "Minesweeper"
description: Desktop implementation of the classic Minesweeper puzzle game with customisable board grids and recursive flood-fill tile clearance in Python and Tkinter.
importance: 4
category: Personal Projects
related_publications: false
---

### Overview

**Minesweeper** is a desktop recreation of the classic deduction puzzle game built in **Python** using the **Tkinter** graphical library and **Pillow (PIL)** for sprite asset management.

The player traverses an obscured grid containing concealed mines, relying on numerical adjacency cues to deduce mine locations, flag hazardous cells, and reveal all safe tiles without detonation.

- **Language**: Python 3
- **GUI Framework**: Tkinter
- **Image Processing**: Pillow (PIL)
- **GitHub Repository**: [TamarNoselidze/Minesweeper](https://github.com/TamarNoselidze/Minesweeper)

---

### Key Features & Mechanics

- **Customisable Game Grid**: Allows players to configure custom board dimensions and mine densities to adjust puzzle difficulty.
- **Recursive Flood-Fill Clearing**: Implements a recursive traversal algorithm that automatically cascades and uncovers connected zero-mine regions upon revealing a blank cell.
- **Tile State Management**: Interactive controls supporting left-click cell clearance and right-click tactical flag toggling to mark suspected mine locations.
- **Visual Assets & Interface**: Renders distinct graphical sprites for active flags, detonated mines, and numeric proximity indicators.
- **Controls & Diagnostics**: Built-in game restart functionality and an integrated rules dialogue window for gameplay instruction.

---

### Code & Repository

- **GitHub Repository**: [TamarNoselidze/Minesweeper](https://github.com/TamarNoselidze/Minesweeper)
