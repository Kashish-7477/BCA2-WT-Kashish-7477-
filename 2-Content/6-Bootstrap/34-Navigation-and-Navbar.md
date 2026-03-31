# Day 34 — Bootstrap Navigation & Navbar

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 6 — Bootstrap
🧪 **Lab Experiment:** 25

---

## Learning Objectives

By the end of this session, students will be able to:
- Create responsive Bootstrap navbar with brand, links, and dropdown
- Add a hamburger menu for mobile screens
- Build breadcrumb and pagination navigation
- Use Bootstrap nav tabs and pills

---

## 1. Bootstrap Navbar

### Basic Responsive Navbar

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
        <!-- Brand -->
        <a class="navbar-brand" href="#">MU — BCA</a>
        
        <!-- Hamburger button (mobile) -->
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" 
                data-bs-target="#mainNav">
            <span class="navbar-toggler-icon"></span>
        </button>
        
        <!-- Collapsible links -->
        <div class="collapse navbar-collapse" id="mainNav">
            <ul class="navbar-nav me-auto">
                <li class="nav-item">
                    <a class="nav-link active" href="#">Home</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">About</a>
                </li>
                
                <!-- Dropdown -->
                <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" data-bs-toggle="dropdown">
                        Courses
                    </a>
                    <ul class="dropdown-menu">
                        <li><a class="dropdown-item" href="#">Web Technology</a></li>
                        <li><a class="dropdown-item" href="#">Data Structures</a></li>
                        <li><hr class="dropdown-divider"></li>
                        <li><a class="dropdown-item" href="#">All Courses</a></li>
                    </ul>
                </li>
                
                <li class="nav-item">
                    <a class="nav-link" href="#">Contact</a>
                </li>
            </ul>
            
            <!-- Search form -->
            <form class="d-flex" role="search">
                <input class="form-control me-2" type="search" placeholder="Search">
                <button class="btn btn-outline-light" type="submit">Search</button>
            </form>
        </div>
    </div>
</nav>
```

> **Code Explanation:**
> - `navbar` — creates the navigation bar component
> - `navbar-expand-lg` — the navbar is **collapsed** (hamburger menu) on screens below `lg` (992px) and **expanded** (horizontal links) on `lg` and above
> - `navbar-dark bg-dark` — white text on dark background (use `navbar-light bg-light` for the reverse)
> - `navbar-brand` — the site name/logo on the far left; always visible even when collapsed
> - `navbar-toggler` — the hamburger button (☰) that appears on mobile; `data-bs-target="#mainNav"` links it to the collapsible section
> - `navbar-toggler-icon` — Bootstrap's built-in hamburger icon (three horizontal lines)
> - `collapse navbar-collapse` — the section that collapses on mobile and expands on desktop
> - `navbar-nav me-auto` — navigation links aligned to the left; `me-auto` pushes everything after it to the right
> - `nav-link active` — `active` class highlights the current page link (styled differently from other links)
> - `dropdown-toggle` + `data-bs-toggle="dropdown"` — creates a dropdown menu on click
> - `dropdown-menu` + `dropdown-item` — the dropdown list and its items
> - `dropdown-divider` — a thin horizontal line separating dropdown items
> - `d-flex` on the form — makes the search input and button sit side by side
> - `form-control me-2` — styled input with margin-end (gap between input and button)
> - `btn btn-outline-light` — a transparent button with white border (matches the dark navbar)

### Navbar Color Schemes

| Classes | Appearance |
|---------|-----------|
| `navbar-dark bg-dark` | White text on dark background |
| `navbar-dark bg-primary` | White text on blue background |
| `navbar-light bg-light` | Dark text on light background |
| `bg-transparent` | Transparent background |

### Fixed vs Sticky Navbar Positioning

| Feature | `fixed-top` | `sticky-top` |
|---------|------------|-------------|
| **Behavior** | Always stays at the top of the viewport | Sticks to top only when you scroll past it |
| **Overlap** | Overlaps page content (need `margin-top` on body) | Does NOT overlap — takes its normal space first |
| **Best for** | Navbars that should always be visible (e-commerce, dashboards) | Navbars that appear after a hero section |
| **Usage** | `<nav class="navbar fixed-top">` | `<nav class="navbar sticky-top">` |
| **Body fix** | Need `body { margin-top: 56px; }` | No fix needed |

```html
<!-- Fixed navbar: always visible, overlaps content -->
<nav class="navbar navbar-dark bg-dark fixed-top">
    <!-- Need to add margin-top to body to prevent content from hiding behind navbar -->
    ...
</nav>
<div style="margin-top: 56px;">Page content starts here</div>

<!-- Sticky navbar: stays in normal flow, sticks on scroll -->
<nav class="navbar navbar-dark bg-dark sticky-top">
    <!-- No margin fix needed — navbar takes its normal space -->
    ...
</nav>
```

> **Code Explanation:**
> - `fixed-top` — removes the navbar from normal document flow and **pins it** to the top of the screen at all times. Content will slide behind it, so you need to add `margin-top` (usually 56px for default navbar height)
> - `sticky-top` — the navbar stays in its normal position initially, but when the user scrolls past it, it **sticks** to the top of the viewport. No margin fix is needed because it doesn't overlap content

### Marking the Active (Current) Page

To indicate which page the user is currently on, add the `active` class and `aria-current="page"` attribute:

```html
<ul class="navbar-nav">
    <!-- "About" is the current page -->
    <li class="nav-item">
        <a class="nav-link" href="index.html">Home</a>
    </li>
    <li class="nav-item">
        <a class="nav-link active" aria-current="page" href="about.html">About</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="contact.html">Contact</a>
    </li>
</ul>
```

> **Code Explanation:**
> - `active` class — makes the link visually stand out (brighter/bolder text) so users know which page they're on
> - `aria-current="page"` — an accessibility attribute that tells screen readers "this is the current page" (important for visually impaired users)
> - When you create a multi-page website, move the `active` class to the correct link on each page

### Search Form in Navbar — Placement Options

The search form can be placed in different positions within the navbar:

```html
<!-- Search form aligned to the right (most common) -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
        <a class="navbar-brand" href="#">Sharma Books</a>
        <div class="collapse navbar-collapse" id="navContent">
            <ul class="navbar-nav me-auto">  <!-- me-auto pushes search to the right -->
                <li class="nav-item"><a class="nav-link" href="#">Books</a></li>
                <li class="nav-item"><a class="nav-link" href="#">Authors</a></li>
            </ul>
            <!-- Search form on the right side of navbar -->
            <form class="d-flex" role="search">
                <input class="form-control me-2" type="search" 
                       placeholder="Search books..." aria-label="Search">
                <button class="btn btn-outline-light" type="submit">🔍</button>
            </form>
        </div>
    </div>
</nav>
```

> **Code Explanation:**
> - `me-auto` on `navbar-nav` pushes all content after it (the search form) to the **right side**
> - `role="search"` — tells screen readers this is a search form (accessibility)
> - `aria-label="Search"` — provides a label for the input since there's no visible `<label>` element
> - `d-flex` — makes the input and button sit side by side
> - On mobile, the search form appears inside the hamburger menu below the navigation links

---

## 2. Nav Tabs & Pills

### Tabs

```html
<ul class="nav nav-tabs" id="myTab">
    <li class="nav-item">
        <button class="nav-link active" data-bs-toggle="tab" data-bs-target="#html">HTML</button>
    </li>
    <li class="nav-item">
        <button class="nav-link" data-bs-toggle="tab" data-bs-target="#css">CSS</button>
    </li>
    <li class="nav-item">
        <button class="nav-link" data-bs-toggle="tab" data-bs-target="#js">JavaScript</button>
    </li>
</ul>
<div class="tab-content p-3 border border-top-0">
    <div class="tab-pane fade show active" id="html">
        <p>HTML provides the structure of web pages.</p>
    </div>
    <div class="tab-pane fade" id="css">
        <p>CSS controls the appearance and layout.</p>
    </div>
    <div class="tab-pane fade" id="js">
        <p>JavaScript adds interactivity.</p>
    </div>
</div>
```

> **Code Explanation:**
> - `nav nav-tabs` — creates a tab-style navigation bar with underlined active tab
> - `data-bs-toggle="tab"` — tells Bootstrap JS to switch tab content when clicked
> - `data-bs-target="#html"` — links this tab button to the content pane with `id="html"`
> - `active` on the button — marks the default active tab
> - `tab-content` — wrapper for all tab panels
> - `tab-pane fade show active` — `fade` adds a fade animation, `show` makes it visible, `active` marks it as the initially displayed panel
> - Tab panels without `show active` are hidden by default and appear when their tab is clicked

```html
<ul class="nav nav-pills">
    <li class="nav-item">
        <a class="nav-link active" href="#">Active</a>   <!-- Filled/highlighted pill -->
    </li>
    <li class="nav-item">
        <a class="nav-link" href="#">Link</a>             <!-- Regular pill -->
    </li>
</ul>
```

> **Code Explanation:**
> - `nav-pills` — styles the navigation as rounded pill-shaped buttons instead of underlined tabs
> - `active` — fills the pill with the primary color (blue by default)
> - Pills are often used for category filters (e.g., "All | Web | App | AI")

---

## 3. Breadcrumb & Pagination

### Breadcrumb

```html
<nav aria-label="breadcrumb">
    <ol class="breadcrumb">
        <li class="breadcrumb-item"><a href="#">Home</a></li>
        <li class="breadcrumb-item"><a href="#">Courses</a></li>
        <li class="breadcrumb-item active">Web Technology</li>  <!-- Current page (no link) -->
    </ol>
</nav>
```

> **Code Explanation:**
> - `aria-label="breadcrumb"` — tells screen readers this is a breadcrumb navigation (accessibility)
> - `breadcrumb` — styles the list horizontally with `/` separators between items
> - `breadcrumb-item` — each step in the path; linked items let users navigate back
> - `active` on the last item — indicates the current page (displayed as plain text, not a link)
> - Breadcrumbs show the user their current location in the site hierarchy (e.g., Home → Courses → Web Technology)

### Pagination

```html
<nav>
    <ul class="pagination justify-content-center">
        <li class="page-item disabled"><a class="page-link" href="#">Previous</a></li>
        <li class="page-item active"><a class="page-link" href="#">1</a></li>
        <li class="page-item"><a class="page-link" href="#">2</a></li>
        <li class="page-item"><a class="page-link" href="#">3</a></li>
        <li class="page-item"><a class="page-link" href="#">Next</a></li>
    </ul>
</nav>
```

> **Code Explanation:**
> - `pagination` — styles the list as a horizontal set of page buttons
> - `justify-content-center` — centers the pagination horizontally on the page
> - `page-item` — wrapper for each page link
> - `page-link` — the clickable link inside each page item
> - `disabled` — grays out the "Previous" button (user is on page 1, can't go back)
> - `active` — highlights page 1 as the current page (filled blue background)

---

## Practical Session

### 🧪 Lab Experiment 25: Complete Navigation Page

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootstrap Navigation</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary sticky-top">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">🎓 Mandsaur University</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#topNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="topNav">
                <ul class="navbar-nav me-auto">
                    <li class="nav-item"><a class="nav-link active" href="#">Home</a></li>
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" data-bs-toggle="dropdown">Departments</a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="#">BCA</a></li>
                            <li><a class="dropdown-item" href="#">BBA</a></li>
                            <li><a class="dropdown-item" href="#">B.Tech</a></li>
                            <li><hr class="dropdown-divider"></li>
                            <li><a class="dropdown-item" href="#">View All</a></li>
                        </ul>
                    </li>
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" data-bs-toggle="dropdown">BCA Courses</a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="#">Web Technology</a></li>
                            <li><a class="dropdown-item" href="#">Data Structures</a></li>
                            <li><a class="dropdown-item" href="#">Mathematics</a></li>
                        </ul>
                    </li>
                    <li class="nav-item"><a class="nav-link" href="#">Faculty</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Contact</a></li>
                </ul>
                <form class="d-flex">
                    <input class="form-control me-2" type="search" placeholder="Search...">
                    <button class="btn btn-outline-light" type="submit">Search</button>
                </form>
            </div>
        </div>
    </nav>

    <div class="container my-4">

        <!-- Breadcrumb -->
        <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
                <li class="breadcrumb-item"><a href="#">Home</a></li>
                <li class="breadcrumb-item"><a href="#">BCA</a></li>
                <li class="breadcrumb-item"><a href="#">Semester II</a></li>
                <li class="breadcrumb-item active">Web Technology</li>
            </ol>
        </nav>

        <h2>Web Technology — Course Content</h2>

        <!-- Tabs -->
        <ul class="nav nav-tabs mt-4" id="unitTabs">
            <li class="nav-item">
                <button class="nav-link active" data-bs-toggle="tab" data-bs-target="#unit1">Unit 1</button>
            </li>
            <li class="nav-item">
                <button class="nav-link" data-bs-toggle="tab" data-bs-target="#unit2">Unit 2</button>
            </li>
            <li class="nav-item">
                <button class="nav-link" data-bs-toggle="tab" data-bs-target="#unit3">Unit 3</button>
            </li>
            <li class="nav-item">
                <button class="nav-link" data-bs-toggle="tab" data-bs-target="#unit4">Unit 4</button>
            </li>
            <li class="nav-item">
                <button class="nav-link" data-bs-toggle="tab" data-bs-target="#unit5">Unit 5</button>
            </li>
        </ul>
        <div class="tab-content border border-top-0 rounded-bottom p-4 bg-white mb-4">
            <div class="tab-pane fade show active" id="unit1">
                <h5>Internet Technology</h5>
                <p>History of Internet, TCP/IP, DNS, World Wide Web, HTTP/HTTPS</p>
                <span class="badge bg-primary">5 Days</span>
                <span class="badge bg-success">Theory Only</span>
            </div>
            <div class="tab-pane fade" id="unit2">
                <h5>HTML Fundamentals</h5>
                <p>HTML structure, text formatting, links, images, tables, lists, frames</p>
                <span class="badge bg-primary">8 Days</span>
                <span class="badge bg-info">Theory + Lab</span>
            </div>
            <div class="tab-pane fade" id="unit3">
                <h5>HTML5</h5>
                <p>Semantic elements, new form inputs, Canvas, SVG, APIs, responsive design</p>
                <span class="badge bg-primary">5 Days</span>
                <span class="badge bg-info">Theory + Lab</span>
            </div>
            <div class="tab-pane fade" id="unit4">
                <h5>CSS</h5>
                <p>Selectors, Box Model, Flexbox, Grid, Animations, Transitions</p>
                <span class="badge bg-primary">7 Days</span>
                <span class="badge bg-info">Theory + Lab</span>
            </div>
            <div class="tab-pane fade" id="unit5">
                <h5>Bootstrap</h5>
                <p>Grid system, components, navbar, forms, carousel, responsive utilities</p>
                <span class="badge bg-primary">7 Days</span>
                <span class="badge bg-info">Theory + Lab</span>
            </div>
        </div>

        <!-- Pagination -->
        <nav aria-label="Page navigation">
            <ul class="pagination justify-content-center">
                <li class="page-item disabled"><a class="page-link" href="#">&laquo; Previous</a></li>
                <li class="page-item active"><a class="page-link" href="#">1</a></li>
                <li class="page-item"><a class="page-link" href="#">2</a></li>
                <li class="page-item"><a class="page-link" href="#">3</a></li>
                <li class="page-item"><a class="page-link" href="#">Next &raquo;</a></li>
            </ul>
        </nav>
    </div>

    <!-- Footer -->
    <footer class="bg-dark text-white text-center py-3">
        <p class="mb-0">&copy; 2026 Mandsaur University — All Rights Reserved</p>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

> **Code Explanation:**
> - **Navbar**: `navbar-dark bg-primary sticky-top` — a blue navbar that sticks to the top when scrolling
> - **`sticky-top`**: The navbar stays visible as users scroll down — important for easy navigation
> - **Brand**: `navbar-brand fw-bold` with 🎓 emoji — always visible, even on mobile
> - **Two dropdowns**: "Departments" and "BCA Courses" — each with `dropdown-toggle` + `dropdown-menu`
> - **`dropdown-divider`**: A thin line separating "View All" from department links
> - **Search form**: `d-flex` makes input and button sit side by side; placed after `me-auto` so it appears on the right
> - **Breadcrumb**: Shows the navigation path: Home → BCA → Semester II → Web Technology
> - **Tabs (`nav-tabs`)**: Five tabs for five units; each linked to a `tab-pane` using `data-bs-target`
> - **Tab content**: Each `tab-pane` has a heading, description, and badges for day count and type
> - **`border border-top-0 rounded-bottom`**: Creates a box around tab content that visually connects to the active tab (no top border since the tab itself provides it)
> - **Badges**: `badge bg-primary` and `badge bg-info` — small colored labels showing "5 Days" and "Theory + Lab"
> - **Pagination**: Centered page navigation with Previous (disabled), numbered pages, and Next
> - **Footer**: `bg-dark text-white text-center py-3` — dark footer with centered copyright text

---

| Component | Key Classes |
|-----------|------------|
| Navbar | `navbar`, `navbar-expand-lg`, `navbar-dark bg-primary` |
| Toggler | `navbar-toggler`, `collapse navbar-collapse` |
| Dropdown | `dropdown`, `dropdown-toggle`, `dropdown-menu` |
| Tabs | `nav nav-tabs`, `tab-content`, `tab-pane` |
| Breadcrumb | `breadcrumb`, `breadcrumb-item` |
| Pagination | `pagination`, `page-item`, `page-link` |

---

*Day 34 of 55 | Unit 6 — Bootstrap | Web Technology (25BCA060)*
