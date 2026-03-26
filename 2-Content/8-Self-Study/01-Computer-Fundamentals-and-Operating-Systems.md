# Computer Fundamentals and Operating Systems

> **Self-Study Prerequisite** | Estimated Time: 2–3 Hours | No Prior Knowledge Required

---

## Learning Objectives

By the end of this self-study module, you should be able to:

- Identify the basic components of a computer (hardware and software)
- Understand what an operating system does and name the popular ones
- Navigate the file system — create, rename, move, and delete files and folders
- Understand file extensions and their importance in web development

---

## 1. What Is a Computer?

A **computer** is an electronic device that takes input, processes it, and produces output.

### Real-World Analogy

Think of a computer like a **kitchen**:
- **Input** = Raw ingredients (vegetables, spices) → Keyboard, mouse, microphone
- **Processing** = The cooking process → CPU (the brain of the computer)
- **Output** = The final dish → Monitor (screen), speakers, printer
- **Storage** = The refrigerator to keep ingredients for later → Hard disk, SSD

### Types of Computers

| Type | Example | Usage |
|------|---------|-------|
| **Desktop** | Dell OptiPlex, HP ProDesk | Office, lab, home |
| **Laptop** | Dell Inspiron, HP Pavilion, Lenovo IdeaPad | Portable use |
| **Tablet** | iPad, Samsung Galaxy Tab | Touch-based, light tasks |
| **Smartphone** | Samsung Galaxy, iPhone, Redmi | Daily communication, apps |
| **Server** | Dell PowerEdge, HP ProLiant | Hosting websites and services |

---

## 2. Hardware vs Software

### Hardware — The Physical Parts

These are the parts you can **touch and see**:

| Component | What It Does | Analogy |
|-----------|-------------|---------|
| **CPU** (Processor) | Performs calculations and logic | The **brain** |
| **RAM** (Memory) | Temporary storage for running programs | Your **work desk** — bigger desk = more space to work |
| **Hard Disk / SSD** | Permanent storage for files | A **cupboard** to store things permanently |
| **Monitor** | Displays output | The **TV screen** |
| **Keyboard** | Text input | A **typewriter** |
| **Mouse** | Pointing and clicking | Your **hand** pointing at things |
| **Motherboard** | Connects everything together | The **skeleton** of the computer |

### Software — The Programs

These are the **instructions** that tell the hardware what to do:

| Type | Examples | Purpose |
|------|---------|---------|
| **System Software** | Windows 11, macOS, Ubuntu Linux | Manages the hardware |
| **Application Software** | Chrome, VS Code, MS Word | Performs specific tasks |
| **Utility Software** | Antivirus, Disk Cleanup, WinRAR | Maintenance tasks |

---

## 3. What Is an Operating System (OS)?

An **Operating System** is the most important software on a computer. It is like a **manager** that:

- Controls all the hardware (screen, keyboard, mouse)
- Lets you run applications (Chrome, VS Code, etc.)
- Manages files and folders
- Handles memory and processing power
- Provides security (passwords, user accounts)

### Popular Operating Systems

| OS | Developer | Used On | Logo Description |
|----|-----------|---------|-----------------|
| **Windows 11** | Microsoft | Most desktops/laptops | Blue window icon |
| **macOS** | Apple | MacBook, iMac | Apple logo |
| **Ubuntu / Linux** | Community / Canonical | Servers, developers | Orange circle with dots |
| **Android** | Google | Smartphones | Green robot |
| **iOS** | Apple | iPhones, iPads | Apple logo |

### Your Lab Computers

In your university lab, you most likely use **Windows 10** or **Windows 11**. All exercises in this course are designed to work on Windows.

---

## 4. The File System — Files and Folders

The way a computer organizes your data is called a **File System**.

### Real-World Analogy

Think of it like a **library**:
- The **library building** = Your hard disk (C: drive)
- **Sections** (Science, History, Fiction) = Folders
- **Shelves** inside sections = Sub-folders
- **Books** on shelves = Files

### Understanding File Paths

A **file path** is the exact address of a file on your computer.

```
C:\Users\Student\Desktop\my-webpage\index.html
```

Breaking it down:

| Part | Meaning |
|------|---------|
| `C:\` | The main drive (like the library building) |
| `Users\Student\` | Inside the "Users" folder, then the "Student" folder |
| `Desktop\` | Inside the Desktop folder |
| `my-webpage\` | A project folder you created |
| `index.html` | The actual file |

### The Backslash `\` vs Forward Slash `/`

- **Windows** uses backslash: `C:\Users\Student\Desktop\`
- **Web URLs** use forward slash: `https://example.com/about/contact.html`
- **In HTML/CSS code**, always use forward slash `/`

---

## 5. File Extensions — What Do They Mean?

A **file extension** is the part after the dot (`.`) in a filename. It tells the computer what type of file it is.

### Extensions You Will Use in This Course

| Extension | Type | Opens With | Usage in Course |
|-----------|------|-----------|----------------|
| `.html` | Web page | Browser (Chrome) | Every day — your main web files |
| `.css` | Stylesheet | Text editor | Styling web pages (Unit 4 onwards) |
| `.js` | JavaScript | Text editor / Browser | Adding interactivity (Unit 5 onwards) |
| `.md` | Markdown | Text editor / GitHub | Course notes, README files |
| `.txt` | Plain text | Notepad | Simple notes |
| `.jpg`, `.png`, `.gif` | Image | Photo viewer | Images in web pages |
| `.mp4`, `.mp3` | Audio/Video | Media player | Multimedia in web pages |

### How to See File Extensions on Windows

By default, Windows **hides** file extensions. You should enable them:

1. Open **File Explorer** (press `Win + E`)
2. Click the **View** tab at the top
3. Check the box that says **"File name extensions"**

Now you will see `index.html` instead of just `index`.

---

## 6. Basic Computer Operations for Web Development

### Creating a New Folder

1. Open **File Explorer** → Navigate to your desired location (e.g., Desktop)
2. **Right-click** on empty space → Select **"New" → "Folder"**
3. Type the folder name (e.g., `my-first-website`) and press **Enter**

**Naming Rules for Web Projects:**
- Use **lowercase** letters: `my-project` (not `My Project`)
- Use **hyphens** instead of spaces: `web-technology-lab` (not `web technology lab`)
- Avoid special characters like `@`, `#`, `&`, `!`

### Creating Files

1. Open **Notepad** (press `Win`, type "Notepad", press Enter)
2. Type your content
3. Go to **File → Save As**
4. Change "Save as type" to **"All Files (*.*)"**
5. Type filename with extension: `index.html`
6. Click **Save**

### Copy, Move, Rename, Delete

| Action | Shortcut | Steps |
|--------|----------|-------|
| **Copy** | `Ctrl + C` | Select file → Right-click → Copy |
| **Paste** | `Ctrl + V` | Go to destination → Right-click → Paste |
| **Cut (Move)** | `Ctrl + X` | Select file → Right-click → Cut → Paste elsewhere |
| **Rename** | `F2` | Select file → Press F2 → Type new name → Enter |
| **Delete** | `Delete` | Select file → Press Delete → Confirm |
| **Undo** | `Ctrl + Z` | Undo last action (works most of the time) |

---

## 7. Text Editors — Where You Write Code

A **text editor** is a program where you write your HTML, CSS, and JavaScript code.

### Notepad vs Code Editor

| Feature | Notepad | VS Code |
|---------|---------|---------|
| Syntax highlighting | ❌ No | ✅ Yes (colors your code) |
| Auto-complete | ❌ No | ✅ Yes |
| Error detection | ❌ No | ✅ Yes |
| Multiple files | One at a time | Multiple tabs |
| Free? | ✅ Yes | ✅ Yes |

### Recommended: Visual Studio Code (VS Code)

**VS Code** is the code editor we will use throughout this course. It is:
- **Free** and open-source
- Made by **Microsoft**
- The **most popular** code editor in the world
- Available on Windows, macOS, and Linux

**How to Install VS Code:**
1. Go to `https://code.visualstudio.com/`
2. Click the big **"Download for Windows"** button
3. Run the downloaded file (`VSCodeSetup-x64-X.XX.X.exe`)
4. Click **Next** → **Next** → Check **"Add to PATH"** → **Install** → **Finish**
5. Open VS Code from Start Menu

---

## 8. Keyboard Shortcuts Every Student Should Know

These shortcuts work in almost every program on Windows:

| Shortcut | Action |
|----------|--------|
| `Ctrl + S` | **Save** current file (USE THIS CONSTANTLY!) |
| `Ctrl + Z` | **Undo** last action |
| `Ctrl + Y` | **Redo** (undo the undo) |
| `Ctrl + C` | **Copy** selected text |
| `Ctrl + V` | **Paste** copied text |
| `Ctrl + X` | **Cut** selected text |
| `Ctrl + A` | **Select All** text |
| `Ctrl + F` | **Find** text in a document |
| `Alt + Tab` | **Switch** between open programs |
| `Win + E` | Open **File Explorer** |
| `F5` | **Refresh** (in browser) |
| `F12` | Open **Developer Tools** (in browser) |

---

## 9. Understanding Storage Units

| Unit | Size | Real-World Example |
|------|------|-------------------|
| **1 Byte (B)** | 1 character | The letter "A" |
| **1 Kilobyte (KB)** | ~1,000 bytes | A short text file |
| **1 Megabyte (MB)** | ~1,000 KB | A photo from your phone |
| **1 Gigabyte (GB)** | ~1,000 MB | A movie in HD |
| **1 Terabyte (TB)** | ~1,000 GB | A full laptop hard disk |

### Typical File Sizes in Web Development

| File Type | Typical Size |
|-----------|-------------|
| HTML page | 5–50 KB |
| CSS file | 2–20 KB |
| JavaScript file | 5–100 KB |
| Image (compressed) | 50–500 KB |
| Bootstrap CSS (from CDN) | ~160 KB |

---

## Self-Assessment Questions

1. What is the difference between hardware and software? Give two examples of each.
2. Name three functions of an operating system.
3. What is a file path? Write the file path for a file called `style.css` on your Desktop.
4. Why should you use hyphens instead of spaces in folder names for web projects?
5. What is the difference between Notepad and VS Code?
6. Which keyboard shortcut saves a file?
7. How many kilobytes are in a megabyte?

---

## Quick Summary

| Topic | Key Takeaway |
|-------|-------------|
| Computer | Input → Processing → Output device |
| Hardware | Physical parts (CPU, RAM, Monitor, Keyboard) |
| Software | Programs (OS, Applications, Utilities) |
| Operating System | Manager that controls everything (Windows, macOS, Linux) |
| File System | Organized hierarchy of drives → folders → files |
| File Extensions | `.html`, `.css`, `.js` are the main ones for this course |
| Text Editor | Use **VS Code** for writing code |
| Shortcuts | `Ctrl + S` (Save) is your best friend |

---

*This is a self-study prerequisite for the Web Technology (25BCA060) course at Mandsaur University.*
