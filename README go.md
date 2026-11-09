# Go

A single-file Go game that runs in the browser. You play black against a simple computer opponent.

## Running it locally

Download `go.html` and open it in any modern browser. It needs no build step, no dependencies and no internet connection.

## How it plays

You play black and move first. Click an intersection to place a stone. The computer plays white.

The game follows these rules:

- **Captures:** a stone or connected group with no empty neighbouring points is removed from the board.
- **No suicide:** you can't make a move that leaves your own group without liberties, unless the move captures.
- **No repeated positions:** you can't recreate a board position that has already occurred in the game.
- **Passing:** press **Pass** when you have nothing useful left to play. The game ends when both sides pass.

## Animation

- Stones pop onto the board when placed.
- Captured stones shrink and fade away.
- The surrounded areas fade in when the game ends.
- A faint preview stone follows your pointer over legal moves.

Animations are switched off automatically if your system is set to reduce motion.

## Board sizes

| Size  | Notes                         |
|-------|-------------------------------|
| 7×7   | Quick games, good for a first try |
| 9×9   | Default                       |
| 13×13 | Longer games                  |

Changing the size starts a new game.

## Scoring

The game uses area scoring. Each side's score is:

- the number of its stones on the board, plus
- the empty areas that only that side surrounds.

White receives 6.5 points of komi to make up for moving second, so a tie is impossible. When the game ends, the areas each side has surrounded are marked on the board with small squares.

## The computer opponent

The computer is a simple rule-based player, not a strong engine. Each turn it scores every legal move and plays the best one. It prefers moves that:

- capture stones,
- put your groups in atari (one liberty left),
- save its own stones that are in atari,
- stay near the centre and near existing stones.

It avoids filling its own eyes and avoids moves that leave its own group in atari. It passes when it has no worthwhile move left, or when you have passed and it is already ahead. An experienced player will probably beat it, but it is useful for learning the rules.

## Known limitations

- There is no undo, and there are no handicap stones.
- Repeated positions are blocked with a basic check against all earlier positions, rather than the exact ko rules of any particular rule set.
- The computer can't judge which groups are dead at the end, so you may need to keep playing to capture them before passing.

## Files

- `go.html`: the whole game (HTML, CSS and JavaScript in one file)
- `README.md`: this file

## Licence

Add the licence of your choice here. If you publish this inside the `jpneto/board_games` repository, it falls under that repository's MIT licence.
