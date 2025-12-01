## :has() - The "Parent Selector"

**The long-standing problem:**
- CSS could only select "downward"
- No parent selector in CSS
- JavaScript needed for parent styling

**:has() solves the problem:**

<div style="display:flex;gap:1em">

```css
.form:has(.error) { border: 2px solid red; }
.card:has(img) { display: grid; }
```

```html
<parent-component :class="{'error': hasEmitted}">
  <child-a @error="hasEmitted=true" />
  <child-b @error="hasEmitted=true" />
</parent-component>
```

</div>

---

## :has() Practical Applications

**Highlighting based on content**
```css
.wrapper:has(.mood-img) {
  background-color: black;
  padding: 1rem;
}
```

**Quantity queries:**
```css
.grid:has(li:nth-child(3):not(:nth-child(4))) {
  flex-direction: row;
}
```

---

## :has() Browser Support

**Current support:**
- Chrome 105+ (September 2022)
- Firefox 121+ (December 2023)
- Safari 15.4+ (March 2022)
- 📊 **Can I Use: 87% global support**

---

### Example Parent Selector `has:`

<a href="./xmp/04_parentselector/index.html" target=_blank>some fiddling with the parent selector</a>
