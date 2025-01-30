# `noise()` 

The `noise()` function that generates smooth, natural-looking randomness. Unlike `random()`, which gives unpredictable values, `noise()` creates gradual changes, making it useful for animations and textures.

## Basic Usage
The `noise()` function returns a value between `0` and `1` for a given input.

```javascript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  let foo = noise(0.005 * frameCount) * 255;
  fill(foo);
  rect(100, 100, 100);
}
```

### Explanation:
- `noise(0.005 * frameCount)` creates a smooth, gradually changing value.
- The value is multiplied by `255` to get a range suitable for colors.
- `fill(foo)` sets the rectangle color based on the noise value.
- The rectangle size also changes with the noise value, making it grow and shrink smoothly.

## Using Noise for Movement
You can use `noise()` to create smooth motion in animations.

```javascript
let xoff = 0;
let cy

function setup() {
  createCanvas(400, 400);
  cy=height / 2
}

function draw() {
  background(220);
  let x = noise(xoff) * width;
  ellipse(x, cy , 40, 40);
  xoff += 0.01;
}
```

### Explanation:
- `noise(xoff)` smoothly changes the x position of the ellipse.
- `xoff` increases gradually to create continuous motion.

## 2D Noise Pattern
You can use two inputs to `noise()` to create patterns.

```javascript
function setup() {
  createCanvas(400, 400);
  noLoop();
}

function draw() {
  background(220);
  for (let y = 0; y < height; y++) {
    for (let x = 0; x < width; x++) {
      let bright = noise(x * 0.02, y * 0.02) * 255;
      stroke(bright);
      point(x, y);
    }
  }
}
```

### Explanation:
- `noise(x, y)` creates a smooth texture across the canvas.
- The brightness of each pixel is determined by the noise value.
