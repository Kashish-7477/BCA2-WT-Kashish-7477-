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

---

## 4. Responsive Spacing

```html
<!-- Different padding at different breakpoints -->
<div class="p-2 p-md-4 p-lg-5">Responsive padding</div>

<!-- Different margin -->
<div class="mt-2 mt-md-4 mt-lg-5">Responsive margin-top</div>
```

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
