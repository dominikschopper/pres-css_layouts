### CSS Reset / Normalize

#### Problem
- Each and every browser has its own default styles
- an `img` is not `display:block`?
- the `input` has some weird `font` presets
- e.g. margins, font-sizes, font-family might differ
- So we have inconsistent behaviour for different browser

---

#### Modern CSS Reset

```css[2-4|5-7|9-11|13-16|]
/* Moderner Reset */
*, *::before, *::after {
  box-sizing: border-box;
}

* {
  margin: 0;
}

input, button, textarea, select {
  font: inherit;
}

img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}
```

[Josh Comeaus Reset](https://www.joshwcomeau.com/css/custom-css-reset/)

---
#### `border-bx` vs `content-box`

```css
.box {
    border: 1px solid black;
    padding: 20px;
    width: 220px;
}
```

![box-sizing comparison](./slides/contentbox-borderbox.jpg)
