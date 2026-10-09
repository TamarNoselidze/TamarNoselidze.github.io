---
layout: page
title: "15-Puzzle Solver"
description: Purely functional A* state-space search algorithm with Manhattan distance heuristics and custom Leftist Heaps in Haskell.
img: assets/img/puzzle.png
importance: 7
category: Machine Learning & AI
related_publications: false
---

### Overview

The 15-Puzzle is a benchmark in artificial intelligence and heuristic state-space search, consisting of a $4 \times 4$ grid with 15 numbered sliding tiles and one empty space. With over $10^{13}$ reachable permutations ($16! / 2$), brute-force search is intractable.

This project implements an optimal, purely functional solver in **Haskell**, combining the **A* search algorithm** with an admissible **Manhattan distance heuristic** and custom functional priority queues.

- **Language**: Haskell (GHC)
- **GitHub Repository**: [TamarNoselidze/15-Puzzle-Solver](https://github.com/TamarNoselidze/15-Puzzle-Solver)

---

### Algorithmic Architecture

- **Informed A* Search**: Guides state exploration using $f(n) = g(n) + h(n)$, where $g(n)$ is path cost and $h(n)$ is heuristic estimated cost to the solved state.
- **Manhattan Distance Heuristic**: Computes tile displacement: $h(n) = \sum_{i=1}^{15} (\lvert x_i - x_i^* \rvert + \lvert y_i - y_i^* \rvert)$. Because the heuristic is admissible and consistent, the solver guarantees finding the mathematically shortest solution.
- **Purely Functional Leftist Min-Heap**: Manages the open set efficiently without mutable arrays. By maintaining the leftist property ($\text{rank}(\text{left}) \ge \text{rank}(\text{right})$), the queue ensures $O(\log n)$ merge, insert, and extract-min operations.
- **Immutable State Tracking**: Uses `Data.Map` to track visited states and $g$-scores while pruning redundant paths.

---

### Usage

- **Input Support**: Solves custom board layouts from text files or generates reachable configurations using backward random-walk scrambles (`-r <num-moves>`).
- **Diagnostics**: Outputs the optimal move sequence, total steps, and number of explored nodes.

---

### Code & Resources

- **GitHub Repository**: [TamarNoselidze/15-Puzzle-Solver](https://github.com/TamarNoselidze/15-Puzzle-Solver)
- **Main Source File**: [`15-solver.hs`](https://github.com/TamarNoselidze/15-Puzzle-Solver/blob/main/15-solver.hs)
