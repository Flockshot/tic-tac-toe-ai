# Unbeatable Tic-Tac-Toe AI (Minimax & Alpha-Beta Pruning)

Designed and implemented an unbeatable AI for Tic-Tac-Toe in C, showcasing expertise in adversarial search algorithms, game theory, and heuristic optimization.

This project was developed in two parts:
1.  **3x3 Perfect AI:** An AI that plays a *perfect* game of 3x3 Tic-Tac-Toe using the Minimax algorithm.
2.  **7x7 Heuristic AI:** A more advanced AI that plays 7x7 Tic-Tac-Toe (4-in-a-row) using a depth-limited search with Alpha-Beta Pruning and a custom heuristic.

![Language](https://img.shields.io/badge/Language-C-A8B9CC.svg?logo=c&logoColor=white)
![AI](https://img.shields.io/badge/Algorithm-Minimax_&_Alpha--Beta-orange.svg)

---

## 🤖 Part 1: The 3x3 "Perfect" AI (Minimax)

This program (`3x3 Minimax.c`) implements a Human-vs-AI game where the AI is unbeatable.

### How It Works
* [cite_start]**Algorithm:** Uses the **Minimax** algorithm[cite: 5133, 5138].
* **Search:** Explores the *entire* game tree to find the optimal move. Because the 3x3 state space is small (~255,168 nodes), a full, exhaustive search is possible.
* **Evaluation:** The AI recurses until it reaches a terminal (win/loss/draw) state. It then assigns a utility score:
    * **+1:** AI Win
    * **-1:** Human Win
    * **0:** Draw
* **Result:** By propagating these scores back up the tree, the AI *always* chooses the move that leads to the best possible outcome (a win, or a draw if a win is impossible). This makes it mathematically unbeatable.

> **[Image: Screenshot of the 3x3 AI forcing a draw or winning]**
>
> *(**Developer Note:** Place a screenshot from `3x3 report.pdf` here to show the final board state of a draw or AI win.)*

---

## 👾 Part 2: The 7x7 "Heuristic" AI (Alpha-Beta Pruning)

This program (`7x7 AlphaBeta.c`) implements a 7x7 (4-in-a-row) version of the game.

### The Challenge
A 7x7 board is computationally infeasible to solve with a full Minimax search. The solution required two critical optimizations:

1.  **Alpha-Beta Pruning:** This optimization is implemented to "prune" (ignore) entire branches of the game tree that are guaranteed to be worse than a move already found. [cite_start]This dramatically reduces the number of nodes the algorithm needs to evaluate[cite: 5209, 5211].

2.  **Depth-Limited Search & Heuristic:**
    * The search is limited to a fixed depth (`DEPTH 7` in the code) to ensure a move is found in a reasonable time.
    * Because the search stops at non-terminal states (boards that aren't a win/loss/draw), a **heuristic evaluation function** is required to *estimate* how good a board is.
    * **My Heuristic:** The `evaluateBoard` function calculates a score based on the **number of 4-in-a-row winning opportunities** a player has. An AI win is `+N` (where N is the number of ways it wins) and a player win is `-N`, allowing the AI to prefer moves that create multiple threats or block the opponent's threats.

> **[Image: Screenshot of the 7x7 AI winning a game]**
>
> *(**Developer Note:** Place a screenshot from `7x7 report.pdf` showing a final 4-in-a-row win for the AI.)*

---

## 📊 Algorithm Comparison

| Feature | 3x3 AI (Perfect) | 7x7 AI (Heuristic) |
| :--- | :--- | :--- |
| **Algorithm** | Minimax | Minimax with Alpha-Beta Pruning |
| **Search** | Full Game Tree (Exhaustive) | Depth-Limited Search (e.g., 7 levels) |
| **Evaluation** | Terminal Nodes Only (+1, 0, -1) | Heuristic Function (counts 4-in-a-row threats) |
| **Result** | **Perfect / Unbeatable Play** | **Strong / Optimized Play** |

---

## 🚀 How to Compile & Run

### Prerequisites
* A C compiler (e.g., `gcc`)

### 1. Compile 3x3 Minimax
```bash
gcc "3x3 Minimax.c" -o tictactoe_3x3
```

### 2. Run 3x3 Minimax
```bash
./tictactoe_3x3
```

### 3. Compile 7x7 Alpha-Beta
```bash
gcc "7x7 AlphaBeta.c" -o tictactoe_7x7
```

### 4. Run 7x7 Alpha-Beta
```bash
./tictactoe_7x7
```