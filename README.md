# chromedino

Live demo: https://hongyime.github.io/chromedino/

![Project screenshot](./screenshot.png)

> JavaScript snippet to make Chrome's T-Rex dino game run forever

## What it does
A two-line JavaScript snippet you paste into Chrome DevTools Console. It patches the `Runner.prototype.gameOver` method to do nothing, so the dinosaur never dies. An additional snippet lets you crank up the game speed.

## Features
- Disable game-over (dino never dies)
- Re-enable normal game-over behavior
- Set custom game speed (e.g., `1000` for warp speed)

## Usage
1. Open Chrome and navigate to `chrome://dino` (or just disconnect your internet)
2. Open DevTools (`F12` → Console)
3. Paste to disable game-over:
```js
var original = Runner.prototype.gameOver
Runner.prototype.gameOver = function(){}
```
4. To re-enable:
```js
Runner.prototype.gameOver = original
```
5. To set speed:
```js
Runner.instance_.setSpeed(1000)
```

## Requirements
- Google Chrome browser (any version with the built-in dino game)
- No installs needed

## Reference
Original technique: https://mathewsachin.github.io/blog/2016/11/05/chrome-dino-hack.html

## License

Apache-2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
