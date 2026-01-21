# US States Geography Quiz - Product Requirements Document

## Overview
A lightweight, colorful web application to help a 10-year-old learn to identify all 50 US states by their shapes and locations on a map.

## Target User
- **Age:** 10 years old
- **Device:** iPad (touch-optimized)
- **Goal:** Pass a geography test by correctly labeling all US states on a blank map

---

## Core Features

### Quiz Modes (4 Types)

| Mode | Description | Difficulty |
|------|-------------|------------|
| **1. Full Map Label** | Tap any state on a complete US map, type its name | Hardest |
| **2. Single State ID** | See one state outline, type its name | Medium-Hard |
| **3. Name from Choices** | See one state outline, pick correct name from 3 options | Medium |
| **4. Shape from Choices** | See a state name, pick correct outline from 3 options | Easiest |

### Mode Selection
- **Choose Mode:** User picks one of the four modes
- **Random Mode:** System randomly cycles through all four modes

### Progress Tracking (Persistent)
- Track correct/incorrect answers per state
- Identify "struggle states" (frequently missed)
- Show mastery level per state (0-5 stars based on consecutive correct answers)
- Display overall progress (X/50 states mastered)
- Data persists across browser sessions using localStorage

### Feedback System
- **Correct:** Celebratory animation (confetti, stars), encouraging message, state turns green
- **Incorrect:** Gentle feedback, show correct answer, state highlights for learning, offer retry
- **Session Summary:** End-of-session report showing score and improvement

---

## UI/UX Requirements

### Visual Style: Colorful & Playful
- Bright, friendly color palette (blues, greens, oranges, purples)
- Large touch-friendly buttons (minimum 44px tap targets)
- Rounded corners, soft shadows
- Fun animations on interactions
- Clear, readable fonts (minimum 18px for body text)

### iPad Optimization
- Responsive design that works in both orientations
- Touch-optimized (no hover-dependent interactions)
- No tiny click targets
- Smooth scrolling and transitions

### Kid-Friendly Elements
- Encouraging language ("Great job!", "You're getting better!", "Try again!")
- No harsh failure states
- Progress feels rewarding (stars, progress bars filling up)
- Simple navigation (minimal clicks to start learning)

---

## Technical Approach

### Stack
- **Single HTML file** with embedded CSS and JavaScript (React via CDN)
- No build step required
- Works offline after initial load
- Easy to deploy (just open the file or host anywhere)

### Data
- 50 US states with SVG path data for outlines
- State metadata (name, abbreviation, region)
- Progress stored in localStorage

### Deployment
- Host as a single file on any web server
- Can be opened directly from Files app on iPad
- Add to Home Screen for app-like experience

---

## Success Metrics
- Child can correctly identify all 50 states
- Sessions are engaging (10+ minutes of use)
- Measurable improvement in "struggle states" over time

---

## Out of Scope (For Now)
- State capitals
- Other geographic features
- Multiplayer/leaderboards
- Account/login system
