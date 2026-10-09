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

The 15-Puzzle is a classic benchmark in artificial intelligence and heuristic search, consisting of a \(4 \times 4\) grid with 15 numbered sliding tiles and one empty space. With over \(10^{13}\) reachable permutations (\(16! / 2\)), brute-force exploration is computationally intractable. 

This project implements an optimal, purely functional solver written in **Haskell**, utilising the **A\* search algorithm** coupled with an admissible **Manhattan distance heuristic** and custom purely functional priority queues.

- **Language**: Haskell (GHC)
- **GitHub Repository**: [TamarNoselidze/15-Puzzle-Solver](https://github.com/TamarNoselidze/15-Puzzle-Solver)

---

### Algorithmic Architecture

#### 1. Informed A* Search & Admissible Heuristic
- **Evaluation Function**: Guides state exploration using \(f(n) = g(n) + h(n)\), where \(g(n)\) represents the path cost from the root configuration and \(h(n)\) estimates the remaining cost to the solved state.
- **Manhattan Distance Heuristic**: Computes the sum of vertical and horizontal grid displacements for all non-empty tiles:
  \[
  h(n) = \sum_{i=1}^{15} \left( \lvert x_i - x_i^* \rvert + \lvert y_i - y_i^* \rvert \right)
  \]
  Because Manhattan distance never overestimates the true number of moves required (admissible and consistent), the search guarantees discovering the mathematically **optimal (shortest)** solution sequence.

#### 2. Purely Functional Leftist Min-Heap
To manage the open set efficiently without mutable arrays or pointer structures, the solver implements a custom **Leftist Heap** priority queue:
- **Leftist Property**: Enforces that the rank of every left child is at least the rank of its right child (\(\text{rank}(\text{left}) \ge \text{rank}(\text{right})\)), ensuring the right spine remains logarithmic.
- **Logarithmic Operations**: Enables \(O(\log n)\) merging, insertion (`insertHeap`), and minimum extraction (`remove_smallest`), keeping state evaluation fast as the search frontier grows.
- **State Tracking**: Uses immutable maps (`Data.Map`) to maintain \(g\)-scores and track board paths while pruning redundant states.

---

### Capabilities & Usage

- **Configurable Input**: Solves arbitrary user-provided board layouts from text files or generates provably reachable initial states via backward random-walk scrambles (`-r <num-moves>`).
- **Detailed Diagnostics**: Reports the step-by-step optimal board transition sequence, total moves executed, and overall count of explored state-space nodes.

---

### Code & Resources

- **GitHub Repository**: [TamarNoselidze/15-Puzzle-Solver](https://github.com/TamarNoselidze/15-Puzzle-Solver)
- **Main Source File**: [`15-solver.hs`](https://github.com/TamarNoselidze/15-Puzzle-Solver/blob/main/15-solver.hs)
