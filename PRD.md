# PRD: chromedino

## Overview
A JavaScript console snippet that patches Chrome's built-in T-Rex dino game to prevent game-over. Useful for testing infinite-run behavior, generating high scores, or simply having fun. Target user: any Chrome user who wants to cheat the dino game without installing extensions.

## Goals
- Provide a copy-paste snippet that disables game-over in the Chrome dino game
- Provide a companion snippet to restore normal behavior
- Provide a speed control snippet

## Non-Goals
- Browser extension packaging
- Automation bots / AI-driven play
- Support for non-Chrome browsers
- High score submission or leaderboard manipulation

## User Stories
- As a Chrome user, I want to disable game-over so I can watch the dino run indefinitely.
- As a developer, I want to restore normal behavior after testing without refreshing the page.
- As a user, I want to set a custom game speed to stress-test the rendering.

## Tech Stack
- **Language**: JavaScript (vanilla, browser runtime)
- **Runtime**: Chrome DevTools Console
- **No build step, no dependencies**

## Architecture
Single file: `dino bot code.js` — three standalone JS one-liners with comments:
1. Store original `gameOver` reference
2. Override `gameOver` with no-op function
3. Restore original reference
4. Set speed via `Runner.instance_.setSpeed(n)`

## Features (detailed)

### Disable Game Over
- Capture `Runner.prototype.gameOver` in `original` variable
- Replace with empty function `function(){}`
- **Acceptance**: dino continues running after hitting obstacles

### Re-enable Game Over
- Restore `Runner.prototype.gameOver = original`
- **Acceptance**: dino dies normally on next obstacle hit

### Set Speed
- Call `Runner.instance_.setSpeed(n)` where n is a number
- Default game speed is ~6; `1000` is effectively infinite
- **Acceptance**: game visibly runs faster after call

## Data / Config
None — no files, no config, no persistent state.

## Deployment / Run
1. Open `chrome://dino` in Chrome
2. Open DevTools Console (`F12`)
3. Paste desired snippet and press Enter

## Constraints & Notes
- Chrome-only — relies on `Runner` global which is Chrome's internal dino game object
- Google may change internal API in Chrome updates, breaking the snippet
- No persistent effect — reloading the page resets everything
