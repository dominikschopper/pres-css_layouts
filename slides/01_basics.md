### CSS Reset / Normalize

#### Problem
- <!-- .element class="c-purple"  --> the default sizing is <code>box-sizing: content-box</code>
- an `img` is not `display:block`?
- the `input` has some weird `font` presets
- e.g. margins, font-sizes, font-family might differ
- thus inconsistent behaviour for different browser
- each and every browser has its own default styles

---

#### `content-box` vs `border-box`

```css
.box {
    border: 1px solid black;
    padding: 20px;
    width: 220px;
}
```

![box-sizing comparison](./slides/slide-assets/contentbox-borderbox.jpg)

---

### Reset Example

<a href="./xmp/00_box-model/index.html" target=_blank>some local code to fiddle</a>

---

#### Modern CSS Reset (partial)

```css
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

[Josh Comeaus full CSS Reset](https://www.joshwcomeau.com/css/custom-css-reset/) (with explanations)

