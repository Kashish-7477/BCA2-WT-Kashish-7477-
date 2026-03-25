# Day 28 — DOM Manipulation

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 5 — JavaScript
🧪 **Lab Experiments:** 19, 20

---

## Learning Objectives

By the end of this session, students will be able to:
- Explain the DOM (Document Object Model)
- Select and modify HTML elements using JavaScript
- Create, append, and remove elements dynamically
- Change styles and classes with JavaScript

---

## 1. What is the DOM?

> **Analogy:** The DOM is like a **family tree** of your HTML page. Each element is a node — `<html>` is the grandparent, `<body>` is the parent, and `<div>`, `<p>`, `<h1>` are children. JavaScript can walk through this tree and change any family member.

```
document
  └── html
       ├── head
       │    └── title
       └── body
            ├── h1
            ├── p
            └── div
                 ├── p
                 └── img
```

The browser reads your HTML and creates this tree structure in memory. JavaScript interacts with this in-memory tree — not the HTML file directly.

---

## 2. Selecting Elements

| Method | Returns | Use Case |
|--------|---------|----------|
| `getElementById('id')` | Single element | When element has unique ID |
| `querySelector('.class')` | First match | CSS selector — most versatile |
| `querySelectorAll('p')` | NodeList (all matches) | Multiple elements |
| `getElementsByClassName('cls')` | HTMLCollection | All with that class |
| `getElementsByTagName('p')` | HTMLCollection | All elements of that tag |

```javascript
// By ID
const header = document.getElementById('header');

// By CSS selector (first match)
const firstCard = document.querySelector('.card');

// All matches
const allCards = document.querySelectorAll('.card');
allCards.forEach(card => {
    console.log(card.textContent);
});
```

---

## 3. Modifying Elements

### Changing Content

```javascript
const title = document.getElementById('title');

title.textContent = 'New Title';          // Plain text (safe from XSS)
title.innerHTML = '<em>New Title</em>';   // Parses HTML (use carefully)
```

### Changing Attributes

```javascript
const img = document.querySelector('img');
img.setAttribute('src', 'new-photo.jpg');
img.setAttribute('alt', 'Updated photo');

const link = document.querySelector('a');
console.log(link.getAttribute('href'));
link.removeAttribute('target');
```

### Changing Styles

```javascript
const box = document.getElementById('box');
box.style.backgroundColor = '#1565C0';
box.style.color = 'white';
box.style.padding = '20px';
box.style.borderRadius = '10px';
```

### Changing Classes

```javascript
const el = document.getElementById('box');

el.classList.add('active');         // Add class
el.classList.remove('hidden');      // Remove class
el.classList.toggle('dark-mode');   // Toggle (add/remove)
el.classList.contains('active');    // Check: true/false
el.classList.replace('old', 'new'); // Replace class
```

---

## 4. Creating & Removing Elements

### Creating Elements

```javascript
// Create a new paragraph
const newP = document.createElement('p');
newP.textContent = 'This was added by JavaScript!';
newP.classList.add('highlight');

// Append to body
document.body.appendChild(newP);

// Insert before a specific element
const container = document.getElementById('container');
const firstChild = container.firstElementChild;
container.insertBefore(newP, firstChild);
```

### Removing Elements

```javascript
const oldElement = document.getElementById('remove-me');
oldElement.remove();
```

---

## Practical Session

### 🧪 Lab Experiment 19: DOM Manipulation

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM Manipulation</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Segoe UI', sans-serif; background: #f4f4f4; padding: 30px; }
        .container { max-width: 700px; margin: 0 auto; }
        h1 { color: #1565C0; text-align: center; margin-bottom: 25px; }
        
        .card { background: white; border-radius: 10px; padding: 25px;
                margin-bottom: 20px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        
        .btn { padding: 8px 20px; border: none; border-radius: 5px;
               cursor: pointer; color: white; font-size: 14px; margin: 3px; }
        .btn-blue { background: #1565C0; }
        .btn-green { background: #4CAF50; }
        .btn-red { background: #E91E63; }
        .btn-orange { background: #FF9800; }
        
        #targetBox {
            padding: 30px; text-align: center; font-size: 18px;
            border: 2px dashed #ccc; margin: 15px 0; border-radius: 10px;
            transition: all 0.3s ease;
        }
        
        .dark-mode { background: #333 !important; color: #0f0 !important; }
        
        #todoList { list-style: none; }
        #todoList li {
            padding: 10px; margin: 5px 0; background: #f9f9f9;
            border-radius: 5px; display: flex; justify-content: space-between;
            align-items: center;
        }
        #todoList li .delete-btn {
            background: #E91E63; color: white; border: none;
            padding: 4px 10px; border-radius: 3px; cursor: pointer;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>DOM Manipulation Lab</h1>

    <!-- 1. Modify Styles -->
    <div class="card">
        <h3>1. Change Element Styles</h3>
        <div id="targetBox">I'm a target box — click buttons to change me!</div>
        <button class="btn btn-blue" onclick="changeColor()">Change Color</button>
        <button class="btn btn-green" onclick="changeSize()">Change Size</button>
        <button class="btn btn-orange" onclick="toggleDark()">Toggle Dark Mode</button>
        <button class="btn btn-red" onclick="resetBox()">Reset</button>
    </div>

    <!-- 2. Dynamic Content -->
    <div class="card">
        <h3>2. Dynamic Content</h3>
        <p id="dynamicText">This text will change.</p>
        <button class="btn btn-blue" onclick="changeText()">Change Text</button>
        <button class="btn btn-green" onclick="addElement()">Add Paragraph</button>
    </div>

    <!-- 3. Mini Todo List -->
    <div class="card">
        <h3>3. Dynamic Todo List</h3>
        <div style="display:flex; gap:10px; margin-bottom:10px;">
            <input type="text" id="todoInput" placeholder="Enter a task..." 
                   style="flex:1; padding:10px; border:1px solid #ddd; border-radius:5px;">
            <button class="btn btn-green" onclick="addTodo()">Add</button>
        </div>
        <ul id="todoList"></ul>
    </div>
</div>

<script>
    const colors = ['#1565C0', '#E91E63', '#4CAF50', '#FF9800', '#9C27B0'];
    let colorIndex = 0;

    // 1. Style Manipulation
    function changeColor() {
        const box = document.getElementById('targetBox');
        colorIndex = (colorIndex + 1) % colors.length;
        box.style.backgroundColor = colors[colorIndex];
        box.style.color = 'white';
        box.textContent = `Color: ${colors[colorIndex]}`;
    }

    function changeSize() {
        const box = document.getElementById('targetBox');
        const currentSize = parseInt(box.style.fontSize) || 18;
        box.style.fontSize = (currentSize < 36 ? currentSize + 4 : 18) + 'px';
    }

    function toggleDark() {
        document.getElementById('targetBox').classList.toggle('dark-mode');
    }

    function resetBox() {
        const box = document.getElementById('targetBox');
        box.style = '';
        box.className = '';
        box.textContent = "I'm a target box — click buttons to change me!";
        colorIndex = 0;
    }

    // 2. Dynamic Content
    function changeText() {
        const el = document.getElementById('dynamicText');
        const messages = [
            'JavaScript is powerful! 💪',
            'DOM manipulation is easy! 🎯',
            'Keep learning! 📚',
            'You are doing great! ⭐'
        ];
        el.textContent = messages[Math.floor(Math.random() * messages.length)];
    }

    function addElement() {
        const p = document.createElement('p');
        p.textContent = `New paragraph added at ${new Date().toLocaleTimeString()}`;
        p.style.color = '#1565C0';
        p.style.padding = '5px';
        document.getElementById('dynamicText').parentElement.appendChild(p);
    }

    // 3. Todo List
    function addTodo() {
        const input = document.getElementById('todoInput');
        const text = input.value.trim();
        if (!text) return;

        const li = document.createElement('li');
        li.innerHTML = `<span>${text}</span>`;

        const deleteBtn = document.createElement('button');
        deleteBtn.textContent = '✕';
        deleteBtn.className = 'delete-btn';
        deleteBtn.addEventListener('click', function() {
            li.remove();
        });
        li.appendChild(deleteBtn);

        document.getElementById('todoList').appendChild(li);
        input.value = '';
        input.focus();
    }

    // Allow Enter key to add todo
    document.getElementById('todoInput').addEventListener('keydown', function(e) {
        if (e.key === 'Enter') addTodo();
    });
</script>

</body>
</html>
```

---

### 🧪 Lab Experiment 20: Dynamic Table Generation

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamic Table</title>
    <style>
        * { box-sizing: border-box; }
        body { font-family: 'Segoe UI', sans-serif; background: #f4f4f4; padding: 30px; }
        .container { max-width: 600px; margin: 0 auto; background: white;
                     border-radius: 10px; padding: 25px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        h1 { color: #1565C0; text-align: center; }
        input { padding: 10px; border: 1px solid #ddd; border-radius: 5px; width: 100%; margin: 5px 0; }
        button { padding: 10px 25px; background: #4CAF50; color: white;
                 border: none; border-radius: 5px; cursor: pointer; margin: 5px 0; }
        table { width: 100%; border-collapse: collapse; margin-top: 15px; }
        th { background: #1565C0; color: white; padding: 10px; }
        td { padding: 10px; border: 1px solid #ddd; text-align: center; }
        tr:nth-child(even) { background: #f9f9f9; }
    </style>
</head>
<body>

<div class="container">
    <h1>Student Records (Dynamic Table)</h1>
    
    <input type="text" id="sName" placeholder="Student Name">
    <input type="text" id="sRoll" placeholder="Roll Number">
    <input type="number" id="sMarks" placeholder="Marks" min="0" max="100">
    <button onclick="addStudent()">Add Student</button>

    <table id="studentTable">
        <thead>
            <tr><th>#</th><th>Name</th><th>Roll No</th><th>Marks</th><th>Grade</th></tr>
        </thead>
        <tbody id="tableBody"></tbody>
    </table>
</div>

<script>
    let count = 0;

    function getGrade(marks) {
        if (marks >= 90) return 'A+';
        if (marks >= 75) return 'A';
        if (marks >= 60) return 'B';
        if (marks >= 40) return 'C';
        return 'F';
    }

    function addStudent() {
        const name = document.getElementById('sName').value.trim();
        const roll = document.getElementById('sRoll').value.trim();
        const marks = parseInt(document.getElementById('sMarks').value);

        if (!name || !roll || isNaN(marks)) {
            alert('Please fill all fields!');
            return;
        }

        count++;
        const grade = getGrade(marks);
        const row = document.createElement('tr');
        row.innerHTML = `<td>${count}</td><td>${name}</td><td>${roll}</td><td>${marks}</td><td>${grade}</td>`;
        document.getElementById('tableBody').appendChild(row);

        // Clear inputs
        document.getElementById('sName').value = '';
        document.getElementById('sRoll').value = '';
        document.getElementById('sMarks').value = '';
        document.getElementById('sName').focus();
    }
</script>

</body>
</html>
```

---

## Summary

| Method | Purpose |
|--------|---------|
| `getElementById()` | Select by ID |
| `querySelector()` | Select by CSS selector |
| `textContent` / `innerHTML` | Change content |
| `style.property` | Change inline style |
| `classList.add/remove/toggle` | Change CSS classes |
| `createElement()` + `appendChild()` | Add new elements |
| `element.remove()` | Remove an element |

---

*Day 28 of 55 | Unit 5 — JavaScript | Web Technology (25BCA060)*
