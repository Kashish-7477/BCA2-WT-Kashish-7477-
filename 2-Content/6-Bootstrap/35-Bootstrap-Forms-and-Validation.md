# Day 35 — Bootstrap Forms & Validation

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 6 — Bootstrap
🧪 **Lab Experiments:** 26, 27

---

## Learning Objectives

By the end of this session, students will be able to:
- Build styled forms using Bootstrap form classes
- Create horizontal, inline, and floating-label forms
- Use Bootstrap's built-in validation styles
- Build a contact/registration form with Bootstrap

---

## 1. Bootstrap Form Controls

```html
<!-- Basic Form -->
<form>
    <div class="mb-3">
        <label for="name" class="form-label">Full Name</label>
        <input type="text" class="form-control" id="name" placeholder="Enter your name">
    </div>
    <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <input type="email" class="form-control" id="email" placeholder="name@example.com">
    </div>
    <div class="mb-3">
        <label for="msg" class="form-label">Message</label>
        <textarea class="form-control" id="msg" rows="3"></textarea>
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

> **Code Explanation:**
> - `mb-3` — adds margin-bottom of 1rem below each form group (spacing between fields)
> - `form-label` — styles the label text (proper font size and spacing above the input)
> - `for="name"` on label + `id="name"` on input — **links the label to the input** so clicking the label focuses the input (important for accessibility)
> - `form-control` — Bootstrap's main class for text inputs; adds consistent padding, border, and focus styling
> - `placeholder` — gray hint text that disappears when user starts typing
> - `textarea` with `rows="3"` — a multi-line input box, 3 rows tall

### Form Control Sizes

```html
<input class="form-control form-control-lg" placeholder="Large">
<input class="form-control" placeholder="Normal">
<input class="form-control form-control-sm" placeholder="Small">
```

> **Code Explanation:**
> - `form-control-lg` — makes the input taller with larger text (useful for prominent fields like search boxes)
> - `form-control` alone — standard/default size
> - `form-control-sm` — compact input with smaller text (useful for filters or inline forms)

---

## 2. Form Layouts

### Horizontal Form

```html
<form>
    <div class="row mb-3">
        <label for="name" class="col-sm-3 col-form-label">Name</label>  <!-- Label takes 25% width -->
        <div class="col-sm-9">                                           <!-- Input takes 75% width -->
            <input type="text" class="form-control" id="name">
        </div>
    </div>
    <div class="row mb-3">
        <label for="email" class="col-sm-3 col-form-label">Email</label>
        <div class="col-sm-9">
            <input type="email" class="form-control" id="email">
        </div>
    </div>
</form>
```

> **Code Explanation:**
> - `row` — uses Bootstrap's grid system to place label and input side by side
> - `col-sm-3` on label — label takes 25% width on small screens and above
> - `col-sm-9` on input wrapper — input takes 75% width (3+9=12)
> - `col-form-label` — vertically aligns the label text with the input field
> - On screens **below sm (576px)**, the label and input stack vertically (mobile-first behavior)

### Inline Form

```html
<form class="row row-cols-lg-auto g-3 align-items-center">
    <div class="col-12">
        <input type="text" class="form-control" placeholder="Name">
    </div>
    <div class="col-12">
        <input type="email" class="form-control" placeholder="Email">
    </div>
    <div class="col-12">
        <button type="submit" class="btn btn-primary">Subscribe</button>
    </div>
</form>
```

> **Code Explanation:**
> - `row row-cols-lg-auto` — uses grid system to place form elements in a row on large screens
> - `g-3 align-items-center` — gap between elements + vertically centers them
> - `col-12` — on small screens, each form element takes full width (stacks vertically)
> - On large screens (`lg+`), elements sit side by side in one row — perfect for newsletter signup bars

```html
<div class="form-floating mb-3">
    <input type="email" class="form-control" id="floatEmail" placeholder="name@example.com">
    <label for="floatEmail">Email address</label>
</div>
<div class="form-floating mb-3">
    <input type="password" class="form-control" id="floatPwd" placeholder="Password">
    <label for="floatPwd">Password</label>
</div>
```

> **Code Explanation:**
> - `form-floating` — wraps the input and label together; the label **starts inside** the input field and **floats up** when the user clicks or types
> - **Important**: The `<input>` must come **before** the `<label>` inside `form-floating` (reverse of normal order)
> - `placeholder` is still required (Bootstrap uses it internally for the floating effect)
> - Floating labels look modern and save vertical space — commonly seen on login forms

---

## 3. Checkboxes, Radios & Select

```html
<!-- Checkboxes -->
<div class="form-check">
    <input class="form-check-input" type="checkbox" id="html" checked>
    <label class="form-check-label" for="html">HTML</label>
</div>
<div class="form-check">
    <input class="form-check-input" type="checkbox" id="css">
    <label class="form-check-label" for="css">CSS</label>
</div>

<!-- Toggle Switch -->
<div class="form-check form-switch">
    <input class="form-check-input" type="checkbox" id="newsletter">
    <label class="form-check-label" for="newsletter">Subscribe to newsletter</label>
</div>

<!-- Radio Buttons -->
<div class="form-check">
    <input class="form-check-input" type="radio" name="gender" id="male" checked>
    <label class="form-check-label" for="male">Male</label>
</div>
<div class="form-check">
    <input class="form-check-input" type="radio" name="gender" id="female">
    <label class="form-check-label" for="female">Female</label>
</div>

<!-- Select -->
<select class="form-select">
    <option selected disabled>Choose...</option>
    <option value="1">Web Technology</option>
    <option value="2">Data Structures</option>
</select>
```

> **Code Explanation:**
> - **Checkboxes** (`form-check` + `form-check-input`): Each checkbox gets proper spacing and alignment
> - `checked` attribute — pre-selects a checkbox (HTML is checked by default)
> - `for="html"` on label + `id="html"` on input — clicking the label text also toggles the checkbox
> - **Toggle Switch** (`form-check form-switch`): Styled as a sliding on/off toggle — same as a checkbox but looks modern
> - **Radio buttons**: Same structure as checkboxes but `type="radio"` + shared `name="gender"` ensures only one can be selected at a time
> - **Select** (`form-select`): Bootstrap-styled dropdown; `selected disabled` on the first option creates a placeholder that can't be selected after choosing another option

---

## 4. Bootstrap Validation

```html
<form class="needs-validation" novalidate>
    <div class="mb-3">
        <label for="vName" class="form-label">Name</label>
        <input type="text" class="form-control" id="vName" required>
        <div class="valid-feedback">Looks good!</div>
        <div class="invalid-feedback">Please enter your name.</div>
    </div>
    <div class="mb-3">
        <label for="vEmail" class="form-label">Email</label>
        <input type="email" class="form-control" id="vEmail" required>
        <div class="invalid-feedback">Please enter a valid email.</div>
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
</form>

<script>
// Bootstrap validation script
(function () {
    'use strict';
    const forms = document.querySelectorAll('.needs-validation');
    Array.from(forms).forEach(function (form) {
        form.addEventListener('submit', function (event) {
            if (!form.checkValidity()) {
                event.preventDefault();
                event.stopPropagation();
            }
            form.classList.add('was-validated');
        }, false);
    });
})();
</script>
```

> **Code Explanation:**
> - `needs-validation` — a custom class that Bootstrap's JS uses to identify forms for validation
> - `novalidate` — disables the browser's default validation popups so Bootstrap's styled validation messages appear instead
> - `required` — HTML5 attribute that makes the field mandatory
> - `valid-feedback` — green message shown when the input passes validation
> - `invalid-feedback` — red message shown when the input fails validation
> - The JavaScript at the bottom:
>   - Selects all forms with `needs-validation` class
>   - Adds a `submit` event listener to each form
>   - `checkValidity()` — built-in browser method that checks all required fields
>   - If invalid: `preventDefault()` stops the form from submitting; `stopPropagation()` prevents the event from bubbling up
>   - `was-validated` class is added to the form, which triggers Bootstrap to show the feedback messages

### Form Accessibility — Labels, ARIA, and Best Practices

Accessibility ensures that **all users**, including those using screen readers or keyboard navigation, can use your forms:

```html
<!-- GOOD: Label properly linked to input via for/id -->
<div class="mb-3">
    <label for="studentName" class="form-label">Student Name</label>
    <input type="text" class="form-control" id="studentName" 
           aria-describedby="nameHelp" required>
    <div id="nameHelp" class="form-text">Enter your full name as per university records.</div>
</div>

<!-- GOOD: Hidden label for search boxes (visually hidden but screen reader readable) -->
<label for="searchBox" class="visually-hidden">Search courses</label>
<input type="search" class="form-control" id="searchBox" placeholder="Search courses...">

<!-- GOOD: ARIA attributes for custom validation messages -->
<input type="email" class="form-control" id="stuEmail" required
       aria-required="true" aria-invalid="false">
```

> **Code Explanation:**
> - `for="studentName"` + `id="studentName"` — **always link labels to inputs** — this is the most important accessibility rule for forms
> - `aria-describedby="nameHelp"` — links the input to help text; screen readers read the help text when the input is focused
> - `form-text` — Bootstrap's class for help text below an input (gray, small text)
> - `visually-hidden` — Bootstrap class that hides the label **visually** but keeps it readable for screen readers (use this when a placeholder serves as the visible label)
> - `aria-required="true"` — explicitly tells screen readers the field is required
> - `aria-invalid="false"` — tells screen readers whether the current value is invalid (update this with JavaScript during validation)

### Input Groups — Prepend/Append Icons or Text

Input groups let you attach text, icons, or buttons to the beginning or end of an input field:

```html
<!-- Rupee symbol before price input -->
<div class="input-group mb-3">
    <span class="input-group-text">₹</span>         <!-- Prepended text -->
    <input type="number" class="form-control" placeholder="Course fee" aria-label="Amount in rupees">
</div>

<!-- Email input with @ domain appended -->
<div class="input-group mb-3">
    <input type="text" class="form-control" placeholder="username">
    <span class="input-group-text">@mfrims.ac.in</span>  <!-- Appended text -->
</div>

<!-- Phone number with country code -->
<div class="input-group mb-3">
    <span class="input-group-text">+91</span>        <!-- Indian country code -->
    <input type="tel" class="form-control" placeholder="9876543210" pattern="\d{10}">
</div>

<!-- Search input with button -->
<div class="input-group mb-3">
    <input type="search" class="form-control" placeholder="Search students...">
    <button class="btn btn-primary" type="button">🔍 Search</button>  <!-- Appended button -->
</div>
```

> **Code Explanation:**
> - `input-group` — wraps the input and its addons together as a single visual unit
> - `input-group-text` — styled container for text/icons that attach to the input (gray background by default)
> - The ₹ symbol is prepended (appears before the input) — useful for currency fields
> - `@mfrims.ac.in` is appended (appears after the input) — useful for email domain auto-fill
> - Buttons can also be appended/prepended using `btn` class inside the input group
> - `aria-label` — provides an accessible name when there's no visible label

### Form State Management — Disabled and Readonly Fields

```html
<!-- Disabled input: grayed out, cannot be clicked or edited, NOT submitted with form -->
<div class="mb-3">
    <label for="rollNo" class="form-label">Roll Number</label>
    <input type="text" class="form-control" id="rollNo" value="25BCA042" disabled>
</div>

<!-- Readonly input: visible and submitted, but user cannot edit it -->
<div class="mb-3">
    <label for="semester" class="form-label">Semester</label>
    <input type="text" class="form-control" id="semester" value="II" readonly>
</div>

<!-- Readonly plain text: looks like normal text, no input border -->
<div class="mb-3">
    <label for="university" class="form-label">University</label>
    <input type="text" class="form-control-plaintext" id="university" 
           value="Mandsaur University" readonly>
</div>
```

> **Code Explanation:**
> - `disabled` — makes the field grayed out and **unclickable**; the value is **NOT sent** when the form is submitted (use for fields that don't apply)
> - `readonly` — the field looks normal and its value **IS sent** on submit, but the user cannot change it (use for auto-filled data like roll number)
> - `form-control-plaintext` — removes the input border/background so it looks like regular text, but is still a form field (useful for displaying data in a form context)

---

## Practical Session

### 🧪 Lab Experiments 26 & 27: Bootstrap Registration & Contact Forms

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootstrap Forms</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-light">

    <div class="container my-5">
        <div class="row g-4">
            
            <!-- Registration Form -->
            <div class="col-lg-6">
                <div class="card shadow">
                    <div class="card-header bg-primary text-white">
                        <h4 class="mb-0">Student Registration</h4>
                    </div>
                    <div class="card-body">
                        <form class="needs-validation" novalidate id="regForm">
                            
                            <div class="form-floating mb-3">
                                <input type="text" class="form-control" id="regName" 
                                       placeholder="Full Name" required minlength="2">
                                <label for="regName">Full Name</label>
                                <div class="invalid-feedback">Name required (min 2 chars)</div>
                            </div>

                            <div class="form-floating mb-3">
                                <input type="email" class="form-control" id="regEmail" 
                                       placeholder="Email" required>
                                <label for="regEmail">Email Address</label>
                                <div class="invalid-feedback">Valid email required</div>
                            </div>

                            <div class="form-floating mb-3">
                                <input type="tel" class="form-control" id="regPhone" 
                                       placeholder="Phone" required pattern="\d{10}">
                                <label for="regPhone">Phone Number</label>
                                <div class="invalid-feedback">10-digit number required</div>
                            </div>

                            <div class="form-floating mb-3">
                                <input type="password" class="form-control" id="regPwd" 
                                       placeholder="Password" required minlength="8">
                                <label for="regPwd">Password</label>
                                <div class="invalid-feedback">Min 8 characters</div>
                            </div>

                            <div class="mb-3">
                                <label class="form-label fw-bold">Gender</label>
                                <div>
                                    <div class="form-check form-check-inline">
                                        <input class="form-check-input" type="radio" name="gender" 
                                               id="gMale" value="male" required>
                                        <label class="form-check-label" for="gMale">Male</label>
                                    </div>
                                    <div class="form-check form-check-inline">
                                        <input class="form-check-input" type="radio" name="gender" 
                                               id="gFemale" value="female">
                                        <label class="form-check-label" for="gFemale">Female</label>
                                    </div>
                                    <div class="form-check form-check-inline">
                                        <input class="form-check-input" type="radio" name="gender" 
                                               id="gOther" value="other">
                                        <label class="form-check-label" for="gOther">Other</label>
                                    </div>
                                </div>
                            </div>

                            <div class="mb-3">
                                <label for="regCourse" class="form-label fw-bold">Course</label>
                                <select class="form-select" id="regCourse" required>
                                    <option value="" selected disabled>Select course...</option>
                                    <option>BCA</option>
                                    <option>BBA</option>
                                    <option>B.Tech</option>
                                </select>
                                <div class="invalid-feedback">Please select a course</div>
                            </div>

                            <div class="mb-3">
                                <label class="form-label fw-bold">Interests</label>
                                <div class="form-check">
                                    <input class="form-check-input" type="checkbox" id="iWeb">
                                    <label class="form-check-label" for="iWeb">Web Development</label>
                                </div>
                                <div class="form-check">
                                    <input class="form-check-input" type="checkbox" id="iApp">
                                    <label class="form-check-label" for="iApp">App Development</label>
                                </div>
                                <div class="form-check">
                                    <input class="form-check-input" type="checkbox" id="iAI">
                                    <label class="form-check-label" for="iAI">AI/ML</label>
                                </div>
                            </div>

                            <div class="form-check mb-3">
                                <input class="form-check-input" type="checkbox" id="terms" required>
                                <label class="form-check-label" for="terms">
                                    I agree to the terms and conditions
                                </label>
                                <div class="invalid-feedback">You must agree</div>
                            </div>

                            <button type="submit" class="btn btn-primary w-100 btn-lg">Register</button>
                        </form>
                    </div>
                </div>
            </div>

            <!-- Contact Form -->
            <div class="col-lg-6">
                <div class="card shadow">
                    <div class="card-header bg-success text-white">
                        <h4 class="mb-0">Contact Us</h4>
                    </div>
                    <div class="card-body">
                        <form class="needs-validation" novalidate id="contactForm">
                            
                            <div class="row mb-3">
                                <div class="col-md-6">
                                    <div class="form-floating">
                                        <input type="text" class="form-control" id="cFirst" 
                                               placeholder="First" required>
                                        <label for="cFirst">First Name</label>
                                    </div>
                                </div>
                                <div class="col-md-6 mt-3 mt-md-0">
                                    <div class="form-floating">
                                        <input type="text" class="form-control" id="cLast" 
                                               placeholder="Last" required>
                                        <label for="cLast">Last Name</label>
                                    </div>
                                </div>
                            </div>

                            <div class="form-floating mb-3">
                                <input type="email" class="form-control" id="cEmail" 
                                       placeholder="Email" required>
                                <label for="cEmail">Email</label>
                                <div class="invalid-feedback">Valid email required</div>
                            </div>

                            <div class="mb-3">
                                <label for="cSubject" class="form-label fw-bold">Subject</label>
                                <select class="form-select" id="cSubject" required>
                                    <option value="" selected disabled>Choose subject...</option>
                                    <option>General Inquiry</option>
                                    <option>Admission</option>
                                    <option>Fee Related</option>
                                    <option>Technical Issue</option>
                                </select>
                            </div>

                            <div class="form-floating mb-3">
                                <textarea class="form-control" id="cMessage" 
                                          placeholder="Message" style="height: 120px" required></textarea>
                                <label for="cMessage">Your Message</label>
                                <div class="invalid-feedback">Please enter a message</div>
                            </div>

                            <div class="form-check form-switch mb-3">
                                <input class="form-check-input" type="checkbox" id="cCopy">
                                <label class="form-check-label" for="cCopy">Send me a copy</label>
                            </div>

                            <button type="submit" class="btn btn-success w-100 btn-lg">Send Message</button>
                        </form>
                    </div>
                </div>

                <!-- Alert placeholder -->
                <div class="alert alert-success mt-3 d-none" id="successAlert">
                    ✅ Message sent successfully!
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // Bootstrap validation
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
> - **Two-column layout**: `col-lg-6` places the registration and contact forms side by side on large screens; they stack on mobile
> - **Registration Form**:
>   - `form-floating` — floating labels that animate upward when the user clicks/types
>   - `required minlength="2"` — name must have at least 2 characters
>   - `pattern="\d{10}"` — phone number must be exactly 10 digits (Indian mobile number format)
>   - `minlength="8"` — password requires at least 8 characters
>   - `form-check-inline` — places radio buttons side by side (Male, Female, Other) instead of stacking
>   - `form-select` with `required` — dropdown for course selection; first option is `disabled` so user must pick one
>   - `form-check form-switch` for newsletter — toggle switch style
>   - `btn-primary w-100 btn-lg` — full-width large blue button
> - **Contact Form**:
>   - `row` with `col-md-6` — places first name and last name side by side on tablets+
>   - `mt-3 mt-md-0` — adds top margin on mobile (since fields stack) but removes it on tablets (where they're side by side)
>   - `style="height: 120px"` on textarea — sets a fixed height for the message area
>   - `form-check form-switch` — "Send me a copy" toggle
> - **JavaScript validation**:
>   - Selects all `needs-validation` forms and adds submit event listeners
>   - `checkValidity()` — browser checks all constraints (required, minlength, pattern, etc.)
>   - If valid: shows alert and resets the form; `classList.remove('was-validated')` clears validation styling
>   - If invalid: adds `was-validated` class, which triggers Bootstrap to show red borders and error messages
>   - `event.preventDefault()` — prevents the form from actually submitting to a server (since we don't have a backend)

---

| Component | Key Classes |
|-----------|------------|
| Input | `form-control`, `form-control-lg` |
| Label | `form-label`, `col-form-label` |
| Select | `form-select` |
| Checkbox/Radio | `form-check`, `form-check-input` |
| Switch | `form-check form-switch` |
| Floating label | `form-floating` |
| Validation | `needs-validation`, `was-validated`, `valid-feedback`, `invalid-feedback` |

---

*Day 35 of 55 | Unit 6 — Bootstrap | Web Technology (25BCA060)*
