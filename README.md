## Author / Team

**Course:** CSS445-Web Programming 
**Project:** IIIT Vadodara Event Board  
**Assignment:** Lab 5 — Design System, Box Model, CSS Grid & Responsive Design


**Team Leader:**

1. Roll No. :- 20261651058
    Name: Payal Verma

**Team Members:**

2. Roll No.:-20261651060
    Name: Piyush Jain

3. Roll No.:- 20261651066
   Name: Prince Vijay




# IIIT Vadodara Event Board

A responsive **Campus Event Board** website created for **CSS Lab Assignment 5**. The project demonstrates semantic HTML, a reusable CSS design system, the CSS box model, CSS Grid, responsive layouts, mobile-first design, accessibility, and responsive navigation.

## Project Overview

The website provides a single place to discover and register for campus activities at IIIT Vadodara. It includes:

- Responsive navigation with a mobile hamburger button
- Hero section with campus imagery
- Event Board statistics
- Featured event cards
- About section
- Event schedule
- Event registration form
- Contact section
- Responsive footer
- Accessibility features such as semantic structure, labels, focus styles, and a skip link

## Technologies Used

- HTML5
- CSS3
- CSS Custom Properties (`:root` variables)
- CSS Grid
- Flexbox
- Responsive Media Queries
- `rem`, `calc()`, and `clamp()`
- Responsive images with `max-width: 100%`
- Semantic HTML
- Google Fonts: Inter and Space Grotesk

## Project Files

```text
event-board/
├── index.html
├── style.css
├── base.css
├── dark_theme.css
├── group names and screenshot of pages.pdf
├── NOTES.md
├── README.md
└── images/
    ├── iiitv_logo.png
    └── image.jpeg
```

### Main Files

- **`index.html`** — Semantic page structure and campus event content.
- **`style.css`** — Lab 5 design system, box model, CSS Grid, responsive layout, and selector practice.
- **`base.css`** — Supporting styles for registration, contact, footer, accessibility, and additional responsive behaviour.
- **`dark_theme.css`** — Dark-theme/supporting theme styles used by the page.
- **`NOTES.md`** — Answers to the Lab 5 assignment questions and the final code appendix.
- **`README.md`** — Project documentation.

The HTML loads the CSS files in this order:

```html
<link rel="stylesheet" href="dark_theme.css">
<link rel="stylesheet" href="base.css">
<link rel="stylesheet" href="style.css">
```

## Design System

The project uses CSS custom properties to keep colours, typography, spacing, borders, and other design values consistent.

Examples from `style.css` include:

```css
:root {
    --brand-dark: #081b62;
    --brand: #2563eb;
    --accent: hsl(24 95% 53%);
    --overlay: rgb(0 0 0 / 40%);
    --ink: #172033;
    --surface: #ffffff;
    --line: #dfe5f0;
}
```

The stylesheet also uses relative units such as `rem`, fluid sizing with `clamp()`, and `calc()` for responsive spacing.

## Responsive Design

The project follows a mobile-first approach.

The base layout starts with a single-column page structure:

```css
.site-shell {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-areas:
        "header"
        "main"
        "footer";
}
```

As the viewport becomes wider, media queries add columns and adjust the layout. The project also uses responsive images:

```css
img {
    max-width: 100%;
    height: auto;
}
```

The navigation hides the full link row on smaller screens and reveals it on wider screens.

## CSS Grid

CSS Grid is used for:

- Overall page regions
- Event cards
- Statistics
- Registration layout
- Contact layout
- Responsive sections

The event and content layouts reflow as the viewport changes.

## Accessibility

The project includes several accessibility-focused features:

- Semantic HTML5 elements
- Descriptive image `alt` text
- Navigation `aria-label`
- Accessible menu button markup
- Skip-to-main-content link
- Visible `:focus-visible` styles
- Form labels
- Responsive and readable typography

## Events Included

The current event board includes example events such as:

- **Code & Create** — Technical event
- **Kreiva Campus Evening** — Cultural event
- **AI & Innovation Workshop** — Workshop

The page also provides event dates, locations, times, and registration links.

## How to Run

### Option 1 — VS Code Live Server

1. Open the project folder in Visual Studio Code.
2. Install/use the **Live Server** extension.
3. Right-click `index.html`.
4. Select **Open with Live Server**.

### Option 2 — Browser

Open `index.html` directly in a modern web browser.

## Responsive Testing

Test the page at different viewport sizes using browser DevTools:

- Narrow/mobile width
- Tablet width
- Wide/desktop width

Verify that:

- Navigation changes appropriately.
- Event cards reflow.
- Images remain within their containers.
- Typography scales correctly.
- Registration and contact sections adapt to available space.

## Assignment Requirements Covered

This project is prepared for the Lab 5 requirements covering:

- Design-system variables
- HEX, RGB, and HSL colours
- Semi-transparent colours
- `rem`, `calc()`, and `clamp()`
- `box-sizing: border-box`
- CSS box model
- CSS Grid and `grid-template-areas`
- Responsive card layouts
- Mobile-first CSS
- `min-width` responsive breakpoints
- Responsive navigation
- Responsive images and typography
- Accessibility and selector practice

The assignment requires a public GitHub repository named **`event-board`**, along with the final HTML/CSS code appendix in `NOTES.pdf`.

## GitHub Repository

Repository name:
event-board

Repository URL:
https://github.com/jannatverma/event-board

If GitHub Pages is enabled:
https://jannatverma.github.io/event-board/
## Submission Notes

Before submission, verify that the repository contains:

- `index.html`
- `style.css`
- `base.css`
- `dark_theme.css`
- Required images/assets
- `README.md`
- `NOTES.md`

Also verify that the required screenshots and final `NOTES.pdf` are included in the submission package as required by the assignment.

