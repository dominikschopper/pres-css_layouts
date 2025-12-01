## CSS Cascade - The Fundamentals

**The complete Cascade order (lowest → highest priority):**
1. User Agent styles (browser defaults) <!-- .element class="fragment highlight-blue" -->
2. User styles (user preferences) <!-- .element class="fragment highlight-blue" -->
3. Author styles (your CSS) <!-- .element class="fragment highlight-blue" -->
4. Author <!-- .element class="fragment highlight-red" --> styles with `!important`
5. User <!-- .element class="fragment highlight-red" --> styles with `!important`
6. User <!-- .element class="fragment highlight-red" --> Agent styles with `!important`

---

## Within each Cascade layer
**When multiple rules are in the same cascade layer:**

**Specificity** determines the winner:

Inline styles (1000) > IDs (100) > Classes (10) > Elements (1)

**Examples:**
```css
p { color: blue; }       /* 0001 */
.warning { color: red; } /* 0010 <- wins */
```

```css
.highlight          { color: blue; }   /* 0010 */
.warning .highlight { color: red; }    /* 0020 */
#header .highlight  { color: purple; } /* 0110 <- wins */
```
<!-- .element class="fragment" -->

```css
p { color: fuchsia !important; } /* <- new layer wins */
```
<!-- .element class="fragment" -->

---

### Example

<a href="./xmp/02_cascade/index.html" target=_blank>some local code to fiddle with the cascade</a>

We added a user stylesheet to firefox and added an `!important` rule, so it cannot be
overriden by author styles

```css
* {
	color: limegreen !important;
	background: rgb(111, 31, 111) !important;
}
```
