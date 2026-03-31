# Day 33 — Bootstrap Components: Cards, Tables & Images

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 6 — Bootstrap
🧪 **Lab Experiment:** 16

---

## Learning Objectives

By the end of this session, students will be able to:
- Create Bootstrap cards with headers, images, and footers
- Style tables using Bootstrap's table classes
- Use Bootstrap's responsive image and figure classes
- Combine cards in a responsive grid layout

---

## 1. Bootstrap Cards

```html
<!-- Basic Card -->
<div class="card" style="width: 18rem;">
    <img src="https://via.placeholder.com/300x180?text=Course+Image" 
         class="card-img-top" alt="Course">
    <div class="card-body">
        <h5 class="card-title">Web Technology</h5>
        <p class="card-text">Learn HTML, CSS, JavaScript, and Bootstrap.</p>
        <a href="#" class="btn btn-primary">Learn More</a>
    </div>
</div>

<!-- Card with Header/Footer -->
<div class="card">
    <div class="card-header bg-primary text-white">Featured Course</div>
    <div class="card-body">
        <h5 class="card-title">Data Structures</h5>
        <p class="card-text">Arrays, Linked Lists, Trees, and Graphs.</p>
    </div>
    <div class="card-footer text-muted">Last updated: April 2026</div>
</div>

<!-- Card with List Group -->
<div class="card">
    <div class="card-header">Semesters</div>
    <ul class="list-group list-group-flush">
        <li class="list-group-item">Semester I</li>
        <li class="list-group-item active">Semester II (Current)</li>
        <li class="list-group-item">Semester III</li>
    </ul>
</div>
```

> **Code Explanation:**
> - **Basic Card**: `card` creates a bordered container; `style="width: 18rem"` limits the card width
> - `card-img-top` — places the image at the top of the card with rounded top corners
> - `card-body` — adds padding around the card content
> - `card-title` and `card-text` — semantic classes for card heading and paragraph
> - `btn btn-primary` — a blue action button inside the card
> - **Card with Header/Footer**: `card-header` creates a colored top bar; `card-footer` creates a bottom section (great for "last updated" info)
> - `bg-primary text-white` on the header gives it a blue background with white text
> - `text-muted` in the footer makes the text light gray (less prominent)
> - **Card with List Group**: `list-group-flush` removes outer borders so the list blends with the card
> - `active` on a list item highlights it (shown as "Semester II (Current)")

### Horizontal Card Layout

A horizontal card shows the image on the left and text on the right — useful for product listings or course catalogs:

```html
<!-- Horizontal card: image on left, content on right -->
<div class="card mb-3" style="max-width: 540px;">
    <div class="row g-0">                           <!-- g-0 removes gutters between columns -->
        <div class="col-md-4">                      <!-- Image takes 1/3 width on md+ -->
            <img src="https://via.placeholder.com/200x250?text=Mandsaur+University"
                 class="img-fluid rounded-start" alt="University campus">
        </div>
        <div class="col-md-8">                      <!-- Text takes 2/3 width on md+ -->
            <div class="card-body">
                <h5 class="card-title">BCA Program</h5>
                <p class="card-text">3-year undergraduate program in Computer Applications at Mandsaur University.</p>
                <p class="card-text"><small class="text-muted">Admissions open for 2026–27</small></p>
            </div>
        </div>
    </div>
</div>
```

> **Code Explanation:**
> - The card uses Bootstrap's grid (`row` + `col-md-4` + `col-md-8`) **inside** the card to create a horizontal layout
> - `g-0` on the row removes gaps so the image sits flush against the text area
> - `col-md-4` gives the image 33% width; `col-md-8` gives the text 67% width
> - `rounded-start` rounds only the left corners of the image (matching the card border)
> - On mobile (below `md`), the columns stack — image on top, text below — creating a normal vertical card

---

## 2. Bootstrap Tables

```html
<!-- Basic Styled Table -->
<table class="table">
    <thead><tr><th>#</th><th>Name</th><th>Marks</th></tr></thead>
    <tbody>
        <tr><td>1</td><td>Rahul</td><td>85</td></tr>
        <tr><td>2</td><td>Priya</td><td>92</td></tr>
    </tbody>
</table>

<!-- Striped + Hoverable + Bordered -->
<table class="table table-striped table-hover table-bordered">
    ...
</table>

<!-- Dark Table -->
<table class="table table-dark table-striped">
    ...
</table>

<!-- Responsive Table (horizontal scroll on small screens) -->
<div class="table-responsive">
    <table class="table">...</table>
</div>
```

> **Code Explanation:**
> - `table` — applies Bootstrap's basic table styling (spacing, borders, alignment)
> - `table-striped` — adds alternating gray/white row backgrounds (zebra stripes) for readability
> - `table-hover` — highlights a row when you hover your mouse over it
> - `table-bordered` — adds borders on all sides of every cell
> - `table-dark` — inverts the table to white text on a dark background
> - `table-responsive` — wraps the table in a **horizontally scrollable container**; on small screens, users can scroll left/right to see all columns instead of the table breaking

### Responsive Table Behavior in Detail

When you wrap a table with `<div class="table-responsive">`, here's what happens on different screens:

| Screen Size | Behavior |
|------------|----------|
| Desktop (wide) | Table displays normally — no scrollbar |
| Tablet (medium) | If table is wider than screen, horizontal scrollbar appears |
| Mobile (small) | Horizontal scrollbar appears — user swipes left/right to see all columns |

```
Desktop view:              Mobile view:
┌──────────────────┐      ┌──────────┐
│ # │ Name │ Marks │      │ # │ Name │ ← scroll →
│ 1 │ Priya│  92   │      │ 1 │ Priya│ ...
│ 2 │ Rahul│  85   │      │ 2 │ Rahul│ ...
└──────────────────┘      └──────────┘
```

You can also use **breakpoint-specific** responsive tables:

```html
<!-- Scrollable only on screens smaller than lg (992px) -->
<div class="table-responsive-lg">
    <table class="table">...</table>
</div>
```

> **Code Explanation:**
> - `table-responsive-lg` — the table scrolls horizontally **only on screens smaller than 992px**; on larger screens, it displays normally
> - Other options: `table-responsive-sm`, `table-responsive-md`, `table-responsive-xl`

### Table Classes

| Class | Effect |
|-------|--------|
| `table` | Basic styling |
| `table-striped` | Zebra striping |
| `table-hover` | Highlight on hover |
| `table-bordered` | Borders on all sides |
| `table-borderless` | No borders |
| `table-dark` | Dark background |
| `table-sm` | Compact (less padding) |
| `table-responsive` | Horizontal scroll |

### Row Colors

```html
<tr class="table-success">Green row</tr>
<tr class="table-danger">Red row</tr>
<tr class="table-warning">Yellow row</tr>
<tr class="table-info">Light blue row</tr>
<tr class="table-primary">Blue row</tr>
```

> **Code Explanation:**
> - `table-success` — gives the row a light green background (used for positive data, like pass marks)
> - `table-danger` — light red background (used for negative data, like fail marks)
> - `table-warning` — light yellow background (used for caution, like low attendance)
> - `table-info` — light blue background (used for informational highlighting)
> - `table-primary` — Bootstrap's primary blue background (used for selected/active rows)

---

## 3. Bootstrap Images

```html
<!-- Responsive image (max-width: 100%) -->
<img src="photo.jpg" class="img-fluid" alt="Responsive image">

<!-- Rounded corners -->
<img src="photo.jpg" class="img-fluid rounded" alt="Rounded">

<!-- Circle (works best with square images) -->
<img src="photo.jpg" class="rounded-circle" alt="Circle" width="150">

<!-- Thumbnail (border + padding) -->
<img src="photo.jpg" class="img-thumbnail" alt="Thumbnail" width="200">

<!-- Figure with caption -->
<figure class="figure">
    <img src="photo.jpg" class="figure-img img-fluid rounded" alt="Photo">
    <figcaption class="figure-caption text-center">BCA Department Building</figcaption>
</figure>
```

> **Code Explanation:**
> - `img-fluid` — makes the image responsive: sets `max-width: 100%` and `height: auto` so the image never overflows its container
> - `rounded` — adds slightly rounded corners (default `border-radius: 0.375rem`)
> - `rounded-circle` — makes the image fully circular (best used with **square** images; rectangular images will appear oval)
> - `img-thumbnail` — adds a thin border and small padding around the image, like a photo frame
> - `figure` + `figure-img` + `figure-caption` — Bootstrap styling for the HTML5 `<figure>` element with proper spacing and aligned captions

### Image Lazy Loading

For pages with many images (like a photo gallery or product catalog), add `loading="lazy"` to defer loading images until the user scrolls to them. This makes the **initial page load faster**:

```html
<!-- Image loads only when user scrolls near it — saves bandwidth -->
<img src="campus-photo.jpg" class="img-fluid" alt="Mandsaur University campus" loading="lazy">

<!-- Thumbnail gallery with lazy loading -->
<div class="row g-3">
    <div class="col-6 col-md-3">
        <img src="lab-photo-1.jpg" class="img-thumbnail w-100" alt="Computer Lab" loading="lazy">
    </div>
    <div class="col-6 col-md-3">
        <img src="lab-photo-2.jpg" class="img-thumbnail w-100" alt="Library" loading="lazy">
    </div>
</div>
```

> **Code Explanation:**
> - `loading="lazy"` — a native HTML attribute (not Bootstrap) that tells the browser: "Don't load this image until it's about to appear on screen"
> - This reduces initial page load time, especially on mobile networks
> - `w-100` — Bootstrap utility that sets `width: 100%` so the thumbnail fills its column
> - Use `loading="lazy"` on all images **except** the first visible image (hero/banner), which should load immediately

---

## Practical Session

### 🧪 Lab Experiment 16: Cards, Tables & Components

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootstrap Components</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-light">

    <!-- Header -->
    <div class="bg-primary text-white text-center py-4 mb-4">
        <h1 class="mb-0">Bootstrap Components</h1>
        <p class="lead mb-0">Cards, Tables & Images</p>
    </div>

    <div class="container">

        <!-- Card Grid -->
        <h2 class="text-primary mb-3">Course Cards</h2>
        <div class="row g-4 mb-5">
            <div class="col-md-6 col-lg-4">
                <div class="card h-100 shadow-sm">
                    <div class="bg-primary text-white text-center py-4">
                        <span style="font-size: 3em;">🌐</span>
                    </div>
                    <div class="card-body">
                        <h5 class="card-title">Web Technology</h5>
                        <p class="card-text">Build modern websites using HTML5, CSS3, JavaScript, and Bootstrap.</p>
                    </div>
                    <div class="card-footer d-flex justify-content-between align-items-center">
                        <small class="text-muted">Semester II</small>
                        <a href="#" class="btn btn-sm btn-primary">View</a>
                    </div>
                </div>
            </div>
            <div class="col-md-6 col-lg-4">
                <div class="card h-100 shadow-sm">
                    <div class="bg-success text-white text-center py-4">
                        <span style="font-size: 3em;">📊</span>
                    </div>
                    <div class="card-body">
                        <h5 class="card-title">Data Structures</h5>
                        <p class="card-text">Master arrays, linked lists, trees, graphs, and algorithms.</p>
                    </div>
                    <div class="card-footer d-flex justify-content-between align-items-center">
                        <small class="text-muted">Semester II</small>
                        <a href="#" class="btn btn-sm btn-success">View</a>
                    </div>
                </div>
            </div>
            <div class="col-md-6 col-lg-4">
                <div class="card h-100 shadow-sm">
                    <div class="bg-warning text-center py-4">
                        <span style="font-size: 3em;">🧮</span>
                    </div>
                    <div class="card-body">
                        <h5 class="card-title">Mathematics</h5>
                        <p class="card-text">Discrete math, probability theory, and linear algebra.</p>
                    </div>
                    <div class="card-footer d-flex justify-content-between align-items-center">
                        <small class="text-muted">Semester II</small>
                        <a href="#" class="btn btn-sm btn-warning">View</a>
                    </div>
                </div>
            </div>
        </div>

        <!-- Student Table -->
        <h2 class="text-primary mb-3">Student Records</h2>
        <div class="table-responsive mb-5">
            <table class="table table-striped table-hover table-bordered align-middle">
                <thead class="table-dark">
                    <tr>
                        <th>#</th>
                        <th>Name</th>
                        <th>Roll No</th>
                        <th>Web Tech</th>
                        <th>Data Structures</th>
                        <th>Mathematics</th>
                        <th>Total</th>
                        <th>Grade</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>1</td><td>Rahul Kumar</td><td>25BCA001</td>
                        <td>85</td><td>78</td><td>92</td>
                        <td class="fw-bold">255</td>
                        <td><span class="badge bg-success">A</span></td>
                    </tr>
                    <tr>
                        <td>2</td><td>Priya Sharma</td><td>25BCA002</td>
                        <td>92</td><td>88</td><td>95</td>
                        <td class="fw-bold">275</td>
                        <td><span class="badge bg-primary">A+</span></td>
                    </tr>
                    <tr>
                        <td>3</td><td>Amit Patel</td><td>25BCA003</td>
                        <td>65</td><td>72</td><td>58</td>
                        <td class="fw-bold">195</td>
                        <td><span class="badge bg-warning text-dark">B</span></td>
                    </tr>
                    <tr class="table-danger">
                        <td>4</td><td>Neha Singh</td><td>25BCA004</td>
                        <td>35</td><td>42</td><td>38</td>
                        <td class="fw-bold">115</td>
                        <td><span class="badge bg-danger">F</span></td>
                    </tr>
                    <tr>
                        <td>5</td><td>Vikram Joshi</td><td>25BCA005</td>
                        <td>78</td><td>82</td><td>75</td>
                        <td class="fw-bold">235</td>
                        <td><span class="badge bg-success">A</span></td>
                    </tr>
                </tbody>
            </table>
        </div>

        <!-- List Group -->
        <h2 class="text-primary mb-3">Quick Links</h2>
        <div class="row mb-5">
            <div class="col-md-6">
                <div class="list-group">
                    <a href="#" class="list-group-item list-group-item-action active">Current Semester</a>
                    <a href="#" class="list-group-item list-group-item-action">Syllabus Download</a>
                    <a href="#" class="list-group-item list-group-item-action">Time Table</a>
                    <a href="#" class="list-group-item list-group-item-action">Exam Schedule</a>
                    <a href="#" class="list-group-item list-group-item-action disabled">Results (Coming Soon)</a>
                </div>
            </div>
        </div>

    </div>

    <!-- Footer -->
    <div class="bg-dark text-white text-center py-3 mt-4">
        <p class="mb-0">&copy; 2026 Mandsaur University</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

> **Code Explanation:**
> - **Card Grid**: `col-md-6 col-lg-4` gives 2 cards per row on tablets, 3 on desktops; `h-100` makes all cards equal height
> - **`shadow-sm`**: Adds a subtle drop shadow for a "floating card" effect
> - **Emoji icons** (`🌐`, `📊`, `🧮`): Used instead of actual images — simple and works without image files
> - **`card-footer d-flex justify-content-between align-items-center`**: Footer uses flexbox to push "Semester II" text to the left and the button to the right
> - **Student Table**: `table-striped table-hover table-bordered` combines three table styles — striped rows, hover highlight, and cell borders
> - **`thead class="table-dark"`**: Dark header row for visual contrast with the light table body
> - **`align-middle`**: Vertically centers content in all table cells
> - **`badge bg-success`** and others: Color-coded grade badges inside table cells
> - **`table-danger` on a `<tr>`**: Highlights Neha's row in red (she has failing marks)
> - **`fw-bold`** on total column: Makes total marks bold
> - **List Group**: `list-group-item-action` makes items look clickable (hover effect); `active` highlights the current item; `disabled` grays out unavailable items
> - **`table-responsive`** wrapper: Ensures the wide student table scrolls horizontally on mobile instead of breaking the layout

---

| Component | Key Classes |
|-----------|------------|
| Card | `card`, `card-body`, `card-title`, `card-img-top` |
| Table | `table`, `table-striped`, `table-hover`, `table-bordered` |
| Images | `img-fluid`, `rounded-circle`, `img-thumbnail` |
| List Group | `list-group`, `list-group-item` |
| Badges | `badge bg-primary` |

---

*Day 33 of 55 | Unit 6 — Bootstrap | Web Technology (25BCA060)*
