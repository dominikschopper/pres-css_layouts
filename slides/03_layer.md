## @layer - Modern CSS Architecture

**The problem without @layer:**
- Specificity determines everything
- CSS order is critical
- Conflicts between team CSS and libraries

**The solution:**
```css
@layer reset, base, components, utilities;
```

---

### CSS @layer - Moderne Architektur

#### Layer-Definition

```css [1-2|4-7|9-11|13-15|17-19| ]
/* order of layers less -> more important */
@layer reset, base, components, utilities;

@layer reset {
  body { font-size: 16px; }
  * { margin: 0; } /* e.g. the reset we've seen */
}

@layer components {
  h2 { margin: 1rem 0; font-size: 1.25rem; }
}

@layer base {
  h2 { margin: 1.5rem 0; font-size: 1.5rem; }
}

@layer utilities {
  h2 { margin: 1.25rem 0; }
}
```

---

### import foreign css into layers

you can also add external stylesheets into a specific layer in your application

use the `layer(name)` function

```css
@layer reset, base, components, utilities;

@import 'https://somewhere/some.css' layer(components);
```

---

**Benefits:**
- Specificity becomes irrelevant
- Clear architecture layers
- overwriting is getting easier

---

## @layer Browser Support

**Current support:**
- Chrome 99+ (March 2022)
- Firefox 97+ (February 2023)
- Safari 15.4+ (March 2022)
- Edge 99+ (March 2022)