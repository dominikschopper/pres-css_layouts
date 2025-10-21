## CSS Cascade - The Fundamentals

**The complete Cascade order (lowest → highest priority):**
1. User Agent styles (browser defaults) <!-- .element class="fragment highlight-blue" -->
2. User styles (user preferences) <!-- .element class="fragment highlight-blue" -->
3. Author styles (your CSS) <!-- .element class="fragment highlight-blue" -->
4. Author <!-- .element class="fragment highlight-red" --> styles with `!important`
5. User <!-- .element class="fragment highlight-red" --> styles with `!important`
6. User <!-- .element class="fragment highlight-red" --> Agent styles with `!important`

---

## Later rules win!


```html
<p class="warning">lorem ipsum</p>
```

author styles
```css
.warning { color: red; }
```

`!important` author styles
```css
p { color: black !important; }
```
Text will be black!

---

## Within each Cascade layer

**When multiple rules have the same cascade priority:**

1. **Specificity** determines the winner:
   - Inline styles (1000) > IDs (100) > Classes (10) > Elements (1)
2. **Source order** as final tiebreaker:
   - Later in the code wins

**Examples:**
```css
p { color: blue; }           /* 0001 */
#header .logo { color: red; } /* 0110 - wins */
```