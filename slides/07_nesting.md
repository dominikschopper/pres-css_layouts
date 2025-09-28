## CSS Nesting - Endlich nativ verfügbar!

**Das lange Warten hat ein Ende:**
- 20+ Jahre: Nur mit Preprocessors (SCSS, Less, Stylus)
- 2023: CSS Nesting nativ in Browsern
- Weniger Build-Tools nötig

**Native CSS Nesting:**
```css
.card {
  padding: 1rem;
  
  &:hover { box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
}
```

---

## CSS vs SCSS - Empfehlung heute

**Verwende natives CSS Nesting für:**
- ✅ Einfache Verschachtelung & Pseudo-Selektoren
- ✅ Moderne Projekte ohne Build-Step
- ✅ Prototyping & kleine Projekte

**Verwende SCSS weiterhin für:**
- 🔧 Mixins & Functions
- 🔧 Loops & Control Structures
- 🔧 Große Projekte mit komplexer Architektur

**Browser Support:** 79% global (Chrome 112+, Firefox 117+, Safari 16.5+)