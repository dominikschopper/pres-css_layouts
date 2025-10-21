## Container Queries - The Problem

**Why so difficult for so long?**
- Media Queries: Viewport-based
- Problem: Components don't know their container
- 20+ years of CSS without true component responsiveness

**Media Queries don't help:**
```css
@media (min-width: 600px) {
  .card { font-size: 18px; }
  /* But sidebar cards too! */
}
```

---

## Container Queries - The Solution

**Setup:**
```css
.card-container {
  container-type: inline-size;
}
```

**Responsive component:**
```css
@container (min-width: 300px) {
  .card { display: grid; }
}
```

---

## Container Queries - Practical Examples

**Small container: Stack layout**
```css
@container (max-width: 400px) {
  .article { display: block; }
}
```

**Large container: Grid layout**
```css
@container (min-width: 500px) {
  .article {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}
```

---

## Container Queries - UX/Design Possibilities

**New design patterns:**
- **Intrinsic Web Design:** Components adapt to their space
- **Contextual Responsiveness:** Sidebar vs Main Content differently
- **Progressive Enhancement:** More space = more features

**Developer advantages:**
- True component isolation
- No global media query conflicts
- Testable, predictable layouts

---

## Container Queries - Advanced Features

**Container Query Units:**
```css
.card {
  font-size: 4cqw;  /* 4% of container width */
  padding: 2cqh;    /* 2% of container height */
}
```

**Multi-dimensional queries:**
```css
@container (min-width: 400px) and (min-height: 300px) {
  .card { aspect-ratio: 16/9; }
}
```

---

## Container Queries Browser Support

**Current support:**
- ✅ Chrome 106+ (September 2022)
- ✅ Firefox 110+ (February 2023)
- ✅ Safari 16+ (September 2022)
- 📊 **Can I Use: 84% global support**