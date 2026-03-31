# Day 37 — Responsive Design with Bootstrap & Mini-Project

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 6 — Bootstrap
🧪 **Lab Experiment:** 30

---

## Learning Objectives

By the end of this session, students will be able to:
- Use Bootstrap's responsive utility classes
- Hide/show elements at different breakpoints
- Build a complete responsive website combining all Bootstrap components
- Apply mobile-first design principles

---

## 1. Responsive Display Utilities

> **Analogy:** Responsive utilities are like a **smart wardrobe** — you wear different clothes for different weather. Similarly, your website shows different elements depending on the screen size.

### Mobile-First Approach

> **Key Principle:** Always **design for mobile first**, then enhance for larger screens. This is how Bootstrap works internally, and it's the recommended approach for all modern websites.
>
> Why mobile-first?
> - Over 60% of web traffic in India comes from mobile phones
> - It's easier to add features for big screens than to remove them for small screens
> - Google prioritizes mobile-friendly websites in search results
>
> **Process:**
> 1. Start with the mobile layout (single column, stacked elements)
> 2. Add `col-md-*` classes for tablet enhancements
> 3. Add `col-lg-*` classes for desktop enhancements
> 4. Test on real devices or Chrome DevTools

### Show/Hide at Breakpoints

| Class | Visible On |
|-------|-----------|
| `d-none` | Hidden on all |
| `d-block` | Visible on all |
| `d-none d-md-block` | Hidden on xs/sm, visible on md+ |
| `d-block d-lg-none` | Visible on xs/sm/md, hidden on lg+ |
| `d-none d-sm-block d-md-none` | Only visible on sm |

```html
<!-- Only visible on mobile -->
<div class="d-block d-md-none">📱 Mobile Menu</div>

<!-- Only visible on desktop -->
<div class="d-none d-lg-block">🖥️ Desktop Sidebar</div>

<!-- Hidden on tablets only -->
<div class="d-block d-md-none d-lg-block">Visible everywhere except md</div>
```

> **Code Explanation:**
> - `d-block d-md-none` — **visible on phones** (`d-block` shows it by default), **hidden on tablets and above** (`d-md-none` hides from 768px+)
> - `d-none d-lg-block` — **hidden on phones and tablets** (`d-none`), **visible on desktops** (`d-lg-block` shows from 992px+)
> - `d-block d-md-none d-lg-block` — visible everywhere **except** medium screens (hidden only on md)
> - The pattern is: start with the **default behavior**, then override at specific breakpoints

---

## 2. Responsive Text & Alignment

```html
<!-- Text alignment changes per breakpoint -->
<p class="text-center text-md-start">Centered on mobile, left on md+</p>
<p class="text-end text-lg-center">Right on small, centered on lg+</p>

<!-- Responsive font size (Bootstrap 5.3+) -->
<h1 class="fs-1">Responsive heading</h1>
<p class="fs-6">Smaller text</p>
```

> **Code Explanation:**
> - `text-center text-md-start` — centered on mobile, left-aligned on medium+ (useful for hero sections)
> - `text-end text-lg-center` — right-aligned on small/medium, centered on large+
> - `fs-1` through `fs-6` — font-size utility classes; `fs-1` is the largest (~2.5rem), `fs-6` is the smallest (~0.875rem)

---

## 3. Responsive Flexbox

```html
<!-- Stack on mobile, row on desktop -->
<div class="d-flex flex-column flex-md-row gap-3">
    <div class="p-3 bg-primary text-white">Item 1</div>
    <div class="p-3 bg-success text-white">Item 2</div>
    <div class="p-3 bg-warning">Item 3</div>
</div>

<!-- Different justify at breakpoints -->
<div class="d-flex justify-content-center justify-content-lg-between">
    <span>A</span><span>B</span><span>C</span>
</div>
```

> **Code Explanation:**
> - `d-flex flex-column flex-md-row` — stacks items vertically on mobile (`flex-column`), switches to horizontal on tablets+ (`flex-md-row`)
> - `gap-3` — adds 1rem gap between flex items (works in both directions)
> - `justify-content-center` — centers items on small screens
> - `justify-content-lg-between` — on large screens, spreads items with space between them

---

## 4. Responsive Spacing

```html
<!-- Different padding at different breakpoints -->
<div class="p-2 p-md-4 p-lg-5">Responsive padding</div>

<!-- Different margin -->
<div class="mt-2 mt-md-4 mt-lg-5">Responsive margin-top</div>
```

> **Code Explanation:**
> - `p-2 p-md-4 p-lg-5` — padding grows with screen size: 0.5rem on mobile → 1.5rem on tablet → 3rem on desktop
> - `mt-2 mt-md-4 mt-lg-5` — same concept but for margin-top
> - This pattern gives **more breathing room** on larger screens where there's more space available

---

## 5. Responsive Images & Embeds

```html
<!-- Always responsive -->
<img src="photo.jpg" class="img-fluid" alt="...">

<!-- Responsive video embed (16:9) -->
<div class="ratio ratio-16x9">
    <iframe src="https://www.youtube.com/embed/example" allowfullscreen></iframe>
</div>

<!-- 4:3 ratio -->
<div class="ratio ratio-4x3">
    <iframe src="..." allowfullscreen></iframe>
</div>
```

> **Code Explanation:**
> - `img-fluid` — the most important responsive image class; sets `max-width: 100%` and `height: auto` so images shrink to fit their container
> - `ratio ratio-16x9` — creates a responsive container that maintains a 16:9 aspect ratio (standard for videos)
> - The iframe inside the `ratio` container automatically fills it while keeping the correct proportions
> - `ratio-4x3` — for older video formats or presentations

### Responsive Image Optimization

For production websites, combine `img-fluid` with performance techniques:

```html
<!-- Lazy loading: image loads only when user scrolls to it -->
<img src="campus-main.jpg" class="img-fluid" alt="Mandsaur University campus" 
     loading="lazy">

<!-- srcset: browser picks the best image size for the device -->
<img srcset="campus-small.jpg 400w,    
             campus-medium.jpg 800w,   
             campus-large.jpg 1200w"   
     sizes="(max-width: 576px) 100vw,  
            (max-width: 992px) 50vw,   
            33vw"                      
     src="campus-medium.jpg"           
     class="img-fluid" 
     alt="University campus"
     loading="lazy">
```

> **Code Explanation:**
> - `loading="lazy"` — defers image loading until the user scrolls near it (saves bandwidth on mobile)
> - `srcset` — provides multiple versions of the same image at different widths (400px, 800px, 1200px)
> - `sizes` — tells the browser how wide the image will display at each breakpoint:
>   - On phones (≤576px): image takes 100% of viewport width → browser picks 400w image
>   - On tablets (≤992px): image takes 50% of viewport → browser picks 800w image
>   - On desktops: image takes 33% of viewport → browser picks 1200w image
> - `src` — fallback for browsers that don't support srcset
> - **Use `loading="lazy"` on all images except the first visible one** (hero images should load immediately)

---

## Testing Responsiveness — Chrome DevTools Guide

To test how your website looks on different devices, use **Chrome DevTools Device Toolbar**:

### How to Open Device Toolbar
1. Open your HTML file in Google Chrome
2. Press `F12` (or `Ctrl + Shift + I`) to open DevTools
3. Click the **📱 device icon** (Toggle Device Toolbar) or press `Ctrl + Shift + M`
4. Select a device from the dropdown (iPhone, iPad, Samsung Galaxy, etc.)

### Common Device Sizes to Test

| Device | Width | Breakpoint | What to Check |
|--------|:-----:|:----------:|--------------|
| iPhone SE | 375px | xs | Mobile layout, hamburger menu, stacked cards |
| iPhone 14 | 390px | xs | Same as above, slightly wider |
| iPad Mini | 768px | md | Tablet layout, 2-column grids, visible sidebar |
| iPad Air | 820px | md | Same as iPad Mini |
| Laptop | 1024px | lg | Desktop layout, horizontal navbar, 3+ column grids |
| Desktop | 1440px | xl | Full desktop experience, all elements visible |

### Quick Responsive Checklist

- [ ] Does the navbar collapse to hamburger on mobile?
- [ ] Do cards/columns stack vertically on small screens?
- [ ] Is text readable without horizontal scrolling?
- [ ] Do images fit within their containers?
- [ ] Is the form usable with a touch keyboard?
- [ ] Do hidden elements (`d-none d-md-block`) work correctly?

---

## Practical Session

### 🧪 Lab Experiment 30: Complete Responsive Website

Build a multi-section responsive landing page using all Bootstrap concepts covered in this unit.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mandsaur University — BCA Department</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .hero { padding: 100px 0; }
        .feature-icon { font-size: 3rem; }
        section { padding: 60px 0; }
        .footer-links a { color: #adb5bd; text-decoration: none; }
        .footer-links a:hover { color: white; }
    </style>
</head>
<body>

    <!-- ==================== NAVBAR ==================== -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top shadow">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">🎓 Mandsaur University</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#siteNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="siteNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item"><a class="nav-link active" href="#home">Home</a></li>
                    <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
                    <li class="nav-item"><a class="nav-link" href="#courses">Courses</a></li>
                    <li class="nav-item"><a class="nav-link" href="#faculty">Faculty</a></li>
                    <li class="nav-item"><a class="nav-link" href="#faq">FAQ</a></li>
                    <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
                </ul>
                <!-- Only visible on larger screens -->
                <div class="d-none d-lg-block ms-3">
                    <button class="btn btn-outline-light btn-sm" data-bs-toggle="modal" 
                            data-bs-target="#loginModal">Login</button>
                </div>
            </div>
        </div>
    </nav>

    <!-- ==================== HERO CAROUSEL ==================== -->
    <section id="home" style="margin-top: 56px;">
        <div id="heroSlider" class="carousel slide carousel-fade" data-bs-ride="carousel">
            <div class="carousel-inner">
                <div class="carousel-item active">
                    <div class="hero bg-primary text-white text-center">
                        <div class="container">
                            <h1 class="display-3 fw-bold">BCA Department</h1>
                            <p class="lead fs-4">Bachelor of Computer Applications</p>
                            <p class="d-none d-md-block">Shaping the next generation of IT professionals at Mandsaur University</p>
                            <a href="#courses" class="btn btn-outline-light btn-lg mt-3">Explore Courses</a>
                        </div>
                    </div>
                </div>
                <div class="carousel-item">
                    <div class="hero bg-success text-white text-center">
                        <div class="container">
                            <h1 class="display-3 fw-bold">Web Technology</h1>
                            <p class="lead fs-4">Semester II — 25BCA060</p>
                            <a href="#courses" class="btn btn-outline-light btn-lg mt-3">View Syllabus</a>
                        </div>
                    </div>
                </div>
                <div class="carousel-item">
                    <div class="hero bg-info text-dark text-center">
                        <div class="container">
                            <h1 class="display-3 fw-bold">Build. Learn. Create.</h1>
                            <p class="lead fs-4">Hands-on lab sessions every day</p>
                            <a href="#contact" class="btn btn-dark btn-lg mt-3">Get Started</a>
                        </div>
                    </div>
                </div>
            </div>
            <button class="carousel-control-prev" data-bs-target="#heroSlider" data-bs-slide="prev">
                <span class="carousel-control-prev-icon"></span>
            </button>
            <button class="carousel-control-next" data-bs-target="#heroSlider" data-bs-slide="next">
                <span class="carousel-control-next-icon"></span>
            </button>
        </div>
    </section>

    <!-- ==================== ABOUT ==================== -->
    <section id="about" class="bg-light">
        <div class="container">
            <h2 class="text-center text-primary mb-5">About the BCA Program</h2>
            <div class="row g-4 align-items-center">
                <div class="col-lg-6">
                    <p class="fs-5">The BCA program at Mandsaur University provides a strong 
                    foundation in computer science, software development, and IT skills. 
                    Our curriculum combines theoretical knowledge with practical lab experience.</p>
                    
                    <div class="row g-3 mt-3">
                        <div class="col-6">
                            <div class="text-center p-3 border rounded bg-white">
                                <div class="display-6 text-primary fw-bold">3</div>
                                <small class="text-muted">Year Program</small>
                            </div>
                        </div>
                        <div class="col-6">
                            <div class="text-center p-3 border rounded bg-white">
                                <div class="display-6 text-success fw-bold">6</div>
                                <small class="text-muted">Semesters</small>
                            </div>
                        </div>
                        <div class="col-6">
                            <div class="text-center p-3 border rounded bg-white">
                                <div class="display-6 text-warning fw-bold">30+</div>
                                <small class="text-muted">Lab Experiments</small>
                            </div>
                        </div>
                        <div class="col-6">
                            <div class="text-center p-3 border rounded bg-white">
                                <div class="display-6 text-danger fw-bold">100%</div>
                                <small class="text-muted">Practical Focus</small>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-6">
                    <div class="card shadow">
                        <div class="card-header bg-primary text-white">Semester II Subjects</div>
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item d-flex justify-content-between">
                                Web Technology <span class="badge bg-primary">25BCA060</span>
                            </li>
                            <li class="list-group-item d-flex justify-content-between">
                                Data Structures <span class="badge bg-success">25BCA061</span>
                            </li>
                            <li class="list-group-item d-flex justify-content-between">
                                Mathematics <span class="badge bg-warning text-dark">25BCA062</span>
                            </li>
                            <li class="list-group-item d-flex justify-content-between">
                                Communication Skills <span class="badge bg-info">25BCA063</span>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ==================== COURSES ==================== -->
    <section id="courses">
        <div class="container">
            <h2 class="text-center text-primary mb-5">Web Technology — Units</h2>
            <div class="row g-4">
                <div class="col-sm-6 col-lg-4">
                    <div class="card h-100 shadow-sm border-0">
                        <div class="card-body text-center">
                            <div class="feature-icon text-primary mb-3">🌐</div>
                            <h5>Internet Technology</h5>
                            <p class="text-muted">TCP/IP, DNS, HTTP, World Wide Web</p>
                            <span class="badge bg-secondary">Unit 1 — 5 Days</span>
                        </div>
                    </div>
                </div>
                <div class="col-sm-6 col-lg-4">
                    <div class="card h-100 shadow-sm border-0">
                        <div class="card-body text-center">
                            <div class="feature-icon text-danger mb-3">📄</div>
                            <h5>HTML & HTML5</h5>
                            <p class="text-muted">Tags, Forms, Semantic Elements, Canvas</p>
                            <span class="badge bg-secondary">Units 2-3 — 13 Days</span>
                        </div>
                    </div>
                </div>
                <div class="col-sm-6 col-lg-4">
                    <div class="card h-100 shadow-sm border-0">
                        <div class="card-body text-center">
                            <div class="feature-icon text-info mb-3">🎨</div>
                            <h5>CSS</h5>
                            <p class="text-muted">Selectors, Box Model, Flexbox, Animations</p>
                            <span class="badge bg-secondary">Unit 4 — 7 Days</span>
                        </div>
                    </div>
                </div>
                <div class="col-sm-6 col-lg-4">
                    <div class="card h-100 shadow-sm border-0">
                        <div class="card-body text-center">
                            <div class="feature-icon text-warning mb-3">⚡</div>
                            <h5>JavaScript</h5>
                            <p class="text-muted">Variables, DOM, Events, Validation</p>
                            <span class="badge bg-secondary">Unit 5 — 5 Days</span>
                        </div>
                    </div>
                </div>
                <div class="col-sm-6 col-lg-4">
                    <div class="card h-100 shadow-sm border-0">
                        <div class="card-body text-center">
                            <div class="feature-icon text-success mb-3">📱</div>
                            <h5>Bootstrap</h5>
                            <p class="text-muted">Grid, Components, Responsive Design</p>
                            <span class="badge bg-primary">Unit 6 — 7 Days (Current)</span>
                        </div>
                    </div>
                </div>
                <div class="col-sm-6 col-lg-4">
                    <div class="card h-100 shadow-sm border-0">
                        <div class="card-body text-center">
                            <div class="feature-icon text-dark mb-3">🗄️</div>
                            <h5>Web Forms & Database</h5>
                            <p class="text-muted">Forms, Server-side, Database Integration</p>
                            <span class="badge bg-secondary">Unit 7 — 4 Days</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ==================== FAQ ==================== -->
    <section id="faq" class="bg-light">
        <div class="container">
            <h2 class="text-center text-primary mb-5">Frequently Asked Questions</h2>
            <div class="row justify-content-center">
                <div class="col-lg-8">
                    <div class="accordion" id="faqAccordion">
                        <div class="accordion-item">
                            <h2 class="accordion-header">
                                <button class="accordion-button" data-bs-toggle="collapse" data-bs-target="#f1">
                                    What are the prerequisites for this course?
                                </button>
                            </h2>
                            <div id="f1" class="accordion-collapse collapse show" data-bs-parent="#faqAccordion">
                                <div class="accordion-body">
                                    Basic computer knowledge is sufficient. Semester I courses like 
                                    Programming Fundamentals will be helpful but not mandatory.
                                </div>
                            </div>
                        </div>
                        <div class="accordion-item">
                            <h2 class="accordion-header">
                                <button class="accordion-button collapsed" data-bs-toggle="collapse" data-bs-target="#f2">
                                    Do I need to install any software?
                                </button>
                            </h2>
                            <div id="f2" class="accordion-collapse collapse" data-bs-parent="#faqAccordion">
                                <div class="accordion-body">
                                    You need a text editor (VS Code recommended) and a web browser 
                                    (Chrome/Firefox). All other tools are available online via CDN.
                                </div>
                            </div>
                        </div>
                        <div class="accordion-item">
                            <h2 class="accordion-header">
                                <button class="accordion-button collapsed" data-bs-toggle="collapse" data-bs-target="#f3">
                                    How is the exam structured?
                                </button>
                            </h2>
                            <div id="f3" class="accordion-collapse collapse" data-bs-parent="#faqAccordion">
                                <div class="accordion-body">
                                    Theory: 60 marks (end-semester) + 40 marks (internal). 
                                    Practical: 60 marks (lab exam) + 40 marks (continuous assessment).
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ==================== CONTACT ==================== -->
    <section id="contact">
        <div class="container">
            <h2 class="text-center text-primary mb-5">Contact Us</h2>
            <div class="row g-4">
                <div class="col-lg-6">
                    <div class="card shadow h-100">
                        <div class="card-body">
                            <h5 class="card-title mb-4">Send a Message</h5>
                            <form class="needs-validation" novalidate>
                                <div class="row g-3 mb-3">
                                    <div class="col-md-6">
                                        <div class="form-floating">
                                            <input type="text" class="form-control" id="cName" placeholder="Name" required>
                                            <label for="cName">Your Name</label>
                                        </div>
                                    </div>
                                    <div class="col-md-6">
                                        <div class="form-floating">
                                            <input type="email" class="form-control" id="cEmail" placeholder="Email" required>
                                            <label for="cEmail">Email</label>
                                        </div>
                                    </div>
                                </div>
                                <div class="form-floating mb-3">
                                    <select class="form-select" id="cSubject" required>
                                        <option value="" disabled selected>Choose...</option>
                                        <option>Admission Inquiry</option>
                                        <option>Course Information</option>
                                        <option>General Question</option>
                                    </select>
                                    <label for="cSubject">Subject</label>
                                </div>
                                <div class="form-floating mb-3">
                                    <textarea class="form-control" id="cMsg" placeholder="Message" 
                                              style="height: 120px" required></textarea>
                                    <label for="cMsg">Your Message</label>
                                </div>
                                <button type="submit" class="btn btn-primary w-100">Send Message</button>
                            </form>
                        </div>
                    </div>
                </div>
                <div class="col-lg-6">
                    <div class="card shadow h-100">
                        <div class="card-body">
                            <h5 class="card-title mb-4">Contact Information</h5>
                            <ul class="list-unstyled">
                                <li class="mb-3">
                                    <strong>🏫 Address:</strong><br>
                                    Mandsaur University, Mandsaur, MP — 458001
                                </li>
                                <li class="mb-3">
                                    <strong>📧 Email:</strong><br>
                                    bca@mfrims.ac.in
                                </li>
                                <li class="mb-3">
                                    <strong>📞 Phone:</strong><br>
                                    +91-7422-123456
                                </li>
                                <li class="mb-3">
                                    <strong>🕐 Office Hours:</strong><br>
                                    Monday – Saturday, 9:00 AM – 5:00 PM
                                </li>
                            </ul>
                            <hr>
                            <h6>Follow Us</h6>
                            <button class="btn btn-outline-primary btn-sm me-1">Facebook</button>
                            <button class="btn btn-outline-info btn-sm me-1">Twitter</button>
                            <button class="btn btn-outline-danger btn-sm me-1">Instagram</button>
                            <button class="btn btn-outline-dark btn-sm">LinkedIn</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ==================== FOOTER ==================== -->
    <footer class="bg-dark text-white py-4 mt-5">
        <div class="container">
            <div class="row g-4">
                <div class="col-md-4">
                    <h5>🎓 Mandsaur University</h5>
                    <p class="text-muted small">Empowering minds and transforming futures through quality education.</p>
                </div>
                <div class="col-md-4 footer-links">
                    <h6>Quick Links</h6>
                    <ul class="list-unstyled small">
                        <li><a href="#home">Home</a></li>
                        <li><a href="#about">About</a></li>
                        <li><a href="#courses">Courses</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </div>
                <div class="col-md-4 footer-links">
                    <h6>Resources</h6>
                    <ul class="list-unstyled small">
                        <li><a href="#">Syllabus</a></li>
                        <li><a href="#">Time Table</a></li>
                        <li><a href="#">Results</a></li>
                        <li><a href="#">Library</a></li>
                    </ul>
                </div>
            </div>
            <hr class="my-3">
            <div class="text-center text-muted small">
                &copy; 2026 Mandsaur University — BCA Department. All rights reserved.
            </div>
        </div>
    </footer>

    <!-- Login Modal -->
    <div class="modal fade" id="loginModal" tabindex="-1">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header bg-dark text-white">
                    <h5 class="modal-title">Student Login</h5>
                    <button class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <form>
                        <div class="form-floating mb-3">
                            <input type="email" class="form-control" id="lEmail" placeholder="Email">
                            <label for="lEmail">Email</label>
                        </div>
                        <div class="form-floating mb-3">
                            <input type="password" class="form-control" id="lPwd" placeholder="Password">
                            <label for="lPwd">Password</label>
                        </div>
                        <button class="btn btn-primary w-100">Login</button>
                    </form>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // Bootstrap form validation
        (function () {
            'use strict';
            const forms = document.querySelectorAll('.needs-validation');
            Array.from(forms).forEach(function (form) {
                form.addEventListener('submit', function (event) {
                    event.preventDefault();
                    if (!form.checkValidity()) {
                        event.stopPropagation();
                    } else {
                        alert('Form submitted successfully!');
                        form.reset();
                        form.classList.remove('was-validated');
                        return;
                    }
                    form.classList.add('was-validated');
                }, false);
            });
        })();
    </script>

</body>
</html>
```

> **Code Explanation:**
>
> **Navbar Section:**
> - `navbar-dark bg-dark fixed-top shadow` — dark navbar that **stays fixed** at the top of the viewport when scrolling; `shadow` adds a subtle drop shadow for depth
> - `collapse navbar-collapse` — links collapse into a hamburger menu on screens below `lg`
> - `d-none d-lg-block` on the Login button — hides the login button on mobile (saves navbar space)
> - `ms-3` — margin-start (left) of 1rem, separating the button from nav links
>
> **Hero Carousel Section:**
> - `style="margin-top: 56px;"` — compensates for the `fixed-top` navbar that overlaps content
> - `carousel-fade` — uses fade transition instead of slide for a smoother hero effect
> - Three slides with different `bg-` colors; each has a heading, tagline, and CTA button
> - `d-none d-md-block` on the first slide's description — hides extra text on mobile to keep the hero clean
> - `btn-outline-light btn-lg` — large transparent button with white border (contrasts with colored backgrounds)
>
> **About Section:**
> - `bg-light` — light gray background to visually separate this section from others
> - `row g-4 align-items-center` — two columns vertically centered; `g-4` adds spacing between columns
> - Statistics boxes: nested `row g-3` with `col-6` creates a 2×2 grid of stat counters
> - `display-6 text-primary fw-bold` — large bold colored number for visual impact
> - Card with `list-group-flush` — displays semester subjects with colored badges for course codes
>
> **Courses Section:**
> - `col-sm-6 col-lg-4` — 2 cards per row on tablets, 3 on desktops, stacked on phones
> - `border-0` on cards — removes the default card border for a cleaner look
> - `feature-icon` (custom CSS) — sets emoji font size to 3rem
> - `badge bg-primary` on Bootstrap card — indicates it's the current unit
>
> **FAQ Section:**
> - `row justify-content-center` + `col-lg-8` — centers the accordion at 66% width on large screens
> - `data-bs-parent="#faqAccordion"` — ensures only one FAQ answer is open at a time
>
> **Contact Section:**
> - `row g-4` with `col-lg-6` — form and contact info side by side on desktops
> - `form-floating` — modern floating label inputs
> - `needs-validation novalidate` — Bootstrap validation (browser validation disabled, custom Bootstrap messages shown)
> - Contact info uses emojis (🏫, 📧, 📞, 🕐) instead of icons — works without any icon library
> - Social media buttons use `btn-outline-*` variants for colored borders without fill
>
> **Footer:**
> - Three-column layout (`col-md-4`) — brand info, quick links, and resources
> - `footer-links a` (custom CSS) — gray links that turn white on hover
> - `text-muted small` — smaller, lighter text for copyright notice
>
> **Login Modal:**
> - `form-floating` inputs for email and password
> - No `modal-footer` — the login button is inside the `modal-body` for a compact design
>
> **JavaScript:**
> - Standard Bootstrap validation script — prevents submission of invalid forms and adds `was-validated` class to trigger visual feedback
> - `event.preventDefault()` on all form submissions — since there's no backend server, forms are handled client-side only
> - On successful validation: shows alert, resets form, removes validation classes

---

## Summary

| Concept | Key Classes |
|---------|------------|
| Show/Hide | `d-none d-md-block`, `d-block d-lg-none` |
| Responsive text | `text-center text-md-start` |
| Responsive spacing | `p-2 p-md-4 p-lg-5` |
| Responsive flex | `flex-column flex-md-row` |
| Responsive embed | `ratio ratio-16x9` |
| Responsive images | `img-fluid` |

---

## Unit 6 Complete!

You've now covered all core Bootstrap concepts:
- **Day 31:** Setup, containers, typography, utility classes
- **Day 32:** 12-column grid, responsive breakpoints, gutters
- **Day 33:** Cards, tables, images, list groups
- **Day 34:** Navbar, tabs, breadcrumbs, pagination
- **Day 35:** Forms, validation, floating labels
- **Day 36:** Carousel, modals, accordion, tooltips
- **Day 37:** Responsive utilities, complete website project

---

*Day 37 of 55 | Unit 6 — Bootstrap | Web Technology (25BCA060)*
