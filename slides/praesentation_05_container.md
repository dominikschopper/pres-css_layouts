## Container Queries - Das Problem

**Warum so lange schwierig?**
- Media Queries: Viewport-basiert
- Problem: Komponenten kennen ihren Container nicht
- 20+ Jahre CSS ohne echte Komponenten-Responsiveness

**Media Queries helfen nicht:**
```css
@media (min-width: 600px) {
  .card { font-size: 18px; }
  /* Aber Sidebar-Cards auch! */
}
```

---

## Container Queries - Die Lösung

**Setup:**
```css
.card-container {
  container-type: inline-size;
}
```

**Responsive Komponente:**
```css
@container (min-width: 300px) {
  .card { display: grid; }
}
```

---

## Container Queries - Praktische Beispiele

**Kleine Container: Stack Layout**
```css
@container (max-width: 400px) {
  .article { display: block; }
}
```

**Große Container: Grid Layout**
```css
@container (min-width: 500px) {
  .article {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}
```

---

## Container Queries - UX/Design Möglichkeiten

**Neue Design-Patterns:**
- **Intrinsic Web Design:** Komponenten passen sich ihrem Raum an
- **Contextual Responsiveness:** Sidebar vs Main Content unterschiedlich
- **Progressive Enhancement:** Mehr Platz = mehr Features

**Entwickler-Vorteile:**
- Echte Komponentenisolation
- Keine globalen Media Query Konflikte
- Testbare, vorhersagbare Layouts

---

## Container Queries - Advanced Features

**Container Query Units:**
```css
.card {
  font-size: 4cqw;  /* 4% der Container-Breite */
  padding: 2cqh;    /* 2% der Container-Höhe */
}
```

**Multi-Dimensional Queries:**
```css
@container (min-width: 400px) and (min-height: 300px) {
  .card { aspect-ratio: 16/9; }
}
```

---

## Container Queries Browser Support

**Aktuelle Unterstützung:**
- ✅ Chrome 106+ (September 2022)
- ✅ Firefox 110+ (Februar 2023)
- ✅ Safari 16+ (September 2022)
- 📊 **Can I Use: 84% global support**