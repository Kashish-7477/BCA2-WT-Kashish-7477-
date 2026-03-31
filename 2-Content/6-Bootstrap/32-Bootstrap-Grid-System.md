# Day 32 — Bootstrap Grid System

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 6 — Bootstrap
🧪 **Lab Experiment:** 15

---

## Learning Objectives

By the end of this session, students will be able to:
- Use Bootstrap's 12-column grid system
- Create responsive layouts that adapt to different screen sizes
- Use row, col, and responsive breakpoint classes
- Build multi-column page layouts

---

## 1. The 12-Column Grid

> **Analogy:** Bootstrap's grid is like a **spreadsheet with 12 columns**. You can make one element span all 12 (full width), two elements span 6 each (50/50), or mix and match — 4 + 8, 3 + 3 + 3 + 3, etc. The columns always add up to 12.

### Mobile-First Strategy

> **Key Concept:** Bootstrap uses a **mobile-first** approach. This means:
> - **Default styles** are for the **smallest screens** (phones)
> - You then **add rules for larger screens** using breakpoint classes (`col-sm-`, `col-md-`, `col-lg-`, etc.)
> - If you write `col-md-6`, it means: "be full width on phones, but become 6 columns (50%) on medium screens and above"
>
> Think of it like building a house — you start with the **foundation** (mobile layout) and add **extra rooms** (desktop layout) on top.

```
|  1 |  2 |  3 |  4 |  5 |  6 |  7 |  8 |  9 | 10 | 11 | 12 |
|───────────────────────────────────────────────────────────────|
| col-12 (full width)                                           |
|───────────── col-6 ──────────|──────────── col-6 ────────────|
|─── col-4 ───|─── col-4 ─────|──────── col-4 ───────────────|
|─ col-3 ─|─ col-3 ─|─ col-3 ─|─ col-3 ──────────────────────|
```

### Basic Grid Structure

```html
<!-- A row containing two equal-width columns -->
<div class="container">          <!-- Centered wrapper with max-width -->
    <div class="row">            <!-- Flex row that holds columns -->
        <div class="col-6">Half width</div>   <!-- 6 out of 12 = 50% -->
        <div class="col-6">Half width</div>   <!-- 6 out of 12 = 50% -->
    </div>
</div>
```

> **Code Explanation:**
> - `container` — creates a centered wrapper; columns must always be inside a container
> - `row` — creates a horizontal group (flex container) that holds columns; it also manages gutters (gaps)
> - `col-6` — each column takes 6 out of 12 parts = **50% width**
> - The two `col-6` columns add up to 12 (6 + 6 = 12), so they fit side by side in one row

**Rules:**
1. Content goes inside `.col-*` classes
2. `.col-*` goes inside `.row`
3. `.row` goes inside `.container`
4. Column numbers should add up to 12

---

## 2. Responsive Breakpoints

| Breakpoint | Class Prefix | Screen Width |
|-----------|-------------|-------------|
| Extra small | `col-` | < 576px |
| Small | `col-sm-` | ≥ 576px |
| Medium | `col-md-` | ≥ 768px |
| Large | `col-lg-` | ≥ 992px |
| Extra large | `col-xl-` | ≥ 1200px |
| XXL | `col-xxl-` | ≥ 1400px |

### Breakpoint Decision Guide — How to Choose

Choosing the right breakpoint depends on **what content** you're displaying:

| Content Type | Recommended Breakpoint | Why |
|-------------|----------------------|-----|
| Blog post sidebar | `col-md-` (768px) | Tablets can show sidebar + content side by side |
| Product cards (e-commerce) | `col-sm-6 col-lg-3` | 2 cards on phone, 4 on desktop |
| Dashboard widgets | `col-lg-` (992px) | Need enough space for charts/data |
| Image gallery | `col-6 col-md-4 col-xl-3` | More columns as screen grows |
| Navigation links | `col-sm-` (576px) | Even small tablets can show horizontal nav |
| Form fields (name + email) | `col-md-6` | Side by side on tablets and above |

> **Rule of Thumb:** If your content has text (paragraphs, articles), use `col-md-` or `col-lg-`. If it's visual (images, icons), you can start earlier with `col-sm-`.

### Responsive Columns

```html
<div class="row">
    <!-- Full width on phone, half on tablet, third on desktop -->
    <div class="col-12 col-md-6 col-lg-4">Column 1</div>  <!-- 100% → 50% → 33% -->
    <div class="col-12 col-md-6 col-lg-4">Column 2</div>
    <div class="col-12 col-md-12 col-lg-4">Column 3</div>  <!-- Full width on tablet, 33% on desktop -->
</div>
```

> **Code Explanation:**
> - `col-12` — on extra-small screens (phones), each column takes full width (stacks vertically)
> - `col-md-6` — on medium screens (≥768px, tablets), columns become 50% width (2 per row)
> - `col-lg-4` — on large screens (≥992px, desktops), columns become 33.3% width (3 per row)
> - The **mobile-first principle** is visible here: the default (`col-12`) is the mobile layout, and larger breakpoints add progressively wider layouts
> - Column 3 uses `col-md-12` because after two `col-md-6` columns fill the row, it needs full width on tablets

### Auto-Width Columns

```html
<div class="row">
    <div class="col">Equal</div>      <!-- Auto equal width -->
    <div class="col">Equal</div>      <!-- Bootstrap divides space equally -->
    <div class="col">Equal</div>      <!-- 3 cols = 33.3% each -->
</div>

<div class="row">
    <div class="col">Auto</div>       <!-- Takes remaining space -->
    <div class="col-6">Fixed 6</div>  <!-- Fixed 50% width -->
    <div class="col">Auto</div>       <!-- Takes remaining space -->
</div>
```

> **Code Explanation:**
> - `col` (without a number) — auto-width; Bootstrap divides the available space equally among all `col` elements
> - In the first row: 3 `col` elements each get 33.3% width automatically
> - In the second row: `col-6` takes exactly 50%, and the two `col` elements split the remaining 50% equally (25% each)
> - Auto-width columns are useful when you don't know exactly how many columns you'll have

---

## 3. Grid Features

### Gutters (Gap Between Columns)

```html
<div class="row g-4">     <!-- gap: 1.5rem on all sides -->
<div class="row gx-3">    <!-- horizontal gap only: 1rem -->
<div class="row gy-4">    <!-- vertical gap only: 1.5rem -->
<div class="row g-0">     <!-- no gap at all -->
```

> **Code Explanation:**
> - `g-4` — adds a gap (gutter) of 1.5rem between columns on **both axes** (horizontal and vertical)
> - `gx-3` — adds a gap of 1rem only **horizontally** (left-right between columns)
> - `gy-4` — adds a gap of 1.5rem only **vertically** (top-bottom between rows of wrapped columns)
> - `g-0` — removes all gaps — columns touch each other edge-to-edge

#### Gutter Size Reference

| Class | Gap Size | In Pixels (approx) |
|:-----:|:--------:|:------------------:|
| `g-0` | `0` | 0px |
| `g-1` | `0.25rem` | 4px |
| `g-2` | `0.5rem` | 8px |
| `g-3` | `1rem` | 16px |
| `g-4` | `1.5rem` | 24px |
| `g-5` | `3rem` | 48px |

> **Tip:** `g-3` or `g-4` are the most commonly used gutter sizes. Use `g-0` for image grids where you want no gaps.

### Offset (Push Columns Right)

```html
<div class="row">
    <div class="col-md-6 offset-md-3">Centered 50% width</div>  <!-- Pushed 25% from left -->
</div>
```

> **Code Explanation:**
> - `offset-md-3` — pushes the column to the right by 3 columns (3/12 = 25%) on medium screens and above
> - Combined with `col-md-6` (50% width) and offset of 3: `3 + 6 + 3 = 12` — this perfectly centers the column
> - This is useful for centering forms, login boxes, or content that shouldn't span the full width

### Column Ordering

```html
<div class="row">
    <div class="col order-3">Appears third</div>   <!-- Visual order: 3rd -->
    <div class="col order-1">Appears first</div>   <!-- Visual order: 1st -->
    <div class="col order-2">Appears second</div>  <!-- Visual order: 2nd -->
</div>
```

> **Code Explanation:**
> - `order-1`, `order-2`, `order-3` — controls the **visual order** of columns without changing the HTML source order
> - The HTML has the columns in order 3-1-2, but on screen they display as 1-2-3
> - This is useful for **responsive layouts** — e.g., show sidebar first on mobile (for navigation) but second on desktop

### Nesting Rows

```html
<div class="row">
    <div class="col-md-8">
        <!-- Nested row inside a column — creates sub-columns within the parent column -->
        <div class="row">
            <div class="col-6">Nested Left</div>   <!-- 50% of the parent col-md-8 -->
            <div class="col-6">Nested Right</div>  <!-- 50% of the parent col-md-8 -->
        </div>
    </div>
    <div class="col-md-4">Sidebar</div>
</div>
```

> **Code Explanation:**
> - A `row` is placed **inside** a `col-md-8` column — this creates a nested 12-column grid within that column
> - The nested `col-6` columns each take 50% of the **parent column's width**, not the full page width
> - So nested `col-6` = 50% of 66.6% = about 33.3% of the full page
> - Nesting is useful for complex layouts like a content area with its own sub-sections

### Vertical and Horizontal Alignment

Bootstrap's grid is built on Flexbox, so you can align columns both vertically and horizontally:

```html
<!-- Vertical alignment: center all columns vertically in the row -->
<div class="row align-items-center" style="min-height: 200px;">
    <div class="col">I'm vertically centered!</div>
    <div class="col">Me too!</div>
</div>

<!-- Horizontal alignment: push columns to the center -->
<div class="row justify-content-center">
    <div class="col-4">Centered column (4/12)</div>  <!-- Doesn't need offset! -->
</div>

<!-- Space between columns -->
<div class="row justify-content-between">
    <div class="col-3">Left</div>   <!-- Pushed to far left -->
    <div class="col-3">Right</div>  <!-- Pushed to far right -->
</div>

<!-- Space around columns -->
<div class="row justify-content-evenly">
    <div class="col-3">Card 1</div>  <!-- Equal space around each -->
    <div class="col-3">Card 2</div>
    <div class="col-3">Card 3</div>
</div>
```

> **Code Explanation:**
> - `align-items-center` — vertically centers all columns inside the row (the row needs a minimum height for this to be visible)
> - `align-items-start` and `align-items-end` — align columns to the top or bottom of the row
> - `justify-content-center` — horizontally centers columns (columns don't have to add up to 12)
> - `justify-content-between` — first column sticks to the left, last to the right, with equal space between
> - `justify-content-evenly` — distributes equal space around every column (like equal spacing between product cards)

| Alignment Class | Direction | Effect |
|----------------|-----------|--------|
| `align-items-start` | Vertical | Columns at top |
| `align-items-center` | Vertical | Columns at middle |
| `align-items-end` | Vertical | Columns at bottom |
| `justify-content-start` | Horizontal | Columns at left (default) |
| `justify-content-center` | Horizontal | Columns at center |
| `justify-content-end` | Horizontal | Columns at right |
| `justify-content-between` | Horizontal | Space between columns |
| `justify-content-evenly` | Horizontal | Equal space around columns |

---

## Practical Session

### 🧪 Lab Experiment 15: Bootstrap Grid Layout

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootstrap Grid System</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .demo-col {
            background: #E3F2FD;
            border: 1px solid #90CAF9;
            padding: 15px;
            text-align: center;
            margin-bottom: 10px;
            border-radius: 5px;
        }
        section { margin-bottom: 40px; }
    </style>
</head>
<body>

    <div class="bg-primary text-white text-center py-4">
        <h1>Bootstrap Grid System</h1>
        <p class="lead mb-0">12-Column Responsive Layout</p>
    </div>

    <div class="container my-5">

        <!-- 1. Equal Columns -->
        <section>
            <h3 class="text-primary">1. Equal Columns</h3>
            <div class="row g-3">
                <div class="col-md-4"><div class="demo-col">col-md-4</div></div>
                <div class="col-md-4"><div class="demo-col">col-md-4</div></div>
                <div class="col-md-4"><div class="demo-col">col-md-4</div></div>
            </div>
        </section>

        <!-- 2. Unequal Columns -->
        <section>
            <h3 class="text-primary">2. Sidebar + Content Layout</h3>
            <div class="row g-3">
                <div class="col-md-3"><div class="demo-col">Sidebar (3)</div></div>
                <div class="col-md-9"><div class="demo-col">Main Content (9)</div></div>
            </div>
        </section>

        <!-- 3. Responsive Cards -->
        <section>
            <h3 class="text-primary">3. Responsive Card Grid</h3>
            <p class="text-muted">1 col on phone → 2 on tablet → 4 on desktop</p>
            <div class="row g-4">
                <div class="col-12 col-sm-6 col-lg-3">
                    <div class="card">
                        <div class="card-body bg-primary text-white rounded-top">
                            <h5 class="card-title">HTML5</h5>
                        </div>
                        <div class="card-body">
                            <p class="card-text">Structure and content markup language.</p>
                        </div>
                    </div>
                </div>
                <div class="col-12 col-sm-6 col-lg-3">
                    <div class="card">
                        <div class="card-body bg-success text-white rounded-top">
                            <h5 class="card-title">CSS3</h5>
                        </div>
                        <div class="card-body">
                            <p class="card-text">Styling, layout, and animations.</p>
                        </div>
                    </div>
                </div>
                <div class="col-12 col-sm-6 col-lg-3">
                    <div class="card">
                        <div class="card-body bg-warning rounded-top">
                            <h5 class="card-title">JavaScript</h5>
                        </div>
                        <div class="card-body">
                            <p class="card-text">Dynamic behavior and interactivity.</p>
                        </div>
                    </div>
                </div>
                <div class="col-12 col-sm-6 col-lg-3">
                    <div class="card">
                        <div class="card-body bg-info text-white rounded-top">
                            <h5 class="card-title">Bootstrap</h5>
                        </div>
                        <div class="card-body">
                            <p class="card-text">Rapid responsive UI development.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 4. Holy Grail Layout -->
        <section>
            <h3 class="text-primary">4. Complete Page Layout</h3>
            
            <!-- Header -->
            <div class="row">
                <div class="col-12">
                    <div class="bg-dark text-white p-3 rounded text-center mb-3">
                        <h4 class="mb-0">Header (col-12)</h4>
                    </div>
                </div>
            </div>
            
            <!-- Nav -->
            <div class="row">
                <div class="col-12">
                    <div class="bg-secondary text-white p-2 rounded text-center mb-3">
                        Home | About | Courses | Contact
                    </div>
                </div>
            </div>
            
            <!-- Content Area -->
            <div class="row g-3">
                <div class="col-md-3">
                    <div class="bg-light p-3 rounded border h-100">
                        <h5>Sidebar</h5>
                        <ul class="list-unstyled">
                            <li><a href="#">Link 1</a></li>
                            <li><a href="#">Link 2</a></li>
                            <li><a href="#">Link 3</a></li>
                        </ul>
                    </div>
                </div>
                <div class="col-md-6">
                    <div class="bg-white p-3 rounded border h-100">
                        <h5>Main Content</h5>
                        <p>This is the main content area spanning 6 columns on medium screens and above.</p>
                        <p>On mobile devices, all three sections stack vertically.</p>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="bg-light p-3 rounded border h-100">
                        <h5>Right Panel</h5>
                        <p>Ads, related content, or quick links.</p>
                    </div>
                </div>
            </div>
            
            <!-- Footer -->
            <div class="row mt-3">
                <div class="col-12">
                    <div class="bg-dark text-white p-3 rounded text-center">
                        Footer (col-12)
                    </div>
                </div>
            </div>
        </section>

    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

> **Code Explanation:**
> - **Custom CSS (`.demo-col`)**: Light blue background with border — used to make grid columns visible for learning purposes
> - **Section 1 — Equal Columns**: Three `col-md-4` columns (4+4+4=12) create equal thirds on medium+ screens; they stack on phones
> - **Section 2 — Sidebar Layout**: `col-md-3` (25%) for sidebar + `col-md-9` (75%) for content — a classic website layout pattern used by blogs and dashboards
> - **Section 3 — Responsive Cards**: `col-12 col-sm-6 col-lg-3` — the mobile-first pattern in action:
>   - Phone: 1 card per row (col-12)
>   - Tablet: 2 cards per row (col-sm-6)
>   - Desktop: 4 cards per row (col-lg-3)
> - **Section 4 — Holy Grail Layout**: A classic web page structure with header (full width), navigation bar (full width), three-column content area (sidebar + main + right panel), and footer (full width)
> - **`h-100`**: Makes all three content columns equal height, regardless of their content length
> - **`g-3` in content row**: Adds 1rem gap between the three columns
> - **`list-unstyled`**: Removes bullet points from the `<ul>` list in the sidebar

---

| Concept | Class | Explanation |
|---------|-------|-------------|
| Container | `container` | Centered, max-width layout |
| Row | `row` | Flex container for columns |
| Columns | `col-md-6` | 6/12 = 50% width at md+ |
| Responsive | `col-12 col-md-6 col-lg-4` | Different sizes per breakpoint |
| Gutters | `g-4`, `gx-3`, `gy-4` | Gap between columns |
| Offset | `offset-md-3` | Push column right |
| Order | `order-1` | Change visual order |

---

*Day 32 of 55 | Unit 6 — Bootstrap | Web Technology (25BCA060)*
