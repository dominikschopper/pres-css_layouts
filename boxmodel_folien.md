
### Das CSS Box Model

---

## Folie 3: Display-Typen & Natürliche Größen

### Display bestimmt das Verhalten

#### Block-Level Elemente

```css
/* Standardverhalten */
div, p, h1, section, article {
  display: block;
  /* Nimmt volle verfügbare Breite */
  /* Höhe bestimmt sich durch Inhalt */
}
```

#### Inline-Level Elemente

```css
/* Standardverhalten */
span, a, strong, em {
  display: inline;
  /* Breite und Höhe durch Inhalt bestimmt */
  /* width/height werden ignoriert */
}
```

#### Inline-Block Hybrid

```css
.inline-block {
  display: inline-block;
  /* Wie inline, aber width/height funktionieren */
}
```

#### (Fast) Jedes Element ist eine Box

```html
<div class="example">Content hier</div>
```

```css
.example {
  width: 200px;          /* Content width */
  padding: 20px;         /* Innenabstand */
  border: 5px solid red; /* Rahmen */
  margin: 15px;          /* Außenabstand */
}
```

#### Die vier Bereiche
- **Content**: Der eigentliche Inhalt (Text, Bilder, etc.)
- **Padding**: Raum zwischen Content und Border
- **Border**: Sichtbarer Rahmen um das Element
- **Margin**: Abstand zu anderen Elementen

---

## Folie 2: Box-Sizing Verhalten

### content-box vs border-box

#### Standard: content-box

```css
.content-box {
  width: 200px;
  padding: 20px;
  border: 5px solid blue;
  /* Tatsächliche Breite: 200 + 40 + 10 = 250px */
}
```

#### Empfohlen: border-box

```css
.border-box {
  box-sizing: border-box;
  width: 200px;
  padding: 20px;
  border: 5px solid blue;
  /* Tatsächliche Breite: 200px (wie erwartet!) */
}
```

---

#### Global Border-Box Setup

```css
/* Moderne Best Practice */
*, *::before, *::after {
  box-sizing: border-box;
}

/* Alternative: Vererbung nutzen */
html {
  box-sizing: border-box;
}

*, *::before, *::after {
  box-sizing: inherit;
}
```

#### Warum border-box?
- ✅ **Intuitive Größenangaben** - width = tatsächliche Breite
- ✅ **Einfachere Berechnungen** - keine Mathematik nötig
- ✅ **Responsive Design** - Padding bricht das Layout nicht
- ✅ **Weniger Überraschungen** - wysiwyg

---

## Folie 4: Intrinsic vs Extrinsic Sizing

### Natürliche Größenbestimmung

#### Intrinsic Sizing (von innen nach außen)

```css
/* Element passt sich dem Inhalt an */
.auto-width {
  width: auto;        /* Standard - passt sich an */
  width: fit-content; /* Moderne Alternative */
  width: max-content; /* Nimmt maximalen Platz */
  width: min-content; /* Nimmt minimalen Platz */
}
```

#### Extrinsic Sizing (von außen bestimmt)

```css
/* Entwickler gibt Größe vor */
.fixed-width {
  width: 300px;    /* Feste Pixel-Werte */
  width: 50%;      /* Relativ zum Parent */
  width: 20em;     /* Relativ zur Schriftgröße */
}
```

---

#### Praktische Beispiele

```css
/* Schlechte Praxis: Über-spezifiziert */
.card-bad {
  width: 300px;
  height: 200px;
  padding: 20px;
  /* Was passiert bei mehr Content? */
}

/* Gute Praxis: Natürliches Sizing */
.card-good {
  width: 300px;
  padding: 20px;
  /* Höhe passt sich automatisch an */
}

/* Noch besser: Flexibles Design */
.card-flex {
  max-width: 300px;
  padding: 20px;
  /* Responsive ohne Media Queries */
}
```

---

## Folie 5: Moderne Sizing-Eigenschaften

### CSS Logical Properties & Neue Einheiten

#### Container-relative Einheiten

```css
.modern-sizing {
  /* Viewport-basiert */
  width: 50vw;      /* 50% der Viewport-Breite */
  height: 100vh;    /* 100% der Viewport-Höhe */

  /* Container-basiert (neu!) */
  width: 50cqw;     /* 50% der Container-Breite */
  height: 100cqh;   /* 100% der Container-Höhe */

  /* Flexible Größen */
  width: clamp(200px, 50%, 600px); /* min, preferred, max */
}
```

#### Aspect Ratio Control

```css
.video-container {
  aspect-ratio: 16/9; /* Seitenverhältnis beibehalten */
  width: 100%;        /* Breite flexibel */
  /* Höhe wird automatisch berechnet */
}

.square {
  aspect-ratio: 1;    /* Perfektes Quadrat */
  width: 200px;       /* Höhe wird 200px */
}
```

---

## Folie 6: Natürliches Layout mit weniger Code

### Weniger ist mehr

#### Traditioneller Ansatz (viel Code)

```css
/* Alte Schule: Alles fest definiert */
.old-layout {
  width: 300px;
  height: 200px;
  padding: 20px;
  margin: 10px;
  box-sizing: border-box;
  overflow: hidden;
}

.old-layout img {
  width: 260px;
  height: 160px;
  object-fit: cover;
}
```

---

#### Moderner Ansatz (weniger Code)

```css
/* Moderne Lösung: Natürliches Verhalten nutzen */
.modern-layout {
  max-width: 300px;
  padding: 20px;
  /* Höhe passt sich automatisch an */
  /* Box-sizing global gesetzt */
}

.modern-layout img {
  width: 100%;
  height: auto;
  /* Aspect-ratio beibehalten */
}
```

#### Vorteile des natürlichen Sizings
- ✅ **Weniger CSS-Code** zu schreiben und warten
- ✅ **Automatisch responsive** ohne Media Queries
- ✅ **Robuster** bei Content-Änderungen
- ✅ **Performance** - Browser optimiert natürliches Verhalten

---

## Folie 7: Praktische Design-Patterns

### Häufige Layout-Probleme elegant lösen

#### Problem: Card mit variablem Content

```css
/* Schlecht: Feste Höhen */
.card-bad {
  height: 200px;
  overflow: hidden; /* Content wird abgeschnitten */
}

/* Gut: Natürliche Höhe */
.card-good {
  min-height: 200px; /* Minimum, aber wächst bei Bedarf */
}

/* Besser: Flexbox nutzen */
.card-container {
  display: flex;
  align-items: stretch; /* Gleiche Höhen automatisch */
}
```

---

#### Problem: Responsive Images

```css
/* Schlecht: Feste Größen */
img {
  width: 300px;
  height: 200px; /* Verzerrt das Bild */
}

/* Gut: Natürliches Verhalten */
img {
  max-width: 100%;
  height: auto; /* Seitenverhältnis beibehalten */
}

/* Modern: Aspect-ratio nutzen */
.image-container {
  aspect-ratio: 3/2;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Bild füllt Container */
}
```

---

#### Problem: Text-Content sizing

```css
/* Schlecht: Feste Zeilen */
.text-bad {
  height: 3em;
  overflow: hidden;
  /* Text wird abgeschnitten */
}

/* Gut: Clamp für responsive Text */
.text-good {
  font-size: clamp(1rem, 2vw, 1.5rem);
  line-height: 1.5;
  /* Größe passt sich automatisch an */
}

/* Container Query für fortgeschrittene Kontrolle */
@container (width > 400px) {
  .text-responsive {
    font-size: 1.2rem;
  }
}
```

---

## Folie 8: Box Model Best Practices

### Zusammenfassung & Empfehlungen

#### ✅ Do's
- **Border-box global setzen** - macht Sizing vorhersagbar
- **Natürliche Dimensionen nutzen** - width: auto, height: auto
- **max-width statt width** - für responsive Designs
- **min-height statt height** - für flexible Content-Bereiche
- **aspect-ratio** für Medien-Container nutzen
- **clamp()** für responsive Spacing und Typography

#### ❌ Don'ts
- **Feste Höhen vermeiden** - außer bei spezifischen Fällen
- **Overflow: hidden als Layout-Fix** - löst das Problem nicht
- **!important für Box-Model** - deutet auf Architektur-Probleme hin
- **Pixel-perfekte Designs** in responsiven Umgebungen erzwingen

---

#### Tools für Box Model Debugging

```css
/* Debugging Helper */
* {
  outline: 1px solid red;    /* Zeigt alle Boxen */
}

/* Oder spezifischer */
.debug {
  background: rgba(255,0,0,0.1);
  outline: 1px solid red;
}
```

#### Browser DevTools nutzen
- **Elements Panel**: Box Model Visualisierung
- **Computed Tab**: Finale Werte sehen
- **Layout Tab**: Box Model interaktiv bearbeiten

**Nächster Schritt: Flexbox für 1D-Layouts! 🚀**
