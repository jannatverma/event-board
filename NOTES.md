# LAB 5 NOTES — IIIT Vadodara Event Board

## Assignment Answers

### 1. Show your `:root` palette. Why are named variables better than repeating hex codes?

The project uses the following named CSS custom properties:

```css
:root {
  --brand: ...;
  --brand-dark: ...;
  --accent: ...;
  --ink: ...;
  --muted: ...;
  --paper: ...;
  --surface: ...;
  --line: ...;
}
```

Named variables make the design consistent and allow the whole theme to be changed from one place instead of editing repeated colour values throughout the stylesheet. The final values should match the actual `:root` block in `style.css`.

### 2. Give one use each of HEX, `rgb()` and `hsl()` from your CSS, and say where you used a semi-transparent colour and why.

The required colour formats are:

- **HEX:** `--brand: #1238b8`
- **RGB:** `background: rgb(255 255 255 / 94%)`
- **HSL:** `background: hsl(27 80% 44%)`

A semi-transparent colour is used for the header/hero overlay so that the background image remains visible while the text stays readable.

> Note: These examples are taken from the existing notes. The final answer should be checked against the actual `style.css` before submission.

### 3. Why prefer `rem` over `px` for fonts and spacing? Show one `calc()` and one `clamp()` you used and what each does.

`rem` scales with the root font size and is useful for accessible, consistent spacing and typography.

Example:

```css
width: calc(100% - 2rem);
```

This creates a fluid width while leaving `2rem` of breathing room.

Example:

```css
font-size: clamp(2.4rem, 7vw, 5.5rem);
```

This creates a heading that grows with the viewport while staying within minimum and maximum limits.

### 4. A box has `width: 200px; padding: 20px; border: 5px`. What is its actual rendered width with `content-box`, and with `border-box`? Which did you use and why?

With **content-box**:

```text
200px + 20px + 20px + 5px + 5px = 250px
```

So the actual outer width is **250px**.

With **border-box**, the declared `width: 200px` includes the content, padding, and border, so the rendered outer width is **200px**.

This project uses:

```css
* {
  box-sizing: border-box;
}
```

This makes sizing more predictable because the declared width includes padding and borders.

### 5. Name the four layers of the box model, from the inside out.

The four layers are:

1. **Content**
2. **Padding**
3. **Border**
4. **Margin**

### 6. What does `repeat(auto-fit, minmax(15rem, 1fr))` do, and why does it need no media query?

```css
repeat(auto-fit, minmax(15rem, 1fr))
```

creates as many columns as can fit in the available space while preventing an event card from becoming narrower than `15rem`.

It automatically reflows from many columns to fewer columns as the window becomes narrower, so a separate media query is not required for the card grid itself.

### 7. Mobile-first: why write the phone styles as the base and add layout with `min-width` queries? And why is the viewport `<meta>` tag essential?

Phone styles are the base because the design starts with the smallest screen and progressively adds space and columns as the viewport grows. `min-width` media queries can then add the larger-screen layouts.

The viewport tag:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

is essential because it tells mobile browsers to use the device width. Without it, responsive CSS will not behave correctly on a phone.

### 8. Paste your `grid-template-areas` map. Which regions span more than one column, and how did you make them?

The page regions are arranged as:

```css
grid-template-areas:
  "header"
  "main"
  "footer";
```

The corresponding regions are assigned using `grid-area`.

The internal content also uses CSS Grid layouts for cards, statistics, registration, and contact sections.

**Important:** The assignment asks for the exact final `grid-template-areas` map and an explanation of regions spanning multiple columns. The uploaded `NOTES.md` only contains the one-column map above, so the final multi-column map should be copied from the completed `style.css` rather than invented here.

### 9. Name one responsive technique for images and one for type that need no media query.

**Images:**

```css
img {
  max-width: 100%;
  height: auto;
}
```

`object-fit: cover` can also be used for a uniform banner or thumbnail.

**Type:**

```css
font-size: clamp(...);
```

`clamp()` makes a type size fluid without requiring a media query.

### 10. Prepare a GitHub repo for `event-board` and paste your final `index.html` and final `style.css`.

The required repository should be a **public GitHub repository named `event-board`**.

It should contain:

- `index.html`
- `style.css`
- `base.css` / `theme-dark.css` if used
- `images/` if used
- `README.md`
- A readable commit history

GitHub Pages may optionally be enabled, with the live Pages link included in the submission.

**Repository link:** `[ADD FINAL GITHUB REPOSITORY LINK]`

**GitHub Pages link:** `[ADD FINAL GITHUB PAGES LINK IF ENABLED]`

The assignment also requires the final cumulative `index.html` and `style.css` to be included as a clearly labelled code appendix in the final `NOTES.pdf`.

> The uploaded materials do not contain the final `index.html`, `style.css`, repository URL, or Pages URL, so these cannot be filled in accurately without the completed project files/details.

---

## Lab 5 Concepts / Reference Notes

### 1. `:root` palette

- `--brand`, `--brand-dark`, `--accent`, `--ink`, `--muted`, `--paper`, `--surface`, and `--line`.
- Named variables make the design consistent and allow the whole theme to be changed from one place instead of editing repeated colour values.

### 2. Colour formats

- HEX: `--brand: #1238b8`.
- RGB: `background: rgb(255 255 255 / 94%)`.
- HSL: `background: hsl(27 80% 44%)`.
- Semi-transparent colours are used for the header/hero overlays so the background image remains visible while text stays readable.

### 3. `rem`, `calc()`, `clamp()`

- `rem` scales with the root font size and is useful for accessible, consistent spacing and typography.
- `calc(100% - 2rem)` creates a fluid width while leaving breathing room.
- `clamp(2.4rem, 7vw, 5.5rem)` creates a heading that grows with the viewport but stays within minimum and maximum limits.

### 4. Box model

- Content-box: `200px + 20px + 20px + 5px + 5px = 250px`.
- Border-box: declared `width: 200px` includes content + padding + border, so the rendered outer width is 200px.
- This project uses `box-sizing: border-box`.

### 5. Four box-model layers

- Content → Padding → Border → Margin.

### 6. `auto-fit` + `minmax`

- `repeat(auto-fit, minmax(15rem, 1fr))` creates as many columns as can fit, while preventing a card from becoming narrower than `15rem`. It reflows automatically, so the card grid does not need a media query.

### 7. Mobile-first + viewport

- Phone styles are the base because they work on small screens first; `min-width` queries progressively add space and columns.
- The viewport meta tag tells mobile browsers to use the device width so responsive CSS behaves correctly.

### 8. Grid areas

```text
"header"
"main"
"footer"
```

The main page regions are assigned with `grid-area`. The internal content uses additional CSS Grid layouts for cards, stats, registration and contact sections.

### 9. Responsive techniques without media queries

- Images: `max-width: 100%`, `height: auto`, and `object-fit: cover`.
- Type: `clamp()` for fluid heading sizes.

### 10. GitHub

- Create a public repository named `event-board`.
- Add `index.html`, `style.css`, `images/`, and this `NOTES.md`.
- Commit changes with meaningful messages and optionally enable GitHub Pages.

---

## Final Code Appendix

### `index.html`

**Paste the final cumulative `index.html` from the completed project here.**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>IIIT Vadodara Event Board | Campus Events</title>

    <meta name="description"
        content="IIIT Vadodara Campus Event Board — discover technical, cultural, academic and student activities.">

    <meta name="robots" content="index, follow">

    <meta property="og:title" content="IIIT Vadodara Event Board">

    <meta property="og:description"
        content="Discover technical, cultural, academic and student events at IIIT Vadodara.">

    <meta property="og:image" content="images/image.jpeg">

    <link rel="icon" href="images/iiitv_logo.png">

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

    <link
        href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Space+Grotesk:wght@500;600;700&display=swap"
        rel="stylesheet">

    <link rel="stylesheet" href="dark_theme.css">
    <link rel="stylesheet" href="base.css">
    <link rel="stylesheet" href="style.css">
</head>


<body>

    <!-- Accessibility: Skip directly to main content -->
    <a href="#main-content" class="skip-link">
        Skip to main content
    </a>


    <div class="site-shell">

        <!-- ================= HEADER ================= -->

        <header class="site-header">

            <a href="#home"
                class="brand"
                aria-label="IIIT Vadodara Event Board home">

                <img
                    src="images/iiitv_logo.png"
                    alt="IIIT Vadodara logo"
                    class="brand-logo">

                <span class="brand-text">
                    <strong>IIIT VADODARA</strong>
                    <small>Campus Event Board</small>
                </span>

            </a>


            <!-- Main navigation -->
            <nav
                class="nav-area"
                aria-label="Main navigation">

                <button
                    class="menu-toggle"
                    type="button"
                    aria-label="Open navigation menu"
                    aria-expanded="false">

                    <span></span>
                    <span></span>
                    <span></span>

                </button>


                <div class="nav-links">

                    <a href="#home">Home</a>

                    <a href="#events">Events</a>

                    <a href="#about">About</a>

                    <a href="#schedule">Schedule</a>

                    <a href="#contact">Contact</a>

                    <a
                        href="#registration"
                        class="nav-cta">
                        Register
                    </a>

                </div>

            </nav>

        </header>


        <!-- ================= MAIN ================= -->

        <main id="main-content" class="main-content">


            <!-- ================= HERO ================= -->

            <section
                class="hero"
                id="home"
                aria-labelledby="hero-title">

                <img
                    class="hero-image"
                    src="images/image.jpeg"
                    width="1200"
                    height="700"
                    alt="IIIT Vadodara campus">

                <div class="hero-overlay"></div>


                <div class="hero-content">

                    <p class="eyebrow">
                        -IIIT VADODARA • CAMPUS EVENT BOARD -
                    </p>


                    <h1 id="hero-title">

                        Welcome to
                        <span>IIIT Vadodara.</span>

                        <br>

                        Campus Event Board

                    </h1>


                    <p class="hero-text">

                        Explore the events, workshops, activities and
                        opportunities that bring the IIIT Vadodara
                        campus community together.

                    </p>


                    <div class="hero-actions">

                        <a
                            href="#events"
                            class="button button-primary">
                            Explore Events →
                        </a>

                        <a
                            href="#about"
                            class="button button-ghost">
                            About Board
                        </a>

                    </div>

                </div>


                <div class="hero-badge">

                    <strong>2013</strong>

                    <span>Established</span>

                </div>

            </section>


            <!-- ================= STATISTICS ================= -->

            <section
                class="stats"
                aria-labelledby="stats-title">

                <h2
                    id="stats-title"
                    class="visually-hidden">
                    Event Board Highlights
                </h2>


                <div class="stat-item">

                    <strong>06+</strong>

                    <span>Event Categories</span>

                </div>


                <div class="stat-item">

                    <strong>03</strong>

                    <span>Featured Events</span>

                </div>


                <div class="stat-item">

                    <strong>24/7</strong>

                    <span>Online Event Board</span>

                </div>


                <div class="stat-item">

                    <strong>IIITV</strong>

                    <span>Student Community</span>

                </div>

            </section>


            <!-- ================= EVENTS ================= -->

            <section
                id="events"
                class="section"
                aria-labelledby="events-title">


                <div class="section-heading">

                    <div>

                        <p class="eyebrow accent-text">
                            WHAT'S HAPPENING
                        </p>

                        <h2 id="events-title">
                            Featured Events
                        </h2>

                    </div>


                    <p>

                        Find an event that matches your interests and

                        <mark>
                            register before the seats fill
                        </mark>.

                    </p>

                </div>


                <div class="event-grid">


                    <!-- EVENT 1 -->

                    <article class="event-card">

                        <figure class="event-image-wrap">

                            <img
                                src="https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?auto=format&fit=crop&w=1000&q=85"
                                alt="Students collaborating during a programming event"
                                width="1000"
                                height="700"
                                loading="lazy">


                            <span class="event-tag">
                                TECH
                            </span>


                            <figcaption>
                                Students collaborating during a programming event
                            </figcaption>

                        </figure>


                        <div class="event-card-body">

                            <p class="event-date">

                                <time datetime="2026-09-25">
                                    25 SEP 2026
                                </time>

                            </p>


                            <h3>
                                Code &amp; Create
                            </h3>


                            <p>

                                Build practical solutions, collaborate
                                with peers and turn ideas into working
                                prototypes.

                            </p>


                            <div class="event-meta">

                                <span>
                                    📍 Computer Lab
                                </span>

                                <span>
                                    ⏰ 10:00 AM
                                </span>

                            </div>


                            <a
                                href="#registration"
                                class="text-link">
                                Register →
                            </a>

                        </div>

                    </article>


                    <!-- EVENT 2 -->

                    <article class="event-card featured-card">

                        <figure class="event-image-wrap">

                            <img
                                src="https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&w=1000&q=85"
                                alt="Students enjoying a campus cultural event"
                                width="1000"
                                height="700"
                                loading="lazy">


                            <span class="event-tag">
                                CULTURE
                            </span>


                            <figcaption>
                                Students enjoying a campus cultural event
                            </figcaption>

                        </figure>


                        <div class="event-card-body">

                            <p class="event-date">

                                <time datetime="2026-10-02">
                                    02 OCT 2026
                                </time>

                            </p>


                            <h3>
                                Kreiva Campus Evening
                            </h3>


                            <p>

                                An evening for music, performance,
                                creativity and student-led cultural
                                activities.

                            </p>


                            <div class="event-meta">

                                <span>
                                    📍 Main Auditorium
                                </span>

                                <span>
                                    ⏰ 5:00 PM
                                </span>

                            </div>


                            <a
                                href="#registration"
                                class="text-link">
                                Register →
                            </a>

                        </div>

                    </article>


                    <!-- EVENT 3 -->

                    <article class="event-card">

                        <figure class="event-image-wrap">

                            <img
                                src="https://images.unsplash.com/photo-1531058020387-3be344556be6?auto=format&fit=crop&w=1000&q=85"
                                alt="Students attending an academic workshop"
                                width="1000"
                                height="700"
                                loading="lazy">


                            <span class="event-tag">
                                WORKSHOP
                            </span>


                            <figcaption>
                                Students attending an academic workshop
                            </figcaption>

                        </figure>


                        <div class="event-card-body">

                            <p class="event-date">

                                <time datetime="2026-10-10">
                                    10 OCT 2026
                                </time>

                            </p>


                            <h3>
                                AI &amp; Innovation Workshop
                            </h3>


                            <p>

                                Explore emerging ideas in artificial
                                intelligence and learn through
                                hands-on activities.

                            </p>


                            <div class="event-meta">

                                <span>
                                    📍 Seminar Hall
                                </span>

                                <span>
                                    ⏰ 11:00 AM
                                </span>

                            </div>


                            <a
                                href="#registration"
                                class="text-link">
                                Register →
                            </a>

                        </div>

                    </article>

                </div>

            </section>


            <!-- ================= ABOUT ================= -->

            <section
                id="about"
                class="section split-section"
                aria-labelledby="about-title">


                <div class="about-copy">

                    <p class="eyebrow accent-text">
                        ABOUT THE PROJECT
                    </p>


                    <h2 id="about-title">
                        One place for campus moments.
                    </h2>


                    <p>

                        The Campus Event Board is designed as a
                        student-friendly interface for discovering
                        and registering for academic, technical,
                        cultural and community activities.

                    </p>


                    <p>

                        The layout uses semantic HTML, responsive
                        CSS Grid, accessible labels, responsive
                        images and a reusable design system.

                    </p>


                    <a
                        class="button button-primary"
                        href="#registration">
                        Join an Event
                    </a>

                </div>


                <aside
                    class="about-panel"
                    aria-label="Institute information">


                    <span class="panel-icon">
                        IIITV
                    </span>


                    <h3>
                        Indian Institute of Information Technology
                        Vadodara
                    </h3>


                    <p>

                        The institute is currently operating from
                        its Gandhinagar campus at Government
                        Engineering College, Sector 28.

                    </p>


                    <a
                        href="https://iiitvadodara.ac.in/"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="text-link">

                        Visit institute website ↗

                    </a>

                </aside>

            </section>


            <!-- ================= SCHEDULE ================= -->

            <section
                id="schedule"
                class="section schedule-section"
                aria-labelledby="schedule-title">


                <div class="section-heading">

                    <div>

                        <p class="eyebrow accent-text">
                            PLAN AHEAD
                        </p>

                        <h2 id="schedule-title">
                            Event Schedule
                        </h2>

                    </div>


                    <p>
                        Quickly check the date, venue and timing
                        before registering.
                    </p>

                </div>


                <div class="table-wrapper">

                    <table>

                        <caption class="visually-hidden">
                            Schedule of upcoming campus events
                        </caption>


                        <thead>

                            <tr>

                                <th scope="col">
                                    Event
                                </th>

                                <th scope="col">
                                    Date
                                </th>

                                <th scope="col">
                                    Time
                                </th>

                                <th scope="col">
                                    Venue
                                </th>

                            </tr>

                        </thead>


                        <tbody>

                            <tr>

                                <td>
                                    Coding Club
                                </td>

                                <td>

                                    <time datetime="2026-09-25">
                                        25 September 2026
                                    </time>

                                </td>

                                <td>
                                    10:00 AM
                                </td>

                                <td>
                                    Computer Lab
                                </td>

                            </tr>


                            <tr>

                                <td>
                                    Campus Evening
                                </td>

                                <td>

                                    <time datetime="2026-10-02">
                                        02 October 2026
                                    </time>

                                </td>

                                <td>
                                    5:00 PM
                                </td>

                                <td>
                                    Main Auditorium
                                </td>

                            </tr>


                            <tr>

                                <td>
                                    AI &amp; Innovation Workshop
                                </td>

                                <td>

                                    <time datetime="2026-10-10">
                                        10 October 2026
                                    </time>

                                </td>

                                <td>
                                    11:00 AM
                                </td>

                                <td>
                                    Seminar Hall
                                </td>

                            </tr>

                        </tbody>

                    </table>

                </div>

            </section>


            <!-- ================= REGISTRATION ================= -->

            <section
                id="registration"
                class="section registration-section"
                aria-labelledby="registration-title">


                <div class="registration-copy">

                    <p class="eyebrow">
                        READY TO PARTICIPATE?
                    </p>


                    <h2 id="registration-title">
                        Reserve your place.
                    </h2>


                    <p>
                        Fill in the form and submit your event preference.
                    </p>

                </div>


                <form
                    class="event-form"
                    action="#"
                    method="post">


                    <div class="form-group">

                        <label for="student-name">
                            Student Name
                        </label>


                        <input
                            type="text"
                            id="student-name"
                            name="student-name"
                            placeholder="Enter your name"
                            required>

                    </div>


                    <div class="form-group">

                        <label for="student-email">
                            Email Address
                        </label>


                        <input
                            type="email"
                            id="student-email"
                            name="student-email"
                            placeholder="name@example.com"
                            required>

                    </div>


                    <div class="form-group">

                        <label for="event-choice">
                            Choose Event
                        </label>


                        <select
                            id="event-choice"
                            name="event-choice"
                            required>

                            <option value="">
                                Select an event
                            </option>

                            <option value="code-create">
                                Code &amp; Create
                            </option>

                            <option value="kreiva">
                                Kreiva Campus Evening
                            </option>

                            <option value="ai-workshop">
                                AI &amp; Innovation Workshop
                            </option>

                        </select>

                    </div>


                    <div class="form-group">

                        <label for="event-date">
                            Event Date
                        </label>


                        <input
                            type="date"
                            id="event-date"
                            name="event-date"
                            required>

                    </div>


                    <button
                        type="submit"
                        class="button button-primary submit-button">

                        Submit Registration

                    </button>

                </form>

            </section>


            <!-- ================= CONTACT ================= -->

            <section
                id="contact"
                class="section contact-section"
                aria-labelledby="contact-title">


                <div>

                    <p class="eyebrow accent-text">
                        GET IN TOUCH
                    </p>


                    <h2 id="contact-title">
                        Contact the Event Desk
                    </h2>


                    <p class="reading-width">

                        For event-related questions, reach out
                        through the details below.

                    </p>

                </div>


                <address class="contact-card">

                    <p>

                        📧

                        <a href="mailto:administration@iiitvadodara.ac.in">
                            administration@iiitvadodara.ac.in
                        </a>

                    </p>


                    <p>

                        📞

                        <a href="tel:+917929775281">
                            +91 79 2975 0281
                        </a>

                    </p>


                    <p>

                        📍 C/O Block No. 9, Government Engineering
                        College, Sector-28, Gandhinagar,
                        Gujarat - 382028

                    </p>

                </address>

            </section>

        </main>


        <!-- ================= FOOTER ================= -->

        <footer class="site-footer">

            <div>

                <strong>
                    IIIT VADODARA
                </strong>

                <p>
                    Campus Event Board • Student Project
                </p>

            </div>


            <p>
                &copy; 2026 Campus Event Board.
                All rights reserved.
            </p>

        </footer>

    </div>


    <!-- Lab 5 note:
         hamburger click behaviour can be added
         in a later JavaScript lab. -->

</body>

</html>
```

### `style.css`

**Paste the final cumulative `style.css` from the completed project here.**

```css
/* =========================================================
   IIIT VADODARA EVENT BOARD — LAB 5
   Design system + Box Model + CSS Grid + Responsive Design
   ========================================================= */

/* A6: border-box makes declared width include padding + border. */
*,
*::before,
*::after {
    box-sizing: border-box;
}

:root {
    /* A2: named design-system variables */
    /* A3: HEX */
    --brand-dark: #081b62;
    --brand: #2563eb;
    --accent: hsl(24 95% 53%);
    --overlay: rgb(0 0 0 / 40%);
    --ink: #172033;
    --muted: rgb(206 95 39);
    --paper: #f6f8fc;
    --surface: #ffffff;
    --line: #dfe5f0;
    --success: #168a5b;
    --shadow: 0 0.5rem 1.5rem rgb(0 0 0 / 8%); /* A3: semi-transparent rgb() */
    

    /* A5: type scale */
    --text-sm: 0.875rem;
    --text-body: 1rem;
    --text-lg: 1.25rem;
    --text-xl: 1.75rem;
    --text-2xl: 2.5rem;
    --text-hero: clamp(2.4rem, 7vw, 5.5rem); /* A4: clamp() */

    --radius-sm: 0.6rem;
    --radius-md: 1rem;
    --radius-lg: 1.5rem;
    --container: min(90%, 70rem); /* A7: capped centered container */
}

html {
    scroll-behavior: smooth;
    scroll-padding-top: 5rem;
}

body {
    margin: 0;
    background: var(--paper);
    color: var(--ink);
    font-family: "Inter", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    font-size: var(--text-body);
    line-height: 1.5; /* A5 */
}

img {
    max-width: 100%; /* A9 */
    height: auto;
    display: block;
}

a {
    color: inherit;
}

button,
input,
select {
    font: inherit;
}

.site-shell {
    /* B2: Grid page regions */
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr;
    grid-template-areas:
        "header"
        "main"
        "footer";
}

.site-header {
    grid-area: header;
    position: sticky;
    top: 0;
    z-index: 100;
    min-height: 4.3rem;
    padding: 0.75rem 5%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
    background: #64748B; /* A3: semi-transparent overlay */
    border-bottom: 1px solid var(--line);
    backdrop-filter: blur(0.8rem);
}

.brand {
    display: flex;
    align-items: center;
    gap: 0.7rem;
    text-decoration: none;
    min-width: 0;
}

.brand-logo {
    width: 3rem;
    height: 3rem;
    object-fit: contain;
    border-radius: 0.5rem;
    background: var(--surface);
}

.brand-text {
    display: grid;
    line-height: 1.1;
    forced-color-adjust: auto;
}

.brand-text strong {
    font-family: "Space Grotesk", sans-serif;
    font-size: 0.95rem;
    letter-spacing: 0.04em;
    text-decoration-color: #000000;
}

.brand-text small {
    color: #000000;
    font-size: 0.72rem;
    margin-top: 0.25rem;
}

.nav-area {
    display: flex;
    align-items: center;
}

.nav-links {
    display: none; /* B6: hidden on phones */
    align-items: center;
    gap: 0.25rem;
}

.nav-links a {
    padding: 0.65rem 0.8rem;
    color: var(--ink);
    text-decoration: none;
    font-size: var(--text-sm);
    font-weight: 600;
    border-radius: 0.6rem;
}

.nav-links a:hover,
.nav-links a:focus-visible {
    background: var(--paper);
    color: var(--brand);
}

.nav-links .nav-cta {
    margin-left: 0.5rem;
    color: var(--surface);
    background: var(--brand);
}

.nav-links .nav-cta:hover,
.nav-links .nav-cta:focus-visible {
    background: var(--brand-dark);
    color: var(--surface);
}

.menu-toggle {
    display: inline-flex;
    width: 2.8rem;
    height: 2.8rem;
    padding: 0.65rem;
    flex-direction: column;
    justify-content: space-around;
    border: 1px solid var(--line);
    border-radius: 0.65rem;
    background: var(--surface);
    cursor: pointer;
}

.menu-toggle span {
    display: block;
    width: 100%;
    height: 2px;
    background: var(--ink);
}

.main-content {
    grid-area: main;
}

.hero {
    position: relative;
    min-height: 75vh;
    overflow: hidden;
    display: flex;
    place-items: center;
    justify-content: center;
    isolation: isolate;
    /* background: var(--brand-dark); */
    text-align: center;
}

.hero-image {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover; /* A9 */
    object-position: center;
    z-index: -2;
}

.hero-overlay {
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 35%);
    z-index: -1;
}

/*
.hero-content {
    width: var(--container);
    padding: 6rem 0;
    color: var(--surface);
}
*/

.hero-content {
    width: min(90%, 70rem);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 6rem 0;
    text-align: center;
    color: #ffffff;
}

.eyebrow {
    margin: 0 0 1rem;
    color: #ffffff;
    font-size: 0.75rem;
    font-weight: 800;
    letter-spacing: 0.16em;
    text-align: center;
}

.accent-text {
    color: var(--accent);
}

.hero h1 {
    max-width: 100%;
    margin: 0;
    font-family: "Space Grotesk", sans-serif;
    font-size: clamp(2.5rem, 6vw, 5.5rem);
    line-height: 1;
    color: #ffffff;
    text-align: center;
    letter-spacing: -0.04em;
    text-align: left;
}

.hero h1 span {
    color: #f97316; /* A3: HEX used as a deliberate one-off highlight */
}

.hero-text {
    max-width: 55rem; /* A5 */
    margin: 1.5rem auto 0;
    color: rgb(255 255 255 / 90%);
    font-size: clamp(1rem, 2vw, 1.2rem);
    line-height: 1.7;
    text-align: center;
}

.hero-actions {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.8rem;
    margin-top: 2rem;
}

.button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-height: 3rem;
    padding: 0.8rem 1.2rem;
    border: 1px solid transparent;
    border-radius: 0.75rem;
    text-decoration: none;
    font-weight: 700;
    cursor: pointer;
    transition: transform 160ms ease, background 160ms ease, color 160ms ease;
}

.button:hover {
    transform: translateY(-2px);
}

.button-primary {
    color: var(--surface);
    background: var(--accent);
}

.button-primary:hover,
.button-primary:focus-visible {
    background: hsl(27 80% 44%); /* A3: HSL */
}

.button-ghost {
    color: var(--surface);
    border-color: rgb(255 255 255 / 60%);
    background: rgb(255 255 255 / 8%);
}

.hero-badge {
    position: absolute;
    right: 5%;
    bottom: 2rem;
    display: none;
    padding: 1rem 1.2rem;
    color: var(--surface);
    background: rgb(8 27 98 / 70%);
    border: 1px solid rgb(255 255 255 / 25%);
    border-radius: 1rem;
    backdrop-filter: blur(0.5rem);
}

.hero-badge strong,
.hero-badge span {
    display: block;
}

.hero-badge strong {
    font-family: "Space Grotesk", sans-serif;
    font-size: 1.8rem;
}

.hero-badge span {
    color: rgb(255 255 255 / 75%);
    font-size: 0.8rem;
}


/* =========================================================
   STATS / EVENT BOARD HIGHLIGHTS
   ========================================================= */

.stats {
    width: 90%;
    max-width: 70rem;
    margin: -2rem auto 0;
    position: relative;
    z-index: 5;

    display: grid;

    /* 4 cards in ONE row */
    grid-template-columns: repeat(4, 1fr);

    gap: 1rem;

    /* Black / dark background */
    background: #111827;

    padding: 1.5rem;
    border-radius: 1rem;

    box-shadow: 0 0.8rem 2rem rgb(0 0 0 / 20%);
}


/* If "Event Board Highlights" is inside .stats */

.stats > h2 {
    grid-column: 1 / -1;

    margin: 0 0 0.5rem;

    color: #ffffff;
    font-family: "Space Grotesk", sans-serif;
    font-size: 1.5rem;
}


/* Individual stat box */

.stat-item {
    min-height: 8rem;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    padding: 1.25rem 1rem;

    text-align: center;

    background: #ffffff;
    border: 1px solid #dfe5f0;
    border-radius: 1rem;

    box-shadow: 0 0.5rem 1.2rem rgb(0 0 0 / 10%);

    transition: transform 180ms ease,
                box-shadow 180ms ease;
}


/* Number */

.stat-item strong {
    display: block;

    margin-bottom: 0.35rem;

    color: #2563eb;

    font-family: "Space Grotesk", sans-serif;
    font-size: 1.6rem;
    font-weight: 800;
}


/* Description */

.stat-item span {
    display: block;

    color: #ce5f27;
    font-size: 0.875rem;
}


/* Hover */

.stat-item:hover {
    transform: translateY(-0.3rem);

    box-shadow: 0 0.8rem 1.8rem rgb(0 0 0 / 18%);
}


.section {
    width: var(--container);
    margin: 0 auto;
    padding: 5rem 0;
}

.section-heading {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    margin-bottom: 2rem;
}

.section-heading h2,
.about-copy h2,
.registration-copy h2,
.contact-section h2 {
    margin: 0;
    font-family: "Space Grotesk", sans-serif;
    font-size: var(--text-2xl);
    line-height: 1.1;
}

.section-heading > p,
.about-copy > p,
.registration-copy > p,
.contact-section .reading-width {
    max-width: 65ch; /* A5 */
    color: var(--muted);
}

.event-grid {
    /* B3: no media query needed for the card reflow */
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr));
    gap: 1.25rem; /* B4 */
}

.event-card {
    overflow: hidden;
    margin: 0;
    padding: 0;
    background: var(--surface);
    border: 1px solid var(--line); /* A8 */
    border-radius: var(--radius-lg);
    box-shadow: 0 0.125rem 0.5rem rgb(0 0 0 / 8%); /* A8 */
    transition: transform 180ms ease, box-shadow 180ms ease;
}

.event-card:hover {
    transform: translateY(-0.35rem);
    box-shadow: 0 1rem 2rem rgb(0 0 0 / 12%);
}

.event-image-wrap {
    position: relative;
    aspect-ratio: 16 / 10;
    overflow: hidden;
}

.event-image-wrap img {
    width: 100%;
    height: 100%;
    object-fit: cover; /* A9 */
    transition: transform 300ms ease;
}

.event-card:hover .event-image-wrap img {
    transform: scale(1.04);
}
/* Register link */
.event-card a.text-link {
    color: blue !important;
    font-weight: 800;
    text-decoration: underline;
}

/* Register link on hover */
.event-card a.text-link:hover,
.event-card a.text-link:focus-visible {
    color: orange !important;
    text-decoration: underline;
}
.event-tag {
    position: absolute;
    left: 0.9rem;
    top: 0.9rem;
    padding: 0.4rem 0.6rem;
    color: var(--surface);
    background: var(--brand);
    border-radius: 999px;
    font-size: 0.7rem;
    font-weight: 800;
    letter-spacing: 0.08em;
}

.featured-card .event-tag {
    background: var(--accent);
}

.event-card-body {
    padding: 1.25rem;
    margin: 0;
}

.event-date {
    margin: 0 0 0.4rem;
    color: var(--accent);
    font-size: 0.75rem;
    font-weight: 800;
    letter-spacing: 0.08em;
}

.event-card h3 {
    margin: 0;
    font-family: "Space Grotesk", sans-serif;
    font-size: var(--text-lg);
}

.event-card p:not(.event-date) {
    color: var(--muted);
}

.event-meta {
    display: flex;
    flex-wrap: wrap;
    gap: 0.6rem 1rem;
    margin: 1rem 0;
    color: var(--muted);
    font-size: 0.8rem;
}

.text-link {
    color:var(--brand-dark);
    font-weight: 800;
    text-decoration:underline;
}

.text-link:hover,
.text-link:focus-visible {
    color: #f97316;
    text-decoration: underline;
}

.split-section {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;
    align-items: center;
}

.about-copy p {
    max-width: 65ch;
}

.about-panel {
    padding: 2rem;
    background: linear-gradient(145deg, var(--brand-dark), var(--brand));
    color: var(--surface);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow);
}

.about-panel p {
    color: rgb(255 255 255 / 78%);
}

.panel-icon {
    display: inline-grid;
    width: 4rem;
    height: 4rem;
    place-items: center;
    margin-bottom: 1rem;
    color: var(--brand-dark);
    background: var(--surface);
    border-radius: 1rem;
    font-family: "Space Grotesk", sans-serif;
    font-weight: 800;
}

.about-panel .text-link {
    color: #ffd08a;
}

.schedule-section {
    padding-top: 2rem;
}

.table-wrapper {
    overflow-x: auto;
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: var(--radius-md);
    box-shadow: var(--shadow);
}

table {
    width: 100%;
    border-collapse: collapse;
    min-width: 40rem;
}

th,
td {
    padding: 1rem;
    text-align: left;
    border-bottom: 1px solid var(--line);
}

th {
    color: var(--surface);
    background: var(--brand);
    font-size: 0.85rem;
}

tbody tr:nth-child(even) {
    background: hsl(357, 55%, 41%);
}

tbody tr:hover {
    background: hsl(220, 55%, 39%);
}

.registration-section {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;
    padding: 2rem;
    background: var(--brand-dark);
    color: var(--surface);
    border-radius: var(--radius-lg);
}

.registration-copy p {
    color: rgb(255 255 255 / 75%);
}

.event-form {
    display: grid;
    gap: 1rem;
}

.form-group {
    display: grid;
    gap: 0.4rem;
}

.form-group label {
    font-size: 0.85rem;
    font-weight: 700;
}

.form-group input,
.form-group select {
    width: 100%;
    padding: 0.85rem 1rem;
    color: var(--ink);
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 0.65rem;
}

.form-group input:focus,
.form-group select:focus {
    outline: 3px solid rgb(230 126 34 / 25%);
    border-color: var(--accent);
}

.submit-button {
    width: 100%;
}

.contact-section {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;
    align-items: start;
}

.contact-card {
    padding: 1.5rem;
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: var(--radius-md);
    box-shadow: var(--shadow);
    font-style: normal;
}

.contact-card p {
    margin: 0 0 1rem;
}

.contact-card p:last-child {
    margin-bottom: 0;
}

.contact-card a {
    color: var(--brand);
    font-weight: 700;
}

.site-footer {
    grid-area: footer;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 2rem 5%;
    color: rgb(255 255 255 / 80%);
    background: #07164e; /* HEX */
}

.site-footer strong {
    color: var(--surface);
    font-family: "Space Grotesk", sans-serif;
}

.site-footer p {
    margin: 0;
    font-size: var(--text-sm);
}


/* A4: calc() for fluid spacing/container math */

.hero-content,
.section {
    width: calc(100% - 2rem);
    max-width: 70rem;
}


/* B5: mobile-first — add columns as the screen grows. */

@media (min-width: 40rem) {

    .section-heading {
        flex-direction: row;
        align-items: end;
        justify-content: space-between;
    }

    .split-section,
    .contact-section {
        grid-template-columns: 1.2fr 0.8fr;
    }

    .registration-section {
        grid-template-columns: 0.9fr 1.1fr;
        align-items: center;
    }
}


/* B6: reveal full nav on wide screens. */

@media (min-width: 64rem) {

    .nav-links {
        display: flex;
    }

    .menu-toggle {
        display: none;
    }

    .hero-badge {
        display: block;
    }

    .hero {
        min-height: 80vh;
    }

    .hero-content {
        width: 90%;
        padding: 4rem 0;
    }

    .hero .eyebrow {
        font-size: 0.65rem;
        letter-spacing: 0.1rem;
    }

    .hero h1 {
        font-size: clamp(2.2rem, 12vw, 3.5rem);
    }

    .hero-actions {
        flex-direction: column;
        width: 100%;
    }

    .hero-actions .button {
        width: 100%;
        max-width: 18rem;
    }

    .registration-section {
        padding: 3rem;
    }
}


/* A7: four-value shorthand example — top right bottom left. */

.site-footer {
    margin-top: 0;
    padding: 2rem 5% 2.5rem 5%;
}


/* A9: display:none is different from visibility:hidden:
   this button is removed from layout on wide screens. */

@media (min-width: 64rem) {
    .menu-toggle {
        display: none;
    }
}


/* =========================================================
   LAB 3 + LAB 4 — REQUIRED SELECTOR PRACTICE
   These rules are added without changing the existing
   visual design. 
   ========================================================= */


/* ---------- LAB 3: accessibility / semantic styling ---------- */

/* Skip-link: available to keyboard users without affecting
   the normal page appearance until it receives focus. */

.skip-link {
    position: absolute;
    left: -9999px;
    top: 0;
}

.skip-link:focus {
    left: 1rem;
    top: 1rem;
    z-index: 1000;
    padding: 0.5rem 1rem;
    background: var(--surface);
    color: var(--ink);
}


/* ---------- LAB 4: combinator selectors ---------- */

/* Child combinator: styles only direct children of .nav-links. */

.nav-links > a {
    text-decoration: none;
}

/* Descendant selector would also match deeper links.
   The > above matches only direct child links. */

/* Adjacent sibling selector: the first paragraph directly
   following an h2. */

.section h2 + p {
    margin-top: 0;
}

/* General sibling selector: paragraphs appearing after h2
   at the same parent level. */

.section h2 ~ p {
    max-width: 65ch;
}


/* ---------- LAB 4: attribute selectors ---------- */

/* External HTTPS links. */

a[href^="https"]::after {
    content: " ↗";
}

/* Form controls selected by their type attribute. */

input[type="email"] {
    width: 100%;
}

input[type="date"] {
    width: 100%;
}


/* ---------- LAB 4: pseudo-elements ---------- */

/* Adds no visible content unless supported by the element. */

.section-heading h2::before {
    content: "";
}

/* Placeholder selector. */

input::placeholder,
select::placeholder {
    opacity: 1;
}


/* ---------- LAB 4: LVHA link order ---------- */

/* Keep the normal appearance unchanged. */

a:link {
    color: inherit;
}

a:visited {
    color: inherit;
}

a:hover {
    color: inherit;
}

a:active {
    color: inherit;
}


/* ---------- LAB 4: inheritance / reset keywords ---------- */

/* Demonstrates inherit without changing the appearance. */

.site-footer a {
    color: inherit;
}

/* Demonstrates initial and unset while preserving the
   existing visual result. */

.event-card h3 {
    font-weight: initial;
}

.event-card .event-meta {
    text-decoration: unset;
}


/* ---------- LAB 4: :is() and :where() ---------- */

/* Grouped selector using :is(). */

:is(.event-card, .about-panel, .contact-card) a {
    text-decoration-thickness: inherit;
}

/* Low-specificity grouping using :where(). */

:where(.event-card, .about-panel, .contact-card) p {
    line-height: inherit;
}


/* ---------- LAB 4: specificity practice ---------- */

/* The selectors below intentionally use classes rather than IDs. */

.event-card .text-link {
    text-decoration-color: currentColor;
}


/* ---------- LAB 4: cascade layer demonstration ---------- */

@layer lab4 {
    .lab4-selector-note {
        color: inherit;
    }
}


/* =========================================================
   FAQ SECTION
   ========================================================= */

.faq-section {
    width: var(--container);
    max-width: 70rem;
    margin: 0 auto;
    padding: 5rem 0;
}

.faq-section h2 {
    margin: 0 0 2rem;
    font-family: "Space Grotesk", sans-serif;
    font-size: var(--text-2xl);
    line-height: 1.1;
    color: var(--ink);
}


/* Individual FAQ box */

.faq-section details {
    margin-bottom: 1rem;
    padding: 1rem 1.25rem;
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: var(--radius-md);
    box-shadow: var(--shadow);
}


/* FAQ question */

.faq-section summary {
    padding: 0.25rem;
    color: var(--ink);
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
}


/* Hover effect */

.faq-section summary:hover {
    color: var(--brand);
}


/* Keyboard focus */

.faq-section summary:focus-visible {
    outline: 3px solid rgb(37 99 235 / 25%);
    outline-offset: 3px;
    border-radius: 0.25rem;
}


/* FAQ answer */

.faq-section details p {
    max-width: 65ch;
    margin: 0.75rem 0 0;
    color: var(--muted);
    line-height: 1.6;
}


/* Open FAQ */

.faq-section details[open] {
    border-color: var(--brand);
}


/* Open question */

.faq-section details[open] summary {
    color: var(--brand);
    margin-bottom: 0.5rem;
}

```

---

