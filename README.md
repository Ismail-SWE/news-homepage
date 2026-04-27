# Frontend Mentor - News homepage solution

This is a solution to the [News homepage challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/news-homepage-H6SWTa1MFl).

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [AI Collaboration](#ai-collaboration)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the interface depending on their device's screen size
- See hover and focus states for all interactive elements on the page
- Toggle the mobile navigation menu open and closed

### Screenshot

![](./preview.jpg)

### Links

- Solution URL: (https://github.com/Ismail-SWE)
- Live Site URL: (https://ismail-swe.github.io/news-homepage/)

## My process

### Built with

- Semantic HTML5 markup
- CSS Grid (12 column system)
- Flexbox
- Vanilla JavaScript
- Mobile-first responsive design
- Google Fonts (Inter)
- CSS custom properties

### What I learned

**1. CSS Grid — 12 column system**

12 columns are used because the number 12 is divisible by 2, 3, 4, and 6, making it flexible for any layout ratio:

```css
.grid-container {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 24px;
}

.featured { grid-column: span 8; }
aside    { grid-column: span 4; grid-row: span 2; }
section  { grid-column: span 12; }
```

**2. grid-area — placing elements by name**

```css
.container {
    grid-template-areas:
        'header  header  header'
        'main    main    sidebar'
        'footer  footer  footer';
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
```

**3. grid-column and grid-row — line-based placement**

```css
/* from line to line */
.item { grid-column: 1 / 4; }

/* relative — how many columns to span */
.item { grid-column: span 3; }
```

**4. minmax() — flexible sizing**

```css
grid-template-rows: repeat(3, minmax(150px, auto));
/* minimum 150px, expands if content is larger */
```

**5. gap — spacing in grid and flex**

```css
/* old way */
grid-column-gap: 20px;
grid-row-gap: 20px;

/* modern */
gap: 20px;
gap: 20px 40px; /* row column */
```

**6. object-fit — proper image display**

```css
img {
    width: 100%;
    height: 300px;
    object-fit: cover; /* image is cropped, not stretched */
}
```

**7. Nested grid — grid inside grid**

```css
.featured {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

/* picture spans 2 columns, h1 and div auto-place below */
.featured picture { grid-column: span 2; }
```

**8. Auto-placement**

Grid automatically places elements into empty cells in order. Once an element with `span 2` takes two columns, the next element automatically falls into the correct position.

**9. Flexbox + Grid together**

```css
nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.nav-links {
    display: flex;
    gap: 24px;
    margin: 0 auto; /* centers between logo and hamburger */
}
```

**10. Responsive design — media queries**

```css
@media (max-width: 768px) {
    .grid-container {
        grid-template-columns: 1fr;
    }

    .featured {
        grid-column: 1;
        grid-template-columns: 1fr;
    }

    .hamburger { display: block; }
    .nav-links  { display: none; }
    .nav-links.open { display: flex; }
}
```

**11. Mobile menu — JavaScript toggle**

```js
const hamburger = document.querySelector('.hamburger');
const navLinks = document.querySelector('.nav-links');
const overlay = document.getElementById('overlay');

hamburger.addEventListener('click', () => {
    navLinks.classList.toggle('open');
    overlay.classList.toggle('open');
});

overlay.addEventListener('click', () => {
    navLinks.classList.remove('open');
    overlay.classList.remove('open');
});
```

**12. picture element — responsive images**

```html
<picture>
    <source media="(min-width: 768px)" srcset="./assets/images/image-web-3-desktop.jpg"/>
    <img src="./assets/images/image-web-3-mobile.jpg" alt="Web 3.0"/>
</picture>
```

The browser automatically shows the desktop image on large screens and the mobile image on small screens.

**13. CSS text effects**

```css
.featured a {
    text-transform: uppercase;
    letter-spacing: 4px;
}

.featured a:hover {
    box-shadow: 4px 4px 0px 0px rgba(0, 0, 0, 0.4);
    transition: box-shadow 0.2s ease;
}
```

**14. flex-shrink: 0 — important for images in flex containers**

```css
.trending-item img {
    width: 100px;
    height: 130px;
    object-fit: cover;
    flex-shrink: 0; /* prevents image from shrinking */
}
```

**15. Sketching grid layouts in Google Sheets**

Before writing code, sketching the grid layout in Google Sheets by merging cells and adding colors helps visualize the structure clearly and makes CSS much easier to write.

### Continued development

- CSS animations and transitions
- JavaScript ES6+ in depth
- React framework
- TypeScript
- Accessibility (ARIA) improvements
- CSS custom properties

### AI Collaboration

- **Tool:** Claude (Anthropic)
- **How:** Used for learning CSS Grid concepts, debugging layout issues, writing responsive design media queries, and implementing JavaScript toggle functionality
- **What worked well:** Learning through Q&A with screenshots made it easy to identify and fix issues instantly. Each concept was explained clearly with examples
- **What didn't:** Some CSS values still needed manual trial and error — AI cannot always predict the exact visual result

## Author

- Frontend Mentor - [@Ismail-SWE](https://www.frontendmentor.io/profile/Ismail-SWE)
- GitHub - [@Ismail-SWE](https://github.com/Ismail-SWE)