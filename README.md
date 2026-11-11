# Minesweeper AI

A graphical Minesweeper game built with Python and Pygame, featuring an AI player that tracks known safe cells and mines and derives new facts from its knowledge base.

This project is a good portfolio piece for demonstrating Python fundamentals, object-oriented design, set-based state management, and basic logical inference. It is currently best presented as an academic or learning project; adding automated tests, improving the AI's strategy, and documenting design decisions would make it stronger for a software engineering résumé.

## Features

- 8 × 8 Minesweeper board with 8 randomly placed mines.
- Click to reveal a cell and right-click to flag or unflag it.
- AI move button that chooses a known-safe cell when possible, then falls back to a random move that is not known to be a mine.
- Reset button to start a new game.
- Rule-based AI knowledge with subset-based sentence inference.

## Requirements

- Python 3.9 or newer
- Pygame

## Run locally

```bash
git clone <repository-url>
cd minesweeper
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
python -m pip install -r requirements.txt
python src/runner.py
```

## How to play

1. Select **Play Game** to begin.
2. Left-click a cell to reveal it.
3. Right-click a hidden cell to toggle its flag.
4. Select **AI Move** to let the agent choose a move.
5. Select **Reset** to start over.

The game ends when a mine is revealed. The win condition is flagging all mines.

## Project structure

```text
.
├── src/
│   ├── minesweeper.py   # Board, sentence, and AI logic
│   └── runner.py        # Pygame interface and game loop
├── requirements.txt
├── .gitignore
├── LICENSE
└── README.md
```

## AI overview

The agent stores logical sentences in the form “these cells contain this many mines.” After a safe cell is revealed, it removes known safe cells and known mines from neighboring candidates, then checks for subset relationships between sentences to infer additional facts. It prioritizes known-safe moves; when none are available, it makes a random move excluding cells already selected or known to contain mines.

## License

Distributed under the MIT License. See [LICENSE](LICENSE).
