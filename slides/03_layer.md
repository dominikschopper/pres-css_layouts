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

```css [1-2|4-6|8-11|13-16|18-21|]
/* order of layers -> important */
@layer reset, base, lib, utilities;

@layer reset {
  * { margin: 0; padding: 0; }
}

@layer base {
  body { font-family: system-ui; }
  h1 { font-size: 2rem; }
}

@layer lib {
  .btn { padding: 0.5rem 1rem; border: none; }
  .card { padding: 1rem; border-radius: 8px; }
}

@layer utilities {
  .text-center { text-align: center; }
  .hidden { display: none; }
}
```

---

### import foreign css into layers

you can also add external stylesheets into a specific layer in
your application

use the `layer(name)` function

```css
@layer reset, base, lib, utilities;

@import 'https://somewhere/some.css' layer(lib);
```

---

**Benefits:**
- Specificity becomes irrelevant
- Clear architecture layers
- overwriting is getting easier (no more specificity wars)

---

## @layer Browser Support

**Current support:**
- ✅ Chrome 99+ (March 2022)
- ✅ Firefox 97+ (February 2023)
- ✅ Safari 15.4+ (March 2022)
- ✅ Edge 99+ (March 2022)