# Day 31 — Introduction to Bootstrap

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 6 — Bootstrap
🧪 **Lab Experiment:** 14

---

## Learning Objectives

By the end of this session, students will be able to:
- Explain what Bootstrap is and why it's used
- Set up Bootstrap via CDN
- Use Bootstrap's container system and utility classes
- Apply basic Bootstrap typography and color classes

---

## 1. What is Bootstrap?

> **Analogy:** Writing CSS from scratch is like **building furniture yourself** — complete control but takes time. Bootstrap is like buying from **IKEA** — pre-built components that you assemble quickly. You get a professional result faster, and you can still customize it.

Bootstrap is a **free, open-source CSS framework** by Twitter. It provides:
- **Pre-built components** (buttons, cards, navigation, modals)
- **Responsive grid system** (12-column layout)
- **Utility classes** (spacing, colors, alignment without custom CSS)
- **Mobile-first** design

### Bootstrap 5 (Latest)

| Feature | Details |
|---------|---------|
| Version | 5.3.x |
| jQuery | Not required (pure JS) |
| Grid | 12-column, flexbox-based |
| Breakpoints | xs, sm, md, lg, xl, xxl |

### Bootstrap 4 vs Bootstrap 5 — Key Differences

| Feature | Bootstrap 4 | Bootstrap 5 |
|---------|------------|------------|
| **jQuery** | Required for all JS components | Removed — uses vanilla JavaScript |
| **Grid breakpoints** | xs, sm, md, lg, xl | xs, sm, md, lg, xl, **xxl** (≥1400px) |
| **RTL support** | Not built-in | Built-in Right-to-Left support (for Urdu, Arabic, etc.) |
| **Form controls** | Custom form classes (`custom-select`, `custom-checkbox`) | Unified classes (`form-select`, `form-check`) |
| **Utilities API** | Limited utility classes | Expanded utility API — generate your own utilities |
| **Close button** | `<button class="close">` with `&times;` | `<button class="btn-close">` (SVG icon built-in) |
| **Offcanvas** | Not available | New offcanvas sidebar component |
| **Vertical spacing** | `gutter` classes limited | `g-*`, `gx-*`, `gy-*` gutter classes |
| **IE support** | Supports IE 10-11 | Dropped IE support completely |

> **Why this matters:** Since Bootstrap 5 doesn't need jQuery, your HTML files load faster and you have fewer dependencies. If you see old tutorials using `$('#myModal').modal('show')`, that's Bootstrap 4 jQuery syntax. In Bootstrap 5, you use `new bootstrap.Modal(element).show()` instead.

### Customizing Bootstrap Colors with Custom CSS

You can **override Bootstrap's default colors** by writing your own CSS rules **after** the Bootstrap CSS link. This works because of CSS specificity — later rules override earlier ones.

```html
<!-- Step 1: Bootstrap CSS (loaded first) -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- Step 2: Your custom CSS (loaded second — overrides Bootstrap) -->
<style>
    /* Override Bootstrap's primary color for buttons */
    .btn-primary {
        background-color: #FF5722;  /* Orange instead of default blue */
        border-color: #FF5722;
    }
    .btn-primary:hover {
        background-color: #E64A19;  /* Darker orange on hover */
        border-color: #E64A19;
    }

    /* Override Bootstrap's default body font */
    body {
        font-family: 'Segoe UI', Tahoma, sans-serif;
    }
</style>
```

> **Code Explanation:**
> - The Bootstrap CSS file is loaded **first** via CDN — this sets all default styles
> - Your custom `<style>` block comes **after** — CSS reads top-to-bottom, so later rules win
> - `.btn-primary` overrides the default blue (`#0d6efd`) with orange (`#FF5722`)
> - `:hover` state also needs overriding, otherwise hover will revert to Bootstrap's default blue
> - This technique lets you **customize Bootstrap's look** without modifying the framework itself

---

## 2. Setting Up Bootstrap

### Via CDN (Content Delivery Network) — Quickest

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Bootstrap Page</title>
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

    <h1>Hello Bootstrap!</h1>

    <!-- Bootstrap JS (at end of body) -->
    <!-- Bootstrap JS (at end of body for faster page load) -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

> **Code Explanation:**
> - `<!DOCTYPE html>` — tells the browser this is an HTML5 document
> - `<meta name="viewport" ...>` — essential for responsive design; makes the page scale correctly on mobile phones
> - `<link href="...bootstrap.min.css">` — loads Bootstrap's CSS from a CDN (no download needed)
> - The CSS link goes in `<head>` so styles load before the page renders
> - `<script src="...bootstrap.bundle.min.js">` — loads Bootstrap's JavaScript (needed for interactive components like dropdowns, modals)
> - The JS script goes at the **end of body** so the HTML content loads first (better performance)
> - `bundle.min.js` includes Popper.js (needed for tooltips and dropdowns) — you don't need to add Popper separately

---

## 3. Containers

```html
<!-- Fixed-width container (centered, max-width at each breakpoint) -->
<div class="container">Content here</div>

<!-- Full-width container -->
<div class="container-fluid">Spans entire width</div>

<!-- Responsive container (full-width until breakpoint) -->
<div class="container-md">Full width below md, fixed above</div>
```

> **Code Explanation:**
> - `container` — creates a centered box with a **fixed maximum width** that changes at each breakpoint (e.g., 540px on sm, 720px on md, 960px on lg)
> - `container-fluid` — always takes **100% of the screen width** with no maximum limit
> - `container-md` — behaves like `container-fluid` (full width) on screens **smaller than md (768px)**, then switches to fixed-width like `container`

### Container vs Container-Fluid — Practical Effect

> **Analogy:** Think of `container` as a **book page** — it has fixed margins on both sides, keeping text readable. `container-fluid` is like a **billboard** — content stretches edge to edge across the entire width.

| Feature | `.container` | `.container-fluid` |
|---------|-------------|-------------------|
| **Width** | Fixed max-width at each breakpoint | Always 100% of screen |
| **Margins** | Auto left/right margins (centered) | Only small padding (left/right) |
| **Best for** | Reading content, forms, text-heavy pages | Full-width banners, hero sections, dashboards |
| **Looks on 1920px screen** | Content centered with large empty sides | Content stretches fully across |

```
┌─────────────────────── Browser Window (1200px) ──────────────────────┐
│                                                                       │
│   ┌──────────── .container (960px, centered) ───────────┐            │
│   │              Your content lives here                 │            │
│   └──────────────────────────────────────────────────────┘            │
│                                                                       │
│ ┌──────────── .container-fluid (1200px, full) ────────────────────┐  │
│ │              Your content stretches edge to edge                 │  │
│ └─────────────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────────────┘
```

---

## 4. Bootstrap Typography

```html
<h1 class="display-1">Display Heading 1</h1>
<h2 class="display-4">Display Heading 4</h2>

<p class="lead">This is a lead paragraph — larger and lighter text.</p>

<p class="text-muted">Muted gray text</p>
<p class="text-primary">Primary blue text</p>
<p class="text-success">Success green text</p>
<p class="text-danger">Danger red text</p>
<p class="text-warning">Warning yellow text</p>

<p class="fw-bold">Bold text</p>
<p class="fst-italic">Italic text</p>
<p class="text-center">Centered text</p>
<p class="text-uppercase">uppercase text</p>
```

> **Code Explanation:**
> - `display-1` through `display-6` — extra-large, eye-catching heading sizes (bigger than regular `h1`–`h6`)
> - `lead` — makes a paragraph slightly larger and lighter — good for introductory text
> - `text-muted` — light gray color, used for less important text
> - `text-primary`, `text-success`, `text-danger`, `text-warning` — applies Bootstrap's theme colors to text
> - `fw-bold` — sets `font-weight: bold` (Bootstrap 5 uses `fw-` prefix for font weight)
> - `fst-italic` — sets `font-style: italic` (Bootstrap 5 uses `fst-` prefix for font style)
> - `text-center` — centers text horizontally
> - `text-uppercase` — transforms text to ALL CAPS using CSS (the actual HTML can be lowercase)

---

## 5. Bootstrap Colors & Backgrounds

### Text Colors

| Class | Color |
|-------|-------|
| `text-primary` | Blue |
| `text-secondary` | Gray |
| `text-success` | Green |
| `text-danger` | Red |
| `text-warning` | Yellow |
| `text-info` | Light blue |
| `text-light` | White (use on dark bg) |
| `text-dark` | Black |

### Backgrounds

```html
<div class="bg-primary text-white p-3">Primary Background</div>
<div class="bg-success text-white p-3">Success Background</div>
<div class="bg-danger text-white p-3">Danger Background</div>
<div class="bg-warning p-3">Warning Background</div>
<div class="bg-dark text-white p-3">Dark Background</div>
```

> **Code Explanation:**
> - `bg-primary`, `bg-success`, `bg-danger`, etc. — sets the background color using Bootstrap's theme palette
> - `text-white` — sets text color to white (needed on dark backgrounds for readability)
> - `p-3` — adds padding of `1rem` (16px) on all four sides
> - Notice `bg-warning` does **not** have `text-white` — yellow backgrounds are light enough for dark text to be readable

---

## 6. Utility Classes

### Spacing (Margin & Padding)

Format: `{property}{sides}-{size}`

| Part | Options |
|------|---------|
| Property | `m` (margin), `p` (padding) |
| Sides | `t` (top), `b` (bottom), `s` (start/left), `e` (end/right), `x` (horizontal), `y` (vertical), blank (all) |
| Size | `0`, `1` (0.25rem), `2` (0.5rem), `3` (1rem), `4` (1.5rem), `5` (3rem), `auto` |

### Understanding the Spacing Numbers

The numbers `0` through `5` are **not pixels** — they are based on a multiplier of Bootstrap's base spacing unit (which is `1rem = 16px` by default):

| Size Number | Value | In Pixels (approx) | Example Use |
|:-----------:|:-----:|:------------------:|-------------|
| `0` | `0` | 0px | Remove all margin/padding |
| `1` | `0.25rem` | 4px | Tiny gap between inline elements |
| `2` | `0.5rem` | 8px | Small gap between related items |
| `3` | `1rem` | 16px | Standard gap (most common) |
| `4` | `1.5rem` | 24px | Larger gap between sections |
| `5` | `3rem` | 48px | Big gap, like before a footer |
| `auto` | `auto` | — | Centers block elements horizontally |

> **Tip:** When in doubt, start with `3` (1rem/16px) — it's the most commonly used spacing value and looks balanced in most cases.

```html
<!-- Examples of spacing in a student profile card -->
<div class="card mt-4 p-3">                  <!-- margin-top: 1.5rem, padding: 1rem on all sides -->
    <h5 class="mb-2">Rahul Sharma</h5>       <!-- margin-bottom: 0.5rem below the name -->
    <p class="mb-0">BCA Sem II — Mandsaur</p> <!-- mb-0 removes bottom margin completely -->
    <hr class="my-3">                         <!-- margin top+bottom: 1rem -->
    <div class="px-2">                        <!-- padding left+right: 0.5rem -->
        <small class="text-muted">Roll No: 25BCA042</small>
    </div>
</div>
```

> **Code Explanation:**
> - `mt-4` — margin-top of 1.5rem (24px) — pushes the card down from elements above
> - `p-3` — padding of 1rem (16px) on all four sides — creates inner space
> - `mb-2` — margin-bottom of 0.5rem (8px) — small gap below the heading
> - `mb-0` — removes margin-bottom completely — keeps paragraph tight against next element
> - `my-3` — margin on Y-axis (top + bottom) of 1rem each
> - `px-2` — padding on X-axis (left + right) of 0.5rem each

```html
<div class="mt-3">margin-top: 1rem</div>
<div class="px-4">padding-left and right: 1.5rem</div>
<div class="mb-5">margin-bottom: 3rem</div>
<div class="p-0">no padding</div>
<div class="mx-auto" style="width: 200px;">Centered block</div>
```

> **Code Explanation:**
> - `mt-3` — adds `margin-top: 1rem` (16px gap above the element)
> - `px-4` — adds `padding-left: 1.5rem` and `padding-right: 1.5rem` (x = horizontal axis)
> - `mb-5` — adds `margin-bottom: 3rem` (48px gap below — a big space)
> - `p-0` — removes all padding (useful when Bootstrap components add default padding)
> - `mx-auto` — sets `margin-left: auto` and `margin-right: auto` — this **centers a block element** horizontally (only works when the element has a defined width)

### Display & Flexbox

```html
<div class="d-flex justify-content-between">
    <span>Left</span>
    <span>Right</span>
</div>

<div class="d-none d-md-block">Hidden on small, visible on md+</div>
```

> **Code Explanation:**
> - `d-flex` — makes the element a flex container (children are laid out in a row by default)
> - `justify-content-between` — pushes the first child to the far left and last child to the far right
> - `d-none` — hides the element (`display: none`)
> - `d-md-block` — on medium screens (≥768px) and above, overrides `d-none` and shows the element (`display: block`)
> - This pattern is commonly used to **hide elements on mobile** and show them on larger screens

### Borders & Rounded

```html
<div class="border border-primary rounded p-3">Bordered box</div>
<img class="rounded-circle" src="..." alt="...">
```

> **Code Explanation:**
> - `border` — adds a 1px solid border around the element
> - `border-primary` — changes the border color to Bootstrap's primary blue
> - `rounded` — adds `border-radius` for slightly rounded corners
> - `p-3` — adds padding inside the bordered box
> - `rounded-circle` — makes the element fully circular (works best with square images)

---

## Practical Session

### 🧪 Lab Experiment 14: Bootstrap Basics Page

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootstrap Basics</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

    <!-- Header -->
    <div class="bg-primary text-white text-center py-5">
        <div class="container">
            <h1 class="display-4 fw-bold">Welcome to Bootstrap</h1>
            <p class="lead">BCA Semester II — Web Technology Lab</p>
            <a href="#content" class="btn btn-light btn-lg mt-3">Get Started</a>
        </div>
    </div>

    <!-- Content -->
    <div class="container my-5" id="content">
        
        <!-- Typography Showcase -->
        <h2 class="text-primary mb-4">Typography</h2>
        <div class="row">
            <div class="col-md-6">
                <h1>Heading 1</h1>
                <h2>Heading 2</h2>
                <h3>Heading 3</h3>
                <h4>Heading 4</h4>
                <h5>Heading 5</h5>
                <h6>Heading 6</h6>
            </div>
            <div class="col-md-6">
                <p class="display-1">Display 1</p>
                <p class="display-4">Display 4</p>
                <p class="lead">Lead paragraph text</p>
                <p class="text-muted">Muted text</p>
                <p><mark>Highlighted text</mark></p>
                <p><small>Small text</small></p>
            </div>
        </div>
        <hr>

        <!-- Color Showcase -->
        <h2 class="text-primary mb-4">Colors</h2>
        <div class="row g-3 mb-4">
            <div class="col-md-4"><div class="bg-primary text-white p-3 rounded">Primary</div></div>
            <div class="col-md-4"><div class="bg-secondary text-white p-3 rounded">Secondary</div></div>
            <div class="col-md-4"><div class="bg-success text-white p-3 rounded">Success</div></div>
            <div class="col-md-4"><div class="bg-danger text-white p-3 rounded">Danger</div></div>
            <div class="col-md-4"><div class="bg-warning p-3 rounded">Warning</div></div>
            <div class="col-md-4"><div class="bg-info p-3 rounded">Info</div></div>
        </div>
        <hr>

        <!-- Buttons Showcase -->
        <h2 class="text-primary mb-4">Buttons</h2>
        <button class="btn btn-primary">Primary</button>
        <button class="btn btn-secondary">Secondary</button>
        <button class="btn btn-success">Success</button>
        <button class="btn btn-danger">Danger</button>
        <button class="btn btn-warning">Warning</button>
        <button class="btn btn-info">Info</button>
        <button class="btn btn-dark">Dark</button>
        <button class="btn btn-outline-primary">Outline</button>
        <br><br>
        <button class="btn btn-primary btn-sm">Small</button>
        <button class="btn btn-primary">Normal</button>
        <button class="btn btn-primary btn-lg">Large</button>
        <hr>

        <!-- Alerts -->
        <h2 class="text-primary mb-4">Alerts</h2>
        <div class="alert alert-success">✅ This is a success alert!</div>
        <div class="alert alert-danger">❌ This is a danger alert!</div>
        <div class="alert alert-warning">⚠️ This is a warning alert!</div>
        <div class="alert alert-info">ℹ️ This is an info alert!</div>

        <!-- Badges -->
        <h2 class="text-primary mb-4">Badges</h2>
        <span class="badge bg-primary">Primary</span>
        <span class="badge bg-success">Success</span>
        <span class="badge bg-danger">Danger</span>
        <span class="badge rounded-pill bg-info">Pill Badge</span>
    </div>

    <!-- Footer -->
    <div class="bg-dark text-white text-center py-3">
        <p class="mb-0">&copy; 2026 Mandsaur University — BCA Semester II</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

> **Code Explanation:**
> - **Header section**: `bg-primary text-white text-center py-5` creates a full-width blue banner with white text, centered, with vertical padding of 3rem
> - **`container` inside header**: Limits the text width even though the blue background stretches full width
> - **`display-4 fw-bold`**: Extra-large, bold heading for visual impact
> - **`btn btn-light btn-lg`**: A large white button — `btn-light` gives it a white/light-gray color that contrasts with the blue background
> - **Typography section (`row` + `col-md-6`)**: Two equal columns on medium+ screens; stacks vertically on mobile
> - **Color showcase (`row g-3`)**: `g-3` adds 1rem gap between the colored boxes; `col-md-4` creates 3 columns on tablets+
> - **`rounded`**: Adds rounded corners to each colored box
> - **Button showcase**: Shows all Bootstrap button variants — solid colors (`btn-primary`, `btn-danger`) and outline (`btn-outline-primary`)
> - **`btn-sm`, `btn-lg`**: Small and large button sizes
> - **Alerts**: `alert alert-success` creates a green success message box; each alert type has its own color
> - **Badges**: `badge bg-primary` creates small colored labels; `rounded-pill` makes the badge pill-shaped (fully rounded ends)
> - **Footer**: `bg-dark text-white py-3` creates a dark footer; `mb-0` on the paragraph removes default bottom margin

---

| Concept | Class/Syntax |
|---------|-------------|
| CDN Link | `<link href="...bootstrap.min.css">` |
| Container | `container`, `container-fluid` |
| Typography | `display-1`, `lead`, `fw-bold` |
| Colors | `text-primary`, `bg-success` |
| Spacing | `mt-3`, `px-4`, `mb-5` |
| Buttons | `btn btn-primary`, `btn-lg` |
| Alerts | `alert alert-success` |

---

*Day 31 of 55 | Unit 6 — Bootstrap | Web Technology (25BCA060)*
