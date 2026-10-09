---
layout: page
title: "Board Game Pente"
description: Graphical recreation of the abstract strategy board game Pente featuring custom capture mechanics and Model-View architecture in C# and GTK#.
importance: 3
category: Personal Projects
related_publications: false
---

### Overview

**Board Game Pente** is a desktop implementation of the classic two-to-four player abstract strategy board game *Pente*, engineered in **C#** with a graphical user interface powered by **GTK# / GDK**. 

Players take turns placing stones on an intersection grid with the objective of creating alignments or executing tactical captures. The application supports standard two-player duels as well as a four-player team mode (paired in two cooperative alliances).

- **Language**: C# (.NET)
- **GUI Framework**: GTK# / GDK
- **Architectural Pattern**: Model-View Architecture
- **GitHub Repository**: [TamarNoselidze/Pente-Game](https://github.com/TamarNoselidze/Pente-Game)

---

### Architectural Design: Model-View Separation

The codebase enforces strict separation between business logic and the presentation layer:

- **Model (`Model.cs` - `Game` class)**:
  - Encapsulates the entire game state, move validation, turn switching, and victory condition evaluation.
  - Fully decoupled from UI libraries (contains no GTK/GDK dependencies), enabling modular testing and domain independence.
- **View (`View.cs` - `MyWindow` and `Area` classes)**:
  - Manages the graphical window and drawing canvas (`Area`) where the grid, stones, and status elements are rendered.
  - Contains no direct state-mutation logic; player clicks dispatch coordinate actions strictly via the `game.play(x, y)` interface.
- **Entry Point (`Program.cs`)**:
  - Initialises the runtime environment and bootstraps the main application loop.

---

### Game Mechanics & Win Conditions

The game incorporates modified classic Pente rules:

- **Two-Player Mode**:
  - **Five-in-a-Row**: A player wins immediately upon placing exactly 5 stones in an unbroken horizontal, vertical, or diagonal line.
  - **Flank Captures**: Flanking an opponent's pair of adjacent stones on opposite ends captures both stones. A player wins by accumulating 5 captures (10 captured stones total).
- **Four-Player Team Mode**:
  - Players form two competing pairs.
  - Victory is achieved when any teammate completes a five-stone sequence, or when the team collectively executes 10 captures (20 captured stones).
- **Capture Detection Algorithm**: Implements an 8-directional raycast search originating from each newly placed stone to detect and remove flanked opponent pairs.

---

### Code & Repository

- **GitHub Repository**: [TamarNoselidze/Pente-Game](https://github.com/TamarNoselidze/Pente-Game)
