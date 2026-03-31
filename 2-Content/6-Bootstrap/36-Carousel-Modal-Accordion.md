# Day 36 — Bootstrap Carousel, Modal & Accordion

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 6 — Bootstrap
🧪 **Lab Experiments:** 28, 29

---

## Learning Objectives

By the end of this session, students will be able to:
- Build an image carousel (slideshow) with controls and captions
- Create modal (popup) dialogs with forms
- Build collapsible accordion (FAQ) sections
- Use Bootstrap's tooltip and toast components

---

## 1. Carousel (Slideshow)

```html
<div id="myCarousel" class="carousel slide" data-bs-ride="carousel">
    
    <!-- Indicators -->
    <div class="carousel-indicators">
        <button data-bs-target="#myCarousel" data-bs-slide-to="0" class="active"></button>
        <button data-bs-target="#myCarousel" data-bs-slide-to="1"></button>
        <button data-bs-target="#myCarousel" data-bs-slide-to="2"></button>
    </div>
    
    <!-- Slides -->
    <div class="carousel-inner">
        <div class="carousel-item active">
            <img src="https://via.placeholder.com/1200x400/0d6efd/ffffff?text=Slide+1" 
                 class="d-block w-100" alt="Slide 1">
            <div class="carousel-caption">
                <h5>First Slide</h5>
                <p>Welcome to Web Technology</p>
            </div>
        </div>
        <div class="carousel-item">
            <img src="https://via.placeholder.com/1200x400/198754/ffffff?text=Slide+2" 
                 class="d-block w-100" alt="Slide 2">
            <div class="carousel-caption">
                <h5>Second Slide</h5>
                <p>Learn Bootstrap Components</p>
            </div>
        </div>
        <div class="carousel-item">
            <img src="https://via.placeholder.com/1200x400/ffc107/000000?text=Slide+3" 
                 class="d-block w-100" alt="Slide 3">
            <div class="carousel-caption d-none d-md-block">
                <h5>Third Slide</h5>
                <p>Build responsive websites</p>
            </div>
        </div>
    </div>
    
    <!-- Controls -->
    <button class="carousel-control-prev" data-bs-target="#myCarousel" data-bs-slide="prev">
        <span class="carousel-control-prev-icon"></span>
    </button>
    <button class="carousel-control-next" data-bs-target="#myCarousel" data-bs-slide="next">
        <span class="carousel-control-next-icon"></span>
    </button>
</div>
```

> **Code Explanation:**
> - `carousel slide` — creates the carousel container; `slide` adds the sliding animation
> - `data-bs-ride="carousel"` — auto-starts the slideshow when the page loads
> - **Indicators**: Small clickable dots at the bottom; `data-bs-slide-to="0"` links each dot to a specific slide (zero-indexed)
> - `class="active"` on the first indicator — marks it as the current slide
> - **Slides** (`carousel-inner` + `carousel-item`): Each `carousel-item` holds one slide; the first must have `active`
> - `d-block w-100` on images — ensures images display as block elements at full width
> - **Captions** (`carousel-caption`): Text overlay on each slide
> - `d-none d-md-block` on the third caption — **hides the caption on mobile** phones (saves space on small screens)
> - **Controls**: `carousel-control-prev` and `carousel-control-next` — left/right arrows; `data-bs-slide="prev"/"next"` tells Bootstrap which direction to move

### Keyboard Navigation for Carousel

Bootstrap carousels support **keyboard navigation** automatically:

| Key | Action |
|-----|--------|
| `←` Left Arrow | Go to previous slide |
| `→` Right Arrow | Go to next slide |

> **Note:** Keyboard navigation only works when the carousel has focus. Users can focus the carousel by clicking on it or tabbing to it. This is important for **accessibility** — users who can't use a mouse can still navigate slides with arrow keys.

To pause auto-play when the user hovers (giving them time to read):

```html
<!-- Carousel that pauses on hover and supports keyboard -->
<div id="myCarousel" class="carousel slide" 
     data-bs-ride="carousel" 
     data-bs-pause="hover"
     data-bs-keyboard="true">
    <!-- data-bs-pause="hover" — pauses auto-rotation when mouse hovers over the carousel -->
    <!-- data-bs-keyboard="true" — enables arrow key navigation (true by default) -->
    ...
</div>
```

> **Code Explanation:**
> - `data-bs-pause="hover"` — pauses the auto-sliding when the user's mouse is over the carousel (default behavior, but good to know)
> - `data-bs-keyboard="true"` — explicitly enables keyboard arrow key navigation (this is `true` by default in Bootstrap 5)

### Carousel Options

| Attribute | Value | Purpose |
|-----------|-------|---------|
| `data-bs-ride="carousel"` | Auto-play |
| `data-bs-interval="3000"` | Slide every 3 seconds |
| `data-bs-ride="false"` | No auto-play |
| class `carousel-fade` | Fade transition instead of slide |

---

## 2. Modal (Popup Dialog)

```html
<!-- Trigger Button -->
<button class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#myModal">
    Open Modal
</button>

<!-- Modal -->
<div class="modal fade" id="myModal" tabindex="-1">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Student Login</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
            </div>
            <div class="modal-body">
                <form>
                    <div class="mb-3">
                        <label class="form-label">Email</label>
                        <input type="email" class="form-control">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Password</label>
                        <input type="password" class="form-control">
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" data-bs-dismiss="modal">Cancel</button>
                <button class="btn btn-primary">Login</button>
            </div>
        </div>
    </div>
</div>
```

> **Code Explanation:**
> - **Trigger Button**: `data-bs-toggle="modal"` + `data-bs-target="#myModal"` — clicking this button opens the modal with `id="myModal"`
> - `modal fade` — `fade` adds a smooth fade-in animation when the modal opens
> - `tabindex="-1"` — prevents the modal from being focused by tabbing when it's closed
> - `modal-dialog` — centers the modal and controls its width
> - `modal-content` — the visible modal box (white background with rounded corners)
> - `modal-header` — contains the title and close button
> - `btn-close` + `data-bs-dismiss="modal"` — the × button that closes the modal
> - `modal-body` — the main content area (forms, text, images, etc.)
> - `modal-footer` — bottom section for action buttons (Cancel/Save/Login)

### Modal Focus Management — Accessibility

When a modal opens, Bootstrap automatically:
1. **Traps focus inside the modal** — pressing Tab cycles through only the modal's elements (not the page behind)
2. **Returns focus** to the trigger button when the modal closes
3. **Adds `aria-modal="true"`** — tells screen readers a modal is open

```html
<!-- Modal with proper accessibility attributes (Bootstrap adds most of these automatically) -->
<div class="modal fade" id="accessibleModal" tabindex="-1" 
     aria-labelledby="modalTitle" aria-hidden="true">
    <!-- aria-labelledby links to the modal's heading for screen readers -->
    <!-- aria-hidden="true" tells screen readers to ignore this when closed -->
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="modalTitle">Enrollment Form</h5>
                <!-- id="modalTitle" is referenced by aria-labelledby above -->
                <button type="button" class="btn-close" data-bs-dismiss="modal" 
                        aria-label="Close"></button>
                <!-- aria-label="Close" tells screen readers what this button does -->
            </div>
            <div class="modal-body">
                <p>Fill in your enrollment details below.</p>
            </div>
        </div>
    </div>
</div>
```

> **Code Explanation:**
> - `aria-labelledby="modalTitle"` — screen readers announce the modal's title when it opens (links to the `id` of the heading)
> - `aria-hidden="true"` — tells assistive technology to ignore the modal when it's closed; Bootstrap automatically changes this to `false` when the modal opens
> - `aria-label="Close"` on the close button — since the button only shows ×, screen readers need this label to know its purpose
> - **Focus trapping** happens automatically — you don't need to write any extra code

### Modal Sizes

```html
<div class="modal-dialog modal-sm">...</div>   <!-- Small -->
<div class="modal-dialog">...</div>             <!-- Default -->
<div class="modal-dialog modal-lg">...</div>    <!-- Large -->
<div class="modal-dialog modal-xl">...</div>    <!-- Extra Large -->
<div class="modal-dialog modal-fullscreen">...</div> <!-- Fullscreen -->
```

> **Code Explanation:**
> - `modal-sm` — small modal (~300px wide), used for simple confirmations ("Are you sure?")
> - Default (no size class) — medium modal (~500px wide), good for login forms and short content
> - `modal-lg` — large modal (~800px wide), good for detailed content like course information
> - `modal-xl` — extra large modal (~1140px wide), good for data tables or image previews
> - `modal-fullscreen` — takes up the entire screen, useful for mobile-first interfaces

---

## 3. Accordion (Collapsible Sections)

```html
<div class="accordion" id="faqAccordion">
    <div class="accordion-item">
        <h2 class="accordion-header">
            <button class="accordion-button" data-bs-toggle="collapse" 
                    data-bs-target="#faq1">
                What is Bootstrap?
            </button>
        </h2>
        <div id="faq1" class="accordion-collapse collapse show" 
             data-bs-parent="#faqAccordion">
            <div class="accordion-body">
                Bootstrap is a CSS framework that provides pre-built components
                and a responsive grid system for faster web development.
            </div>
        </div>
    </div>
    <div class="accordion-item">
        <h2 class="accordion-header">
            <button class="accordion-button collapsed" data-bs-toggle="collapse" 
                    data-bs-target="#faq2">
                Is Bootstrap free?
            </button>
        </h2>
        <div id="faq2" class="accordion-collapse collapse" 
             data-bs-parent="#faqAccordion">
            <div class="accordion-body">
                Yes! Bootstrap is completely free and open source under the MIT license.
            </div>
        </div>
    </div>
</div>
```

> **Code Explanation:**
> - `accordion` — the parent container; the `id` is referenced by `data-bs-parent` to create the "only one open at a time" behavior
> - `accordion-item` — each collapsible section (question + answer)
> - `accordion-header` + `accordion-button` — the clickable header; `data-bs-toggle="collapse"` tells Bootstrap to show/hide the linked content
> - `data-bs-target="#faq1"` — links the button to the content with `id="faq1"`
> - `collapse show` — the first item starts open (`show` makes it visible by default)
> - `collapsed` class on the second button — indicates this section is closed (rotates the arrow icon)
> - `data-bs-parent="#faqAccordion"` — **important!** This ensures only one item is open at a time. Without it, multiple items can be open simultaneously
> - `accordion-body` — the content area that slides open/closed

### Accordion Accessibility — ARIA Roles

Bootstrap's accordion **automatically adds accessibility attributes** when initialized:

| Attribute | Added To | Purpose |
|-----------|----------|---------|
| `aria-expanded="true/false"` | Accordion button | Tells screen readers if the section is open or closed |
| `aria-controls="faq1"` | Accordion button | Links button to the content it controls |
| `role="region"` | Accordion collapse | Marks the content as a distinct page region |
| `aria-labelledby="..."` | Accordion collapse | Links content to its header for screen readers |

> **What this means for students:** You don't need to manually add these ARIA attributes — Bootstrap's JavaScript adds them when the page loads. But understanding them helps you know why Bootstrap components work well with screen readers.

```html
<!-- What Bootstrap renders after initialization (you write the left, Bootstrap adds the right) -->
<button class="accordion-button" 
        data-bs-toggle="collapse" 
        data-bs-target="#faq1"
        aria-expanded="true"       
        aria-controls="faq1">      
    <!-- aria-expanded="true" — screen reader announces "expanded" -->
    <!-- aria-controls="faq1" — screen reader knows this button controls the #faq1 panel -->
    What is Bootstrap?
</button>
```

> **Code Explanation:**
> - `aria-expanded="true"` — Bootstrap adds this automatically; it changes to `"false"` when the section is collapsed
> - `aria-controls="faq1"` — tells assistive technology which panel this button toggles
> - Screen readers will announce: "What is Bootstrap?, expanded, button" — helping blind users understand the interface

### Tooltips

```html
<button class="btn btn-info" data-bs-toggle="tooltip" title="Hello from tooltip!">
    Hover me
</button>

<script>
// Initialize all tooltips
const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]');
const tooltipList = [...tooltipTriggerList].map(el => new bootstrap.Tooltip(el));
</script>
```

> **Code Explanation:**
> - `data-bs-toggle="tooltip"` — marks this element as having a tooltip
> - `title="Hello from tooltip!"` — the text that appears in the tooltip popup
> - **Tooltips must be initialized with JavaScript** — they don't work automatically like dropdowns or modals
> - `querySelectorAll('[data-bs-toggle="tooltip"]')` — finds all tooltip elements on the page
> - `new bootstrap.Tooltip(el)` — creates a tooltip instance for each element

### Toasts (Notification popups)

```html
<div class="toast-container position-fixed top-0 end-0 p-3">
    <div class="toast" id="myToast">
        <div class="toast-header bg-success text-white">
            <strong class="me-auto">Success</strong>
            <small>Just now</small>
            <button type="button" class="btn-close btn-close-white" data-bs-dismiss="toast"></button>
        </div>
        <div class="toast-body">Form submitted successfully!</div>
    </div>
</div>

<script>
const toast = new bootstrap.Toast(document.getElementById('myToast'));
toast.show();
</script>
```

> **Code Explanation:**
> - `toast-container position-fixed top-0 end-0 p-3` — positions the toast container in the **top-right corner** of the screen
> - `position-fixed` — stays in place even when the page scrolls
> - `toast` — the notification popup component; hidden by default
> - `toast-header` — colored header with title, timestamp, and close button
> - `btn-close-white` — white close button (for dark header backgrounds)
> - `toast-body` — the notification message text
> - `new bootstrap.Toast(element)` — creates a toast instance
> - `toast.show()` — programmatically displays the toast (it auto-hides after 5 seconds by default)

---

## Practical Session

### 🧪 Lab Experiments 28 & 29: Carousel, Modal & Accordion Page

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Bootstrap Components</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#">🎓 MU — BCA</a>
            <div class="navbar-nav ms-auto">
                <button class="btn btn-outline-light btn-sm" data-bs-toggle="modal" 
                        data-bs-target="#loginModal">Login</button>
            </div>
        </div>
    </nav>

    <!-- Carousel -->
    <div id="heroCarousel" class="carousel slide carousel-fade" data-bs-ride="carousel" data-bs-interval="4000">
        <div class="carousel-indicators">
            <button data-bs-target="#heroCarousel" data-bs-slide-to="0" class="active"></button>
            <button data-bs-target="#heroCarousel" data-bs-slide-to="1"></button>
            <button data-bs-target="#heroCarousel" data-bs-slide-to="2"></button>
        </div>
        <div class="carousel-inner">
            <div class="carousel-item active">
                <div class="bg-primary text-white text-center" style="padding: 120px 0;">
                    <h1 class="display-4">Mandsaur University</h1>
                    <p class="lead">Empowering Minds, Transforming Futures</p>
                    <button class="btn btn-outline-light btn-lg">Learn More</button>
                </div>
            </div>
            <div class="carousel-item">
                <div class="bg-success text-white text-center" style="padding: 120px 0;">
                    <h1 class="display-4">BCA Program</h1>
                    <p class="lead">Build your career in Computer Applications</p>
                    <button class="btn btn-outline-light btn-lg">Apply Now</button>
                </div>
            </div>
            <div class="carousel-item">
                <div class="bg-info text-white text-center" style="padding: 120px 0;">
                    <h1 class="display-4">Web Technology</h1>
                    <p class="lead">Master HTML, CSS, JavaScript & Bootstrap</p>
                    <button class="btn btn-outline-light btn-lg">Start Learning</button>
                </div>
            </div>
        </div>
        <button class="carousel-control-prev" data-bs-target="#heroCarousel" data-bs-slide="prev">
            <span class="carousel-control-prev-icon"></span>
        </button>
        <button class="carousel-control-next" data-bs-target="#heroCarousel" data-bs-slide="next">
            <span class="carousel-control-next-icon"></span>
        </button>
    </div>

    <div class="container my-5">

        <!-- FAQ Accordion -->
        <h2 class="text-primary mb-4 text-center">Frequently Asked Questions</h2>
        <div class="accordion mb-5" id="faqAccordion">
            <div class="accordion-item">
                <h2 class="accordion-header">
                    <button class="accordion-button" data-bs-toggle="collapse" data-bs-target="#faq1">
                        What is Bootstrap?
                    </button>
                </h2>
                <div id="faq1" class="accordion-collapse collapse show" data-bs-parent="#faqAccordion">
                    <div class="accordion-body">
                        Bootstrap is a free, open-source CSS framework developed by Twitter. 
                        It includes pre-designed components, responsive grid, and JavaScript plugins 
                        that help developers build professional websites quickly.
                    </div>
                </div>
            </div>
            <div class="accordion-item">
                <h2 class="accordion-header">
                    <button class="accordion-button collapsed" data-bs-toggle="collapse" data-bs-target="#faq2">
                        Why use Bootstrap over plain CSS?
                    </button>
                </h2>
                <div id="faq2" class="accordion-collapse collapse" data-bs-parent="#faqAccordion">
                    <div class="accordion-body">
                        Bootstrap saves development time with its pre-built, tested components. 
                        It ensures cross-browser compatibility and provides a responsive grid system 
                        that handles different screen sizes automatically.
                    </div>
                </div>
            </div>
            <div class="accordion-item">
                <h2 class="accordion-header">
                    <button class="accordion-button collapsed" data-bs-toggle="collapse" data-bs-target="#faq3">
                        Is Bootstrap 5 different from Bootstrap 4?
                    </button>
                </h2>
                <div id="faq3" class="accordion-collapse collapse" data-bs-parent="#faqAccordion">
                    <div class="accordion-body">
                        Major changes: jQuery is no longer required, new utility API, 
                        improved grid system with xxl breakpoint, RTL support, 
                        updated forms, and new components like offcanvas.
                    </div>
                </div>
            </div>
            <div class="accordion-item">
                <h2 class="accordion-header">
                    <button class="accordion-button collapsed" data-bs-toggle="collapse" data-bs-target="#faq4">
                        How do I add Bootstrap to my project?
                    </button>
                </h2>
                <div id="faq4" class="accordion-collapse collapse" data-bs-parent="#faqAccordion">
                    <div class="accordion-body">
                        The easiest way is via CDN: add the Bootstrap CSS link in the 
                        <code>&lt;head&gt;</code> and the JS script before the closing 
                        <code>&lt;/body&gt;</code> tag. You can also download the files or 
                        use npm in larger projects.
                    </div>
                </div>
            </div>
        </div>

        <!-- Cards with Modal Triggers -->
        <h2 class="text-primary mb-4 text-center">Our Courses</h2>
        <div class="row g-4 mb-5">
            <div class="col-md-4">
                <div class="card shadow-sm h-100">
                    <div class="card-body text-center">
                        <div class="display-1 mb-3">🌐</div>
                        <h5 class="card-title">Web Technology</h5>
                        <p class="card-text">HTML, CSS, JS, Bootstrap</p>
                        <button class="btn btn-primary" data-bs-toggle="modal" 
                                data-bs-target="#courseModal1">Details</button>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card shadow-sm h-100">
                    <div class="card-body text-center">
                        <div class="display-1 mb-3">📊</div>
                        <h5 class="card-title">Data Structures</h5>
                        <p class="card-text">Arrays, Trees, Graphs</p>
                        <button class="btn btn-success" data-bs-toggle="modal" 
                                data-bs-target="#courseModal2">Details</button>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card shadow-sm h-100">
                    <div class="card-body text-center">
                        <div class="display-1 mb-3">🧮</div>
                        <h5 class="card-title">Mathematics</h5>
                        <p class="card-text">Discrete Math, Probability</p>
                        <button class="btn btn-warning" data-bs-toggle="modal" 
                                data-bs-target="#courseModal3">Details</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

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
                            <input type="email" class="form-control" id="loginEmail" placeholder="Email">
                            <label for="loginEmail">Email</label>
                        </div>
                        <div class="form-floating mb-3">
                            <input type="password" class="form-control" id="loginPwd" placeholder="Password">
                            <label for="loginPwd">Password</label>
                        </div>
                        <div class="form-check mb-3">
                            <input class="form-check-input" type="checkbox" id="remember">
                            <label class="form-check-label" for="remember">Remember me</label>
                        </div>
                    </form>
                </div>
                <div class="modal-footer">
                    <button class="btn btn-secondary" data-bs-dismiss="modal">Cancel</button>
                    <button class="btn btn-primary">Login</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Course Detail Modals -->
    <div class="modal fade" id="courseModal1" tabindex="-1">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header bg-primary text-white">
                    <h5 class="modal-title">Web Technology — Details</h5>
                    <button class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <h6>Topics Covered:</h6>
                    <ul>
                        <li>Internet Technology & HTTP</li>
                        <li>HTML & HTML5</li>
                        <li>CSS & Responsive Design</li>
                        <li>JavaScript & DOM</li>
                        <li>Bootstrap Framework</li>
                    </ul>
                    <p><strong>Credits:</strong> 4 | <strong>Exam:</strong> 60 marks (theory) + 40 marks (practical)</p>
                </div>
                <div class="modal-footer">
                    <button class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="courseModal2" tabindex="-1">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header bg-success text-white">
                    <h5 class="modal-title">Data Structures — Details</h5>
                    <button class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <p>Arrays, Linked Lists, Stacks, Queues, Trees, Graphs, Sorting & Searching algorithms.</p>
                </div>
                <div class="modal-footer">
                    <button class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="courseModal3" tabindex="-1">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header bg-warning">
                    <h5 class="modal-title">Mathematics — Details</h5>
                    <button class="btn-close" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <p>Discrete Mathematics, Probability, Linear Algebra, Number Theory.</p>
                </div>
                <div class="modal-footer">
                    <button class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-dark text-white text-center py-3">
        <p class="mb-0">&copy; 2026 Mandsaur University</p>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

> **Code Explanation:**
> - **Navbar**: `navbar-dark bg-dark` with a Login button (`data-bs-toggle="modal"`) — opens the login modal on click
> - **Hero Carousel**: `carousel-fade` adds a fade transition instead of the default slide; `data-bs-interval="4000"` auto-advances every 4 seconds
> - Each slide uses a colored background (`bg-primary`, `bg-success`, `bg-info`) with centered text — no actual images needed
> - `style="padding: 120px 0;"` creates tall hero sections
> - **FAQ Accordion**: `data-bs-parent="#faqAccordion"` ensures only one question is open at a time
> - First accordion item has `collapse show` (starts open); others have `collapsed` on the button (starts closed)
> - **Course Cards**: Three cards with emoji icons, each has a "Details" button that opens a different modal (`data-bs-target="#courseModal1"`, etc.)
> - `shadow-sm` adds a subtle shadow; `h-100` makes all cards equal height
> - **Login Modal**: `form-floating` inputs for email and password; `btn-close-white` for close button on dark header
> - `form-check` with "Remember me" checkbox
> - **Course Detail Modals**: `modal-lg` for wider modals; each has a different colored header matching the card's button color
> - The Web Technology modal includes a topic list and exam details
> - **Footer**: Simple dark footer with copyright

---

| Component | Key Classes/Attributes |
|-----------|----------------------|
| Carousel | `carousel slide`, `carousel-inner`, `carousel-item` |
| Controls | `carousel-control-prev/next`, `data-bs-slide` |
| Modal | `modal fade`, `modal-dialog`, `modal-content` |
| Accordion | `accordion`, `accordion-item`, `accordion-collapse` |
| Tooltip | `data-bs-toggle="tooltip"`, `title="..."` |
| Toast | `toast`, `toast-header`, `toast-body` |

---

*Day 36 of 55 | Unit 6 — Bootstrap | Web Technology (25BCA060)*
