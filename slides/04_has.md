## :has() - The "Parent Selector"

**The long-standing problem:**
- CSS could only select "downward"
- No parent selector in CSS
- JavaScript needed for parent styling

**:has() solves the problem:**
```css
.form:has(.error) { border: 2px solid red; }
.card:has(img) { display: grid; }
```

---

## :has() Practical Applications

**Form validation without JavaScript:**
```css
.form-group:has(input:invalid) {
  border-left: 3px solid red;
}
```

**Quantity queries:**
```css
.grid:has(li:nth-child(3):not(:nth-child(4))) {
  justify-content: center;
}
```

---

## :has() Browser Support

**Current support:**
- ✅ Chrome 105+ (September 2022)
- ✅ Firefox 121+ (December 2023)
- ✅ Safari 15.4+ (March 2022)
- 📊 **Can I Use: 87% global support**