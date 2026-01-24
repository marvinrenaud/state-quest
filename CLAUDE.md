# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**State Quest** - A US States geography quiz app for kids (target age: 10). iPad-optimized, touch-friendly educational app to help learn all 50 US states by shape and location.

## Architecture

Single-file React application (`us-states-quiz-v3.html`) with no build step:
- **~1950 lines** of embedded HTML, CSS, and JSX
- React 18 via CDN with Babel for in-browser JSX transformation
- All state data (SVG paths, metadata) embedded in the file
- localStorage for persistence (history, best times)
- URL hash-based navigation between modes

### Key Sections (by line range)

- **Lines 1-800**: CSS styles and state SVG path data (`STATES_ARRAY`)
- **Lines 800-950**: Utility functions, localStorage helpers, shared components (Confetti, FeedbackOverlay)
- **Lines 950-1100**: `USMap` component - renders the full interactive US map
- **Lines 1100-1450**: `FullMapQuiz`, `SingleStateQuiz` components
- **Lines 1450-1610**: `NameChoicesQuiz`, `ShapeChoicesQuiz` components (multiple choice modes)
- **Lines 1610-1800**: `MysteryQuiz` component (mixed mode combining all question types)
- **Lines 1800-1950**: `App` component, mode selection, progress tracking UI

### Quiz Modes

| Mode | Component | Description |
|------|-----------|-------------|
| `fullMap` | FullMapQuiz | Tap state on map, type name |
| `singleState` | SingleStateQuiz | See outline, type name |
| `nameChoices` | NameChoicesQuiz | See outline, pick name from buttons |
| `shapeChoices` | ShapeChoicesQuiz | See name, pick shape from buttons |
| `mystery` | MysteryQuiz | Randomly mixes all above types |

### State Management Pattern

Each quiz component follows the same pattern:
- `queue` - shuffled array of 50 states
- `index` - current question (0-49)
- `choices` - current button options (for choice modes)
- `feedback` - controls FeedbackOverlay visibility and content
- `selected` - tracks user's button selection

## Development

No build commands. Open `us-states-quiz-v3.html` directly in a browser or serve via any static file server.

```bash
# Quick local server
python3 -m http.server 8000
# Then open http://localhost:8000/us-states-quiz-v3.html
```

`index.html` is just a redirect to `us-states-quiz-v3.html`.

## Common Bug Patterns

**Button state persistence between turns**: When fixing issues with buttons showing stale CSS classes (correct/incorrect colors) between questions, ensure React keys include the question `index` (e.g., `key={\`${index}-${choice.id}\`}`) to force remounting on turn change.

**Race conditions in handleNext()**: State updates (`setFeedback`, `setSelected`, `setIndex`, `setChoices`) are batched by React. If UI shows stale state, consider the render order of these updates.
