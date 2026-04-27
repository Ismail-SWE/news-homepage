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

![](./screenshot.jpg)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

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

**1. CSS Grid — 12 ustunli sistema**

Har qanday nisbatni ifodalash uchun 12 ustun ishlatiladi — chunki 12 soni 2, 3, 4, 6 ga bo'linadi:

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

**2. grid-area — nom bilan joylash**

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

**3. grid-column va grid-row — chiziq usuli**

```css
/* chiziqdan chiziqqa */
.item { grid-column: 1 / 4; }

/* nisbiy — qancha ustun egallash */
.item { grid-column: span 3; }
```

**4. minmax() — moslashuvchan o'lcham**

```css
grid-template-rows: repeat(3, minmax(150px, auto));
/* kamida 150px, kontent ko'p bo'lsa kengayadi */
```

**5. gap — grid va flex da oraliq**

```css
/* eski usul */
grid-column-gap: 20px;
grid-row-gap: 20px;

/* zamonaviy */
gap: 20px;
gap: 20px 40px; /* row column */
```

**6. object-fit — rasmni to'g'ri ko'rsatish**

```css
img {
    width: 100%;
    height: 300px;
    object-fit: cover; /* rasm cho'zilmaydi, kesib ko'rsatadi */
}
```

**7. Nested grid — grid ichida grid**

```css
.featured {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

/* picture span 2 oladi, h1 va div avtomatik joylashadi */
.featured picture { grid-column: span 2; }
```

**8. Auto-placement — avtomatik joylash**

Grid elementlarni o'zi navbat bilan bo'sh kataklarga joylashtiradi. `span 2` bergan element ikki ustunni olgandan keyin, keyingi element o'zi to'g'ri joyga tushadi.

**9. Flexbox + Grid birgalikda**

```css
nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.nav-links {
    display: flex;
    gap: 24px;
    margin: 0 auto; /* o'rtaga olish */
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

**12. picture elementi — responsive rasm**

```html
<picture>
    <source media="(min-width: 768px)" srcset="./assets/images/image-web-3-desktop.jpg"/>
    <img src="./assets/images/image-web-3-mobile.jpg" alt="Web 3.0"/>
</picture>
```

Katta ekranda desktop rasm, kichik ekranda mobile rasm avtomatik ko'rsatiladi.

**13. CSS text effektlar**

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

**14. flex-shrink: 0 — muhim**

```css
.trending-item img {
    width: 100px;
    height: 130px;
    object-fit: cover;
    flex-shrink: 0; /* rasm kichraymaydi */
}
```

**15. Google Sheets da grid eskiz qilish**

Kod yozishdan oldin Google Sheets da katakchalarni birlashtrib, ranglash orqali grid layoutni oldin vizual chizib olish — bu vaqtni tejaydi va CSS yozishni osonlashtiradi.

### Continued development

- CSS animations va transitions
- JavaScript ES6+ chuqurroq
- React framework
- TypeScript
- Accessibility (ARIA) yaxshilash
- CSS variables ishlatish

### AI Collaboration

- **Tool:** Claude (Anthropic)
- **How:** CSS Grid tushunchalarini o'rganishda, debugging qilishda, responsive design va JavaScript yozishda yordam olish uchun foydalandim
- **What worked well:** Har bir konsepsiyani savol-javob orqali tushunish juda samarali bo'ldi. Screenshot yuborib, nima xato ekanini aniqlash qulay bo'ldi
- **What didn't:** Ba'zi CSS qiymatlarini o'zim sinab ko'rib topishim kerak bo'ldi — AI har doim ham vizual natijani oldindan ayta olmaydi

## Author

- Frontend Mentor - [@yourusername](https://www.frontendmentor.io/profile/yourusername)
- GitHub - [@Ismail-SWE](https://github.com/Ismail-SWE)