# Go — Browser-Based Board Game

<p align="center">
  <img src="assets/go-demo.svg" alt="Animated demo of the Go game: placing stones, capturing, and scoring" width="440">
</p>

A lightweight, single-file implementation of the classic strategy board game **Go** (also known as **Baduk** or **Weiqi**). Play as Black against a simple computer-controlled White opponent directly in your browser.

The game runs entirely in the browser. It requires no build step, dependencies, installation, or internet connection.

## Features

- Play as Black against a rule-based computer opponent playing White.
- Choose from **7×7**, **9×9**, and **13×13** board sizes.
- Place stones by clicking an empty board intersection.
- Capture individual stones and connected groups by removing all their liberties.
- Prevent illegal suicide moves, except when the move captures.
- Block repeated board positions using a basic repetition check.
- Pass a turn when no useful move remains; two consecutive passes end the game.
- Calculate scores using area scoring, including **6.5 komi** for White.
- Animate stone placement, captures, and end-game territory highlights.
- Preview legal moves with a faint stone under the pointer.
- Respect the operating system's reduced-motion preference.

## Getting Started

### Requirements

- A modern web browser (such as Chrome, Firefox, Safari, or Edge).
- No additional software or dependencies.

### Run locally

1. Clone this repository:

   ```bash
   git clone https://github.com/aayantcsc-spec/go-.git
   ```

2. Open the project folder:

   ```bash
   cd go-
   ```

3. Open `go.html` in your browser.

You can also download `go.html` from the repository and open it directly. No local server is required.

## How to Play

1. You play **Black** and make the first move.
2. Click an empty intersection to place a black stone.
3. The computer responds automatically with a white stone.
4. Surround opposing stones or groups to remove all their liberties and capture them.
5. Select **Pass** when you have no useful move remaining.
6. The game ends after both players pass consecutively.

### Rules implemented

| Rule | Description |
| --- | --- |
| Liberties | Empty points directly adjacent horizontally or vertically to a stone or connected group. |
| Captures | A group with no remaining liberties is removed from the board. |
| No suicide | A move that leaves your own group without liberties is illegal unless it captures. |
| Repetition | A move cannot recreate a board position that has already occurred in the game. |
| Passing | Two consecutive passes end the game. |
| Scoring | Each player's stones and exclusively surrounded empty points count toward their area. |
| Komi | White receives 6.5 points to compensate for moving second. |

## Board Sizes

| Size | Intended use |
| --- | --- |
| **7×7** | Quick games and learning the basics. |
| **9×9** | Default size; a good balance for casual play. |
| **13×13** | Longer games with more room for strategy. |

Changing the board size starts a new game.

## Scoring

The game uses **area scoring**:

- Each stone still on the board counts for its owner.
- An empty region counts as territory when it is surrounded exclusively by one player's stones.
- White receives an additional **6.5 komi points**.

At the end of the game, the areas identified as territory are marked on the board. The computer does not reliably identify dead groups, so continue playing to capture them before passing.

## Computer Opponent

The computer is a simple rule-based player, not a strong Go engine. On each turn, it evaluates legal moves and chooses the one with the best score.

Its preferences include:

- Capturing opponent stones.
- Putting opponent groups in atari (one liberty remaining).
- Saving its own groups that are in atari.
- Playing near the centre and near existing stones.
- Avoiding filling its own eyes.
- Avoiding moves that leave its own groups in atari.

The computer may pass when it has no worthwhile move, or when you have passed and it is already ahead. Experienced Go players will likely beat it; it is intended for casual play and learning the basic rules.

## Animations and Accessibility

The game includes:

- A pop animation when a stone is placed.
- A shrink-and-fade effect when stones are captured.
- Territory highlights that fade in when the game ends.
- A faint preview stone over legal intersections.

Animations are automatically disabled when the system requests reduced motion.

> The animated board at the top of this README (`assets/go-demo.svg`) is a scripted illustration of these effects, not a recording of a real game.

## Technology

The project uses standard browser technologies:

- **HTML** for the page structure.
- **CSS** for layout, appearance, and animations.
- **JavaScript** for the game rules, scoring, and computer opponent.

There are no external libraries or frameworks.

## Project Structure

```text
go-/
├── assets/
│   └── go-demo.svg   # Animated demo shown in this README
├── go.html           # Complete game: HTML, CSS, and JavaScript
└── README.md         # Project documentation
```

## Known Limitations

- There is no undo feature or handicap-stone support.
- Repeated positions are blocked by checking earlier board positions. This is a basic repetition check, not an exact implementation of every Go ruleset's ko and superko rules.
- The computer cannot reliably determine which groups are dead at the end of the game.
- The computer opponent is intentionally simple and is not designed for competitive play.

## Possible Future Improvements

- Undo and redo moves.
- Multiple computer difficulty levels.
- Two-player local mode.
- Move history and game replay.
- Save and resume games.
- Hints and move suggestions.
- A stronger computer opponent.

## Repository

<https://github.com/aayantcsc-spec/go->

## License

Choose and add a license before distributing the project. If this project is published as part of another repository with an applicable license, follow that repository's licensing terms.

---

**Enjoy the game!**  
*Think strategically. Control territory. Capture wisely.*
