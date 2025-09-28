## :has() - Der "Parent Selector"

**Das jahrelange Problem:**
- CSS konnte nur "nach unten" selektieren
- Kein Parent-Selector in CSS
- JavaScript für Parent-Styling nötig

**:has() löst das Problem:**
```css
.form:has(.error) { border: 2px solid red; }
.card:has(img) { display: grid; }
```

---

## :has() Praktische Anwendungen

**Form Validation ohne JavaScript:**
```css
.form-group:has(input:invalid) {
  border-left: 3px solid red;
}
```

**Quantity Queries:**
```css
.grid:has(li:nth-child(3):not(:nth-child(4))) {
  justify-content: center;
}
```

---

## :has() Browser Support

**Aktuelle Unterstützung:**
- ✅ Chrome 105+ (September 2022)
- ✅ Firefox 121+ (Dezember 2023)
- ✅ Safari 15.4+ (März 2022)
- 📊 **Can I Use: 87% global support**