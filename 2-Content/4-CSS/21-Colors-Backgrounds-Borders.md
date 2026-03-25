# Day 21 — CSS Colors, Backgrounds & Borders

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 4 — CSS
🧪 **Lab Experiment:** 11

---

## Learning Objectives

By the end of this session, students will be able to:
- Use all CSS color formats (named, hex, rgb, rgba, hsl)
- Apply background colors, images, and gradients
- Style borders with different styles, widths, and radius
- Create CSS-only visual effects using backgrounds and borders

---

## 1. CSS Color Formats

| Format | Syntax | Example |
|--------|--------|---------|
| Named | `color: red;` | 147 named colors |
| Hex | `color: #FF0000;` | 6-digit hex |
| Hex shorthand | `color: #F00;` | 3-digit hex |
| RGB | `color: rgb(255, 0, 0);` | Red, Green, Blue (0–255) |
| RGBA | `color: rgba(255, 0, 0, 0.5);` | RGB + Alpha (opacity 0–1) |
| HSL | `color: hsl(0, 100%, 50%);` | Hue (0–360), Saturation, Lightness |

> **Analogy (HSL):** Think of a **color wheel** in art class. **Hue** is the position on the wheel (0 = red, 120 = green, 240 = blue). **Saturation** is how vivid the color is (0% = gray, 100% = pure). **Lightness** is brightness (0% = black, 50% = normal, 100% = white).

### Color Comparison

```css
.red-named { color: red; }
.red-hex   { color: #FF0000; }
.red-rgb   { color: rgb(255, 0, 0); }
.red-hsl   { color: hsl(0, 100%, 50%); }
/* All four look identical */

.semi-transparent { color: rgba(255, 0, 0, 0.5); }
```

---

## 2. Background Properties

### Background Color

```css
body { background-color: #f4f4f4; }
.card { background-color: rgba(21, 101, 192, 0.1); }
```

### Background Image

```css
.hero {
    background-image: url('campus.jpg');
    background-size: cover;          /* Fill entire element */
    background-position: center;     /* Center the image */
    background-repeat: no-repeat;    /* Don't tile */
    background-attachment: fixed;    /* Parallax effect */
    height: 400px;
}
```

| Property | Values |
|----------|--------|
| `background-size` | `cover`, `contain`, `100px 200px` |
| `background-position` | `center`, `top left`, `50% 50%` |
| `background-repeat` | `no-repeat`, `repeat`, `repeat-x`, `repeat-y` |
| `background-attachment` | `scroll` (default), `fixed` (parallax) |

### Background Shorthand

```css
.hero {
    background: url('campus.jpg') center/cover no-repeat fixed;
}
```

---

## 3. CSS Gradients

### Linear Gradient

```css
.gradient-1 {
    background: linear-gradient(to right, #667eea, #764ba2);
}
.gradient-2 {
    background: linear-gradient(135deg, #11998e, #38ef7d);
}
.gradient-3 {
    background: linear-gradient(to bottom, #FF9933, #FFFFFF, #138808); /* Indian flag */
}
```

### Radial Gradient

```css
.radial {
    background: radial-gradient(circle, #667eea, #764ba2);
}
```

---

## 4. Border Properties

### Border Syntax

```css
.box {
    border: 2px solid #333;        /* Shorthand: width style color */
}

/* Individual sides */
.box {
    border-top: 3px solid #1565C0;
    border-right: 1px dashed #ccc;
    border-bottom: 3px solid #1565C0;
    border-left: 1px dashed #ccc;
}
```

### Border Styles

| Style | Appearance |
|-------|-----------|
| `solid` | ─────── |
| `dashed` | - - - - |
| `dotted` | · · · · |
| `double` | ══════ |
| `groove` | 3D groove |
| `ridge` | 3D ridge |
| `inset` | 3D inset |
| `outset` | 3D outset |
| `none` | No border |

### Border Radius (Rounded Corners)

```css
.rounded    { border-radius: 10px; }          /* All corners */
.pill       { border-radius: 50px; }          /* Pill shape */
.circle     { border-radius: 50%; }           /* Perfect circle */
.custom     { border-radius: 10px 30px 10px 30px; } /* TL TR BR BL */
```

---

## 5. Box Shadow

```css
.card {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    /* x-offset  y-offset  blur  color */
}

.card-hover {
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

/* Inner shadow */
.inset {
    box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.2);
}
```

---

## Practical Session

### 🧪 Lab Experiment 11: Colors, Backgrounds & Borders

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Colors, Backgrounds & Borders</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        body {
            font-family: 'Segoe UI', sans-serif;
            background: #f0f0f0;
        }

        /* Hero section with gradient */
        .hero {
            background: linear-gradient(135deg, #1565C0 0%, #0D47A1 50%, #002171 100%);
            color: white;
            text-align: center;
            padding: 60px 20px;
        }
        .hero h1 {
            font-size: 2.5em;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.3);
        }
        .hero p {
            margin-top: 10px;
            font-size: 1.2em;
            opacity: 0.9;
        }

        /* Card container */
        .cards {
            max-width: 900px;
            margin: 30px auto;
            padding: 0 20px;
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
        }

        /* Card styles */
        .card {
            width: 260px;
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        .card-header {
            padding: 20px;
            color: white;
            text-align: center;
        }
        .card-body {
            padding: 20px;
        }
        .card-body p { color: #555; font-size: 14px; }

        /* Different colored cards */
        .card:nth-child(1) .card-header { background: linear-gradient(135deg, #667eea, #764ba2); }
        .card:nth-child(2) .card-header { background: linear-gradient(135deg, #11998e, #38ef7d); }
        .card:nth-child(3) .card-header { background: linear-gradient(135deg, #ee0979, #ff6a00); }

        /* Border showcase */
        .border-demo {
            max-width: 900px;
            margin: 30px auto;
            padding: 20px;
        }
        .border-box {
            display: inline-block;
            width: 120px;
            height: 80px;
            margin: 10px;
            padding: 10px;
            text-align: center;
            line-height: 60px;
            font-size: 12px;
            background: white;
        }
        .b-solid  { border: 3px solid #1565C0; }
        .b-dashed { border: 3px dashed #E91E63; }
        .b-dotted { border: 3px dotted #4CAF50; }
        .b-double { border: 4px double #FF9800; }
        .b-groove { border: 4px groove #9C27B0; }
        .b-ridge  { border: 4px ridge #009688; }

        /* Rounded corners showcase */
        .radius-demo {
            max-width: 900px;
            margin: 30px auto;
            padding: 20px;
            text-align: center;
        }
        .shape {
            display: inline-block;
            width: 100px;
            height: 100px;
            margin: 10px;
            line-height: 100px;
            text-align: center;
            color: white;
            font-size: 12px;
        }
        .square   { background: #1565C0; border-radius: 0; }
        .rounded  { background: #E91E63; border-radius: 15px; }
        .more-rounded { background: #4CAF50; border-radius: 30px; }
        .circle   { background: #FF9800; border-radius: 50%; }

        /* Footer */
        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 15px;
            margin-top: 30px;
        }
    </style>
</head>
<body>

    <div class="hero">
        <h1>CSS Visual Styling</h1>
        <p>Colors, Backgrounds, Gradients, Borders & Shadows</p>
    </div>

    <div class="cards">
        <div class="card">
            <div class="card-header"><h3>HTML</h3></div>
            <div class="card-body"><p>Structure and content of web pages using semantic markup.</p></div>
        </div>
        <div class="card">
            <div class="card-header"><h3>CSS</h3></div>
            <div class="card-body"><p>Styling and layout — colors, fonts, spacing, and animations.</p></div>
        </div>
        <div class="card">
            <div class="card-header"><h3>JavaScript</h3></div>
            <div class="card-body"><p>Interactivity and dynamic behavior on the client side.</p></div>
        </div>
    </div>

    <div class="border-demo">
        <h2 style="text-align:center; margin-bottom:15px;">Border Styles</h2>
        <div style="text-align:center;">
            <div class="border-box b-solid">Solid</div>
            <div class="border-box b-dashed">Dashed</div>
            <div class="border-box b-dotted">Dotted</div>
            <div class="border-box b-double">Double</div>
            <div class="border-box b-groove">Groove</div>
            <div class="border-box b-ridge">Ridge</div>
        </div>
    </div>

    <div class="radius-demo">
        <h2 style="margin-bottom:15px;">Border Radius</h2>
        <div class="shape square">0px</div>
        <div class="shape rounded">15px</div>
        <div class="shape more-rounded">30px</div>
        <div class="shape circle">50%</div>
    </div>

    <footer>
        <p>&copy; 2026 Mandsaur University — BCA Semester II</p>
    </footer>

</body>
</html>
```

---

## Summary

| Property | Purpose | Example |
|----------|---------|---------|
| `color` | Text color | `#1565C0`, `rgba(0,0,0,0.8)` |
| `background-color` | Element background | `#f4f4f4` |
| `background-image` | Background image/gradient | `url()`, `linear-gradient()` |
| `border` | Border shorthand | `2px solid #333` |
| `border-radius` | Rounded corners | `10px`, `50%` |
| `box-shadow` | Drop shadow | `0 4px 6px rgba(0,0,0,0.1)` |

---

*Day 21 of 55 | Unit 4 — CSS | Web Technology (25BCA060)*
