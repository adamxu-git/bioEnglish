# BIOSPELL - Biology Vocabulary Challenge

A spelling game for biology students to master professional English terminology. Single-file, zero-dependency web app — just open `spelling-game.html` in a browser.

## Game Modes

| Mode | Description |
|------|-------------|
| **SEQUENTIAL** | 10 words per round, covers all 97 words in order, loops automatically |
| **RANDOM** | 10 random words each time; practiced words get lower weight and appear less often |
| **REVIEW** | Focus on words you got wrong or close; count shown in real-time next to the button |
| **TIMED** | Race the clock; time limit calculated from word length + definition complexity (5–30s) |

## Features

- **Three result types**: CORRECT (green), CLOSE (orange, ~25% edit distance tolerance), INCORRECT (red)
- **IPA phonetics** displayed after answering
- **Auto-pronunciation** on answer reveal; click the word to replay
- **Chinese translation** toggle per question
- **Letter hint boxes** that update as you type
- **Progress dots** with click-to-review
- **Confetti** on correct answers
- **Per-word statistics** (attempts / correct / close / wrong) persisted in localStorage
- **Word Bank** panel: browse all words with stats, filter by lesson, search
- **Weight-based random**: correct ×0.5, close ×0.7, wrong ×0.8 (min 0.1)
- **End Round** button to exit mid-game; partial results shown
- **Hidden data reset**: click the title 5 times quickly on the home screen

## Vocabulary

97 terms across 5 lessons, stored in `words.json`:

| Lesson | Topic | Count |
|--------|-------|-------|
| Lesson 1 | Cell Structure & Function | 30 |
| Lesson 2 | Photosynthesis | 14 |
| Lesson 3 | Cell Division | 21 |
| Lesson 4 | Genetics | 17 |
| Lesson 5 | DNA Structure & Replication | 15 |

## Files

| File | Purpose |
|------|---------|
| `spelling-game.html` | The complete game (inline data + logic) |
| `words.json` | Editable word data source with phonetics |
| `words.js` | Auto-generated JS var from `words.json` |

To sync data after editing `words.json`:
```bash
node -e "require('fs').writeFileSync('words.js','var allWords='+JSON.stringify(JSON.parse(require('fs').readFileSync('words.json','utf8')),null,2)+';\n')"
```

## Tech

Pure HTML + CSS + vanilla JS. IBM Plex Mono font. Works with `file://` protocol — no server needed.
