# CSS (Beginner → Intermediate → Advanced)

## 🟢 BEGINNER LEVEL

### 🔴 CSS kya hai
**What is it?** CSS (Cascading Style Sheets) HTML elements ko style karta hai — colors, layout, spacing, fonts.
**Why used?** HTML sirf structure deta hai, CSS use dikhne layak (visually appealing) banata hai.

### 🔴 Inline / Internal / External CSS
```html
<!-- Inline -->
<p style="color: red;">Text</p>

<!-- Internal -->
<style> p { color: red; } </style>

<!-- External (best practice) -->
<link rel="stylesheet" href="style.css">
```
**Important:** External CSS best practice hai — reusable, maintainable.

### 🔴 Syntax
```css
selector {
  property: value;
}
```
```css
p {
  color: blue;
  font-size: 16px;
}
```

### 🔴 Selectors
```css
p { }              /* tag selector */
.classname { }      /* class selector */
#idname { }          /* id selector */
* { }                /* universal selector */
```

### 🔴 Attribute Selectors
```css
input[type="text"] { border: 1px solid gray; }
```

### 🟡 Combinators
```css
div p { }      /* descendant */
div > p { }    /* direct child */
div + p { }    /* adjacent sibling */
div ~ p { }    /* general sibling */
```

### 🔴 Specificity & Cascade
**What is it?** Jab multiple rules same element pe apply hote hain, browser decide karta hai kaunsa rule jeetega.
**Order (weakest → strongest):** tag < class < id < inline style < `!important`
**Common Mistake:** Har jagah `!important` use karna — debugging mushkil ho jaata hai.

### 🟡 Inheritance
Kuch properties (color, font-family) child elements ko automatically mil jaati hain parent se.

### 🔴 Box Model — MUST KNOW
**What is it?** Har HTML element ek box hota hai jisme 4 layers hoti hain: Content → Padding → Border → Margin.
```
Margin (outside space)
  Border
    Padding (inside space)
      Content
```
```css
div {
  width: 200px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```
### 🔴 box-sizing
```css
* { box-sizing: border-box; }
```
`border-box` set karne se padding+border width ke andar count hote hain (total width fixed rehta hai) — **ye almost har project me use hota hai**.

### 🔴 Units
| Unit | Meaning |
|---|---|
| `px` | fixed pixels |
| `%` | parent ke relative |
| `em` | parent font-size ke relative |
| `rem` | root font-size ke relative (best for consistency) |
| `vw/vh` | viewport width/height ka % |
| `vmin/vmax` | viewport ka chhota/bada dimension |

### 🔴 Colors & Background
```css
color: #ff0000;             /* HEX */
color: rgb(255, 0, 0);      /* RGB */
color: rgba(255, 0, 0, 0.5); /* RGBA with opacity */
color: hsl(0, 100%, 50%);   /* HSL */
background: linear-gradient(to right, red, blue);
background-image: url("bg.jpg");
```

### 🔴 Typography
```css
font-family: 'Arial', sans-serif;
font-size: 16px;
font-weight: bold;
line-height: 1.5;
letter-spacing: 1px;
text-align: center;
text-decoration: underline;
text-transform: uppercase;
```

**Practice (Beginner)**
1. Ek card style karo (border, padding, background color)
2. 3 tarike se same color set karo (HEX, RGB, HSL)
3. Text ko center align + bold + custom font-size do

---

## 🟡 INTERMEDIATE LEVEL

### 🔴 Layout — display
```css
display: block;        /* full width, new line */
display: inline;       /* content ke jitna width, same line */
display: inline-block;  /* inline + width/height set ho sakta hai */
display: none;          /* element hide ho jaata hai */
```

### 🔴 position
```css
position: static;    /* default */
position: relative;   /* apni original position se offset */
position: absolute;   /* nearest positioned ancestor ke relative */
position: fixed;      /* viewport ke relative, scroll pe fixed */
position: sticky;     /* scroll tak relative, phir fixed ho jaata hai */
```
**Common Mistake:** `absolute` use karte waqt parent pe `position: relative` set karna bhoolna.

### 🟡 z-index & overflow
```css
z-index: 10;           /* stacking order, positioned elements pe hi kaam karta hai */
overflow: hidden;       /* extra content chhupa deta hai */
overflow: scroll;
overflow: auto;
```

### 🔴 FLEXBOX — MUST KNOW
**What is it?** 1-dimensional layout system — elements ko row ya column me align karne ke liye.
```css
.container {
  display: flex;
  flex-direction: row;       /* row | column */
  justify-content: center;    /* main axis alignment */
  align-items: center;        /* cross axis alignment */
  align-content: stretch;     /* multi-line alignment */
  flex-wrap: wrap;
  gap: 10px;
}
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 200px;
  order: 2;
}
```
| Property | Kaam |
|---|---|
| `justify-content` | horizontal alignment (main axis) |
| `align-items` | vertical alignment (cross axis) |
| `flex-wrap` | items next line pe wrap karein ya nahi |
| `gap` | items ke beech space |
| `flex-grow` | extra space le lega |
| `flex-shrink` | space kam hone pe simat jaayega |

**Example: Navbar**
```css
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

### 🔴 GRID — MUST KNOW
**What is it?** 2-dimensional layout system — rows aur columns dono control karta hai.
```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: 100px auto;
  gap: 20px;
}
.item {
  grid-column: 1 / 3;
  grid-row: 1 / 2;
}
```
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```
| Function | Kaam |
|---|---|
| `repeat(n, size)` | pattern repeat karta hai |
| `minmax(min, max)` | column ka min/max size |
| `auto-fit` | jitne columns fit ho sakein, adjust karta hai |
| `auto-fill` | empty tracks bhi rakhta hai |

```css
.container {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar content"
    "footer footer";
}
.header { grid-area: header; }
```

**Flexbox vs Grid:** Flexbox 1D (ek direction) ke liye best hai (navbar, buttons row). Grid 2D (rows+columns) layouts ke liye best hai (poora page layout, gallery).

**Practice (Intermediate)**
1. Flexbox se navbar banao (logo left, links right)
2. Grid se 3-column card layout banao
3. Ek page layout banao: header, sidebar, content, footer (grid-template-areas se)

---

## 🔵 ADVANCED LEVEL

### 🔴 Responsive Design — MUST KNOW
**What is it?** Website alag-alag screen sizes (mobile, tablet, desktop) pe sahi dikhe.
**Mobile-first approach:** Pehle mobile ke liye CSS likho, phir bade screens ke liye media query se overwrite karo.

```css
/* Mobile first */
.container { display: block; }

@media (min-width: 768px) {
  .container { display: flex; }
}
```

### 🔴 Media Queries & Breakpoints
```css
@media (max-width: 600px) { /* mobile */ }
@media (min-width: 601px) and (max-width: 1024px) { /* tablet */ }
@media (min-width: 1025px) { /* desktop */ }
```
**Common Breakpoints:** 480px (mobile), 768px (tablet), 1024px (laptop), 1440px (desktop)

### 🟡 Fluid Layouts & Responsive Images
```css
img { max-width: 100%; height: auto; }
```

### 🔴 clamp(), min(), max(), calc()
```css
font-size: clamp(1rem, 2vw + 1rem, 2.5rem); /* min, preferred, max */
width: calc(100% - 40px);
width: min(500px, 100%);
```
**Why used:** Responsive values manually media queries likhe bina.

### 🔴 Pseudo-classes & Pseudo-elements
```css
a:hover { color: red; }
input:focus { border-color: blue; }
li:first-child { }
li:last-child { }
li:nth-child(2) { }
p::before { content: "★ "; }
p::first-line { }
```
**Difference:** Pseudo-class (`:hover`) state target karta hai. Pseudo-element (`::before`) ek "virtual" element create karta hai.

### 🔴 Transitions & Transform
```css
.box {
  transition: all 0.3s ease-in-out;
}
.box:hover {
  transform: scale(1.1) rotate(5deg) translateX(10px);
}
```

### 🟡 Animations & Keyframes
```css
@keyframes slideIn {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}
.box {
  animation: slideIn 0.5s ease-in-out;
}
```

### 🔴 CSS Variables (Custom Properties)
```css
:root {
  --primary-color: #3498db;
  --spacing: 16px;
}
.button {
  background: var(--primary-color);
  padding: var(--spacing);
}
```
**Why used:** Reusable values, theme switching easy ho jaata hai.

### 🟡 Shadows, Filters, Object-fit
```css
box-shadow: 0 4px 6px rgba(0,0,0,0.1);
text-shadow: 1px 1px 2px gray;
filter: blur(5px) brightness(0.8);
img { object-fit: cover; object-position: center; }
```

### 🔵 CSS Reset & Architecture
```css
* { margin: 0; padding: 0; box-sizing: border-box; }
```
**Naming convention (BEM):**
```css
.card { }
.card__title { }      /* element */
.card--featured { }   /* modifier */
```
**Why used:** Large projects me consistent, conflict-free naming milta hai.

### 🔵 Modern CSS Best Practices
- Mobile-first likho
- CSS Variables use karo
- BEM ya similar naming convention follow karo
- `rem` use karo `px` ke bajaye font-sizes ke liye
- Flexbox/Grid use karo, floats avoid karo

**Practice (Advanced)**
1. Ek responsive navbar banao jo mobile pe hamburger jaisa dikhe (media query se)
2. Hover animation with transition + transform banao
3. CSS variables use karke dark/light theme toggle banao

---

## 📋 CSS Cheat Sheet
```css
color, background-color, font-size, font-weight, text-align
padding, margin, border, width, height, box-sizing: border-box
display: flex/grid/block/none
position: relative/absolute/fixed/sticky
```

## 📋 Flexbox Cheat Sheet
```css
display: flex;
flex-direction: row | column;
justify-content: flex-start | center | space-between | space-around;
align-items: flex-start | center | flex-end | stretch;
flex-wrap: nowrap | wrap;
gap: 10px;
```

## 📋 Grid Cheat Sheet
```css
display: grid;
grid-template-columns: repeat(3, 1fr);
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
gap: 20px;
grid-column: span 2;
```

## 📋 Responsive Cheat Sheet
```css
@media (max-width: 768px) { }
img { max-width: 100%; height: auto; }
width: clamp(200px, 50%, 600px);
```

## Common Mistakes
- `box-sizing: border-box` set na karna
- `position: absolute` use karna bina parent pe `relative` set kiye
- Fixed `px` widths use karna responsive design me
- `!important` overuse karna
- Media queries ko max-width aur min-width mix karke confuse karna

## Interview Questions
1. Flexbox vs Grid kab use karte hain?
2. Box model explain karo
3. `em` vs `rem` me difference?
4. CSS specificity kaise calculate hoti hai?
5. Mobile-first design kya hai?

## Practice Tasks
**Beginner:** Card design, color palette practice, box model practice
**Intermediate:** Flexbox navbar, Grid gallery, responsive 2-column layout
**Advanced:** Full responsive landing page with animations + CSS variables + dark mode

## ✍️ Notebook Notes
1. Box Model order: Content → Padding → Border → Margin
2. `box-sizing: border-box` — hamesha use karo
3. Flexbox = 1D layout, Grid = 2D layout
4. `justify-content` = main axis, `align-items` = cross axis
5. Mobile-first: pehle mobile CSS, phir `min-width` media queries
6. `rem` use karo font-size ke liye (not px)
7. CSS Variables: `--name: value;` aur `var(--name)`
8. Common breakpoints: 480px, 768px, 1024px
