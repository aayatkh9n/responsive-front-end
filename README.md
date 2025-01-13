# Single-File Responsive Webpage

A responsive web application built with HTML, CSS, and JavaScript combined in a single file. Features dynamic scaling and a responsive layout that adapts to different screen sizes.

## Features

- All code (HTML, CSS, and JavaScript) in a single file for easy deployment
- Fixed navigation bar that stays at the top while scrolling
- Collapsible left sidebar menu with toggle button
- Three-column responsive layout
- Dynamic page scaling based on viewport width
- Mobile-friendly design
- Footer with proper positioning

## Project Structure

```
responsive-webpage/
│
└── index.html    # Contains all HTML, CSS, and JavaScript
```

## Getting Started

### Prerequisites

- Any modern web browser (Chrome, Firefox, Safari, or Edge)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/responsive-webpage.git
```

2. Open the project:
```bash
cd responsive-webpage
```

3. Run the application:
   - Simply double-click `index.html`
   - Or drag and drop `index.html` into your preferred web browser

### Alternative: Quick Start

1. Create a new file named `index.html`
2. Copy the entire code into this file
3. Save and open with your web browser

## Viewport Scaling

The webpage automatically scales based on the following screen widths:

| Screen Width (pixels) | Page Scale |
|----------------------|------------|
| 992 - 1600          | 90%        |
| 700 - 767           | 80%        |
| 600 - 700           | 75%        |
| ≤ 600               | 50%        |

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers

## Modifying the Code

The file structure within `index.html` is organized as follows:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Layout</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* Navbar */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background-color: #333;
            color: white;
            padding: 1rem;
            z-index: 1000;
        }

        /* Main container */
        .container {
            display: flex;
            margin-top: 60px;
            flex: 1;
            min-height: calc(100vh - 120px);
        }

        /* Left menu */
        .left-menu {
            width: 250px;
            background-color: #f0f0f0;
            padding: 1rem;
            transition: transform 0.3s ease;
        }

        .left-menu.collapsed {
            transform: translateX(-250px);
        }

        .toggle-menu {
            position: fixed;
            left: 10px;
            top: 70px;
            z-index: 100;
            padding: 0.5rem;
            background-color: #333;
            color: white;
            border: none;
            cursor: pointer;
        }

        /* Main content */
        .main-content {
            flex: 1;
            padding: 1rem;
            background-color: #fff;
        }

        /* Right panel */
        .right-panel {
            width: 200px;
            background-color: #f0f0f0;
            padding: 1rem;
        }

        /* Footer */
        .footer {
            background-color: #333;
            color: white;
            padding: 1rem;
            text-align: center;
        }

        /* Responsive design */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
            }

            .left-menu {
                width: 100%;
                transform: translateY(-100%);
            }

            .left-menu.collapsed {
                transform: translateY(-100%);
            }

            .right-panel {
                width: 100%;
            }

            .toggle-menu {
                top: auto;
                bottom: 20px;
                left: 20px;
            }
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <h1>My Website</h1>
    </nav>

    <button class="toggle-menu" onclick="toggleMenu()">☰</button>

    <div class="container">
        <aside class="left-menu">
            <h2>Left Menu</h2>
            <ul>
                <li>Menu Item 1</li>
                <li>Menu Item 2</li>
                <li>Menu Item 3</li>
            </ul>
        </aside>

        <main class="main-content">
            <h2>Main Content</h2>
            <p>This is the main content area of the website.</p>
        </main>

        <aside class="right-panel">
            <h2>Right Panel</h2>
            <p>Additional information goes here.</p>
        </aside>
    </div>

    <footer class="footer">
        <p>&copy; 2025 My Website. All rights reserved.</p>
    </footer>

    <script>
        // Toggle menu function
        function toggleMenu() {
            const leftMenu = document.querySelector('.left-menu');
            leftMenu.classList.toggle('collapsed');
        }

        // Screen width based scaling
        function adjustPageScale() {
            const width = window.innerWidth;
            let scale = 1;

            if (width >= 992 && width <= 1600) {
                scale = 0.9;
            } else if (width >= 700 && width <= 767) {
                scale = 0.8;
            } else if (width >= 600 && width < 700) {
                scale = 0.75;
            } else if (width <= 600) {
                scale = 0.5;
            }

            document.body.style.transform = `scale(${scale})`;
            document.body.style.transformOrigin = 'top left';
            // Adjust container height to account for scaling
            document.body.style.height = `${100 / scale}vh`;
        }

        // Listen for window resize
        window.addEventListener('resize', adjustPageScale);
        // Initial call
        adjustPageScale();
    </script>
</body>
</html>
```

To modify:
1. Edit CSS: Find the `<style>` section in the head
2. Edit HTML: Update the content in the `<body>` section
3. Edit JavaScript: Locate the `<script>` section at the bottom

## License

This project is licensed under the MIT License.
