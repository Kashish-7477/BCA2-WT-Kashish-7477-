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
<div class="container">
    <div class="row">
        <div class="col-6">Half width</div>
        <div class="col-6">Half width</div>
    </div>
</div>
```

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

### Responsive Columns

```html
<div class="row">
    <!-- Full width on phone, half on tablet, third on desktop -->
    <div class="col-12 col-md-6 col-lg-4">Column 1</div>
    <div class="col-12 col-md-6 col-lg-4">Column 2</div>
    <div class="col-12 col-md-12 col-lg-4">Column 3</div>
</div>
```

### Auto-Width Columns

```html
<div class="row">
    <div class="col">Equal</div>      <!-- Auto equal width -->
    <div class="col">Equal</div>
    <div class="col">Equal</div>
</div>

<div class="row">
    <div class="col">Auto</div>
    <div class="col-6">Fixed 6</div>  <!-- Fixed, others auto -->
    <div class="col">Auto</div>
</div>
```

---

## 3. Grid Features

### Gutters (Gap Between Columns)

```html
<div class="row g-4">     <!-- gap: 1.5rem on all sides -->
<div class="row gx-3">    <!-- horizontal gap only -->
<div class="row gy-4">    <!-- vertical gap only -->
<div class="row g-0">     <!-- no gap -->
```

### Offset (Push Columns Right)

```html
<div class="row">
    <div class="col-md-6 offset-md-3">Centered 50% width</div>
</div>
```

### Column Ordering

```html
<div class="row">
    <div class="col order-3">Appears third</div>
    <div class="col order-1">Appears first</div>
    <div class="col order-2">Appears second</div>
</div>
```

### Nesting Rows

```html
<div class="row">
    <div class="col-md-8">
        <!-- Nested row inside a column -->
        <div class="row">
            <div class="col-6">Nested Left</div>
            <div class="col-6">Nested Right</div>
        </div>
    </div>
    <div class="col-md-4">Sidebar</div>
</div>
```

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

---

## Summary

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
