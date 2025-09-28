## CSS Cascade - Die Grundlagen

**Die 4 Stufen der Cascade:**
1. **Origin** (User Agent → User → Author)
2. **Importance** (!important)
3. **Specificity** (Inline → IDs → Classes → Elements)
4. **Source Order** (später gewinnt)

---

## Spezifität berechnen

**Spezifitäts-Score:**
- Inline Styles: **1000** Punkte
- IDs: **100** Punkte  
- Classes/Attributes/Pseudo: **10** Punkte
- Elements: **1** Punkt

**Beispiele:**
```css
p                    /* 0001 */
#header .logo        /* 0110 */
```

**Problem:** Spezifitätskriege mit `!important`