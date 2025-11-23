## CSS Nesting - Finally available natively!

**The long wait is over:**
- 20+ years: Only with preprocessors (SCSS, Less, Stylus)
- 2023: CSS Nesting native in browsers
- Fewer build tools needed

**Native CSS Nesting:**
```css
.card {
  padding: 1rem;

  &:hover { box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
}
```

---

## CSS vs SCSS - Recommendation today

**Use native CSS Nesting for:**
- Simple nesting & pseudo-selectors
- Modern projects without build step
- Prototyping & small projects

**Continue using SCSS for:**
- &rArr; Mixins & Functions
- &rArr; Loops & Control Structures
- &rArr; Large projects with complex architecture

---

**Current support:**
- Chrome 112+ (April 2023)
- Firefox 117+ (August 2023)
- Safari 16.5+ (May 2023)
- **Can I Use: 79% global support**
