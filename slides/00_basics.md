### CSS Reset / Normalize

#### Problem
- Each and every browser has its own default styles
- So we have inconsistent behaviour for different browser
- e.g. margins, font-sizes, font-family might differ

---

#### Modern CSS Reset

```css[2-4]
/* Moderner Reset */
*, *::before, *::after {
  box-sizing: border-box;
}

* {
  margin: 0;
}

body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}

img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}
```

[Josh Comeaus Reset](https://www.joshwcomeau.com/css/custom-css-reset/)


---


## Folie 3: CSS Cascade

---

### The order of (css) things

|   |  Origin                 |
|---|-------------------------|
| 1 | user-agent              |
| 2 | user                    |
| 3 | author __(we!)__        |
| 4 | CSS keyframe animations |

<div class="fragment c-orange" style="margin-left: -12px; padding: 0">

|   |                         |
|---|-------------------------|
| 5 | `!important` author     |
| 6 | `!important` user       |
| 7 | `!important` user-agent |

</div>

|   |                         |
|---|-------------------------|
| 8 | CSS transitions ˘˘˘˘˘˘˘˘˘˘˘˘ |

---

#### The order of (css) things 2

1. **Cascade**
2. **Specificity**
3. **Source Order**

---

#### Cascade in Aktion

```css
/* Diese Regeln überschreiben sich */
p { color: blue; }          /* 0-0-0-1 */
.text { color: red; }       /* 0-0-1-0 */
#content p { color: green; } /* 0-1-0-1 */

/* Ergebnis: grün (höchste Spezifität) */
```

---

## Folie 4: Specificity Calculation

### Spezifität berechnen

#### Spezifitäts-Kategorien

| Kategorie | Wert | Beispiel |
|-----------|------|----------|
| **Inline Styles** | 1000 | `style="color: red"` |
| **IDs** | 100 | `#header` |
| **Classes, Attributes, Pseudo-classes** | 10 | `.nav`, `[type="text"]`, `:hover` |
| **Elements, Pseudo-elements** | 1 | `div`, `::before` |

---

#### Spezifitäts-Beispiele

```css
/* Spezifitäts-Berechnung */
h1                           /* 0-0-0-1 = 1 */
.navigation ul li a          /* 0-0-1-3 = 13 */
#header .logo               /* 0-1-1-0 = 110 */
div#content .article p.intro /* 0-1-2-2 = 122 */
style="color: red"          /* 1-0-0-0 = 1000 */
```

#### ⚠️ Spezifitätskriege vermeiden!
- Verwenden Sie `!important` sparsam
- Schreiben Sie CSS von allgemein zu spezifisch
- Nutzen Sie CSS Layers für bessere Kontrolle

---

## Folie 5: CSS @layer

### CSS @layer - Moderne Architektur

#### Layer-Definition

```css
/* Layer-Reihenfolge definieren */
@layer reset, base, components, utilities;

@layer reset {
  * { margin: 0; padding: 0; }
}

@layer base {
  body { font-family: system-ui; }
  h1 { font-size: 2rem; }
}

@layer components {
  .btn { padding: 0.5rem 1rem; border: none; }
  .card { padding: 1rem; border-radius: 8px; }
}

@layer utilities {
  .text-center { text-align: center; }
  .hidden { display: none; }
}
```

---

#### Layer-Hierarchie

```
🔝 Utilities Layer    (höchste Priorität)
   Components Layer
   Base Layer
🔻 Reset Layer        (niedrigste Priorität)
```

#### Vorteile von @layer
- **Spezifität wird irrelevant** innerhalb der Layer-Reihenfolge
- **Klare Architektur-Ebenen** wie bei CSS-Frameworks
- **Bessere Wartbarkeit** und Vorhersagbarkeit
- **Konflikte vermeiden** zwischen verschiedenen CSS-Bereichen

---

## Folie 6: Browser Support & Tools

### Browser Support & Debugging

#### CSS @layer Browser Support
- ✅ **Chrome 99+** (März 2022)
- ✅ **Firefox 97+** (Februar 2022)
- ✅ **Safari 15.4+** (März 2022)
- 🔄 **Polyfill verfügbar** für ältere Browser

#### Progressive Enhancement

```css
/* Fallback für ältere Browser */
.btn {
  padding: 0.5rem 1rem;
}

/* Mit @layer für moderne Browser */
@supports (color: color(display-p3 1 0 0)) {
  @layer components {
    .btn { padding: 0.5rem 1rem; }
  }
}
```

---

#### Debugging Tools

| Tool                           | Feature              | Nutzen                       |
|--------------------------------|----------------------|------------------------------|
| **outline**                    | outline 4tw          | Elementgrenzen sehen         |
| **background-color**           | semi transparent     | Elementgrenzen & Überlappung |
| **Chrome DevTools**            | Computed Tab         | Zeigt Spezifität und Cascade |
| **Firefox DevTools**           | Layer-Visualisierung | @layer Debugging             |
| **CSS Specificity Calculator** | Online Tools         | Spezifität berechnen         |
| **Lighthouse**                 | Performance-Audit    | CSS-Performance optimieren   |

#### 🎯 Best Practices Zusammenfassung
- CSS Reset/Normalize verwenden
- `box-sizing: border-box` global setzen
- @layer für saubere Architektur
- Spezifitätskriege vermeiden
- Progressive Enhancement nutzen


---

## Folie 2: Box Model

### Box Model Grundlagen

#### Komponenten des Box Models
- **Content**: Der eigentliche Inhalt
- **Padding**: Innenabstand
- **Border**: Rahmen
- **Margin**: Außenabstand

---

#### Box-Sizing Verhalten

```css
/* Standard Box Model */
width = content

/* Border Box Model (empfohlen!) */
width = content + padding + border

/* Global setzen */
*, *::before, *::after {
  box-sizing: border-box;
}
```

#### Warum border-box?
- Predictable sizing
- Einfachere Berechnungen
- Weniger Layout-Überraschungen

---

## Übergang zu Layouts

### Nächste Schritte

**Grundlagen geschafft!** 🎉

Jetzt sind wir bereit für:
- **Flexbox** - 1D Layouts
- **CSS Grid** - 2D Layouts
- **Moderne Layout-Patterns**
- **Komponenten-Integration**

**Fragen zu den Grundlagen?**