## CSS Cascade - The Fundamentals

**The complete Cascade order (lowest → highest priority):**
1. User Agent styles (browser defaults) <!-- .element class="fragment highlight-green" -->
2. User styles (user preferences) <!-- .element class="fragment highlight-green" -->
3. Author styles (your CSS) <!-- .element class="fragment highlight-green" -->
4. Author styles with `!important`<!-- .element class="fragment highlight-red" -->
5. User styles with `!important`<!-- .element class="fragment highlight-red" -->
6. User Agent styles with `!important`<!-- .element class="fragment highlight-red" -->

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