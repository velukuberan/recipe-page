# Frontend Mentor - Recipe page

This is a solution to the [Recipe page challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/recipe-page-KiTsR8QQKm). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

<p align="center">
  <img src="./preview.jpg" alt="Design preview for the Recipe page coding challenge" width="50%">
</p>


## Table of Contents

-   [Overview](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#overview)
    -   [The Challenge](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#the-challenge)
    -   [Screenshot](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#screenshot)
    -   [Links](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#links)
-   [My Process](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#my-process)
    -   [Built With](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#built-with)
    -   [What I Learned](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#what-i-learned)
    -   [Continued Development](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#continued-development)
    -   [Useful Resources](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#useful-resources)
-   [Author](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#author)
-   [Acknowledgments](https://claude.ai/chat/dff9d1ef-3b68-4e9b-8f52-76a7a0936b4b#acknowledgments)

----------

## Overview

### The Challenge

Users should be able to:

-   View the recipe page with proper layout on any device
-   See hover states for interactive elements (if applicable)
-   Experience a responsive design that adapts from mobile (375px) to desktop (1440px)

### Screenshot

<p align="center">
  <figure>
    <img src="https://github.com/user-attachments/assets/4379115d-5c15-4797-a5f3-17b77f9a7f38" alt="Recipe Page Desktop" width="75%">
    <figcaption>On Desktop</figcaption>
  </figure>
</p>

<p align="center">
    <figure>
    <img src="https://github.com/user-attachments/assets/842e4bcd-60a2-49e6-a186-5b7bdc5437ab" alt="Recipe Page Mobile" width="50%">
    <figcaption>On Mobile</figcaption>
  </figure>
</p>

### Links

-   Solution URL: [Add solution URL here](https://github.com/velukuberan/recipe-page)
-   Live Site URL: [Add live site URL here](https://velukuberan.github.io/recipe-page)

----------

## My Process

### Built With

-   Semantic HTML5 markup
-   CSS custom properties (CSS variables)
-   Flexbox
-   CSS Grid
-   Mobile-first workflow
-   BEM (Block Element Modifier) naming convention
-   Google Fonts (Young Serif, Outfit)

### What I Learned

#### 1. Semantic HTML Structure

I focused on using appropriate semantic elements to improve accessibility and document structure:

```html
<main>
    <article class="card">
        <figure class="card__image">
            <img src="./assets/images/image-omelette.jpeg" alt="Omelette Recipe">
        </figure>
        <!-- Content sections -->
    </article>
</main>

```

-   `<main>` - Primary content container
-   `<article>` - Self-contained, independently distributable content
-   `<figure>` - Image with potential caption support

#### 2. Table Accessibility with Row Headers

I learned the importance of using `<th scope="row">` for tables where the first column contains labels:

```html
<table>
    <tbody>
        <tr>
            <th scope="row">Calories</th>
            <td>277kcal</td>
        </tr>
    </tbody>
</table>

```

This helps screen readers announce the relationship between headers and data cells correctly.

#### 3. CSS Custom Properties System

I implemented a comprehensive design token system using CSS custom properties:

```css
:root {
    /* Colors */
    --rose-800: #7A284E;
    --rose-50: #FFF7FB;
    --stone-900: #312E2C;
    --stone-600: #5F564D;
    
    /* Typography */
    --font-serif: 'Young Serif', serif;
    --font-sans: 'Outfit', sans-serif;
    
    /* Spacing Scale */
    --spacing-100: 0.5rem;   /* 8px */
    --spacing-200: 1rem;     /* 16px */
    --spacing-300: 1.5rem;   /* 24px */
    --spacing-400: 2rem;     /* 32px */
}

```

#### 4. Custom List Styling with CSS Counters

For the ordered list in instructions, I used CSS counters to create custom-styled numbers:

```css
.card__instructions ol {
    list-style: none;
    counter-reset: item;
}

.card__instructions ol li::before {
    counter-increment: item;
    content: counter(item) ".";
    color: var(--brown-800);
    font-weight: var(--font-weight-bold);
    position: absolute;
    left: 0;
}

```

#### 5. Custom Bullet Points

For unordered lists, I replaced default bullets with custom-colored ones:

```css
.card__preparation ul li::before,
.card__ingredients ul li::before {
    content: "\2022";
    color: var(--rose-800);
    font-size: var(--font-size-normal);
}

```

#### 6. Responsive Design Strategy

I implemented a mobile-first approach with three breakpoints:

| Breakpoint | Width      | Description                                |
|------------|------------|--------------------------------------------|
| Mobile     | < 768px    | Full-width image, no border-radius on card |
| Tablet     | ≥ 768px    | Centered card with padding                 |
| Desktop    | ≥ 1440px   | Maximum card width, increased margins      |

Key mobile technique - removing card padding to allow full-bleed image:

```css
@media screen and (max-width: 47.9375rem) {
    .card {
        border-radius: 0;
        padding: 0;
    }
    
    .card__text-content {
        padding: 0 var(--spacing-400) var(--spacing-400);
    }
}

```

#### 7. BEM Naming Convention

I structured CSS classes following the BEM methodology:

```
.card                    /* Block */
.card__image             /* Element */
.card__text-content      /* Element */
.card__preparation       /* Element */
.card__divider           /* Element */

```

### Continued Development

Areas I want to improve in future projects:

1.  **Stricter BEM adherence** - Avoid mixing BEM blocks with element selectors like `.card__title h1`. Instead, add explicit classes to all styled elements.
    
2.  **Remove unnecessary HTML wrappers** - The `<span>` elements inside list items were added for styling but could be eliminated with better CSS approaches.
    
3.  **Separation of concerns** - Move presentational elements like `<strong>` in the table to CSS-only solutions.
    
4.  **CSS organization** - Consider splitting CSS into logical partials:
    
    -   `_variables.css` - Custom properties
    -   `_typography.css` - Text presets
    -   `_components.css` - Card and section styles
5.  **Accessibility testing** - Run the page through screen readers and automated accessibility tools.
    

### Useful Resources

-   [MDN - Table Accessibility](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced#tables_for_visually_impaired_users) - Helped understand `<th scope="row">` usage
-   [CSS Tricks - A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) - Reference for flexbox properties
-   [BEM Methodology](https://getbem.com/) - Official BEM documentation
-   [Google Fonts](https://fonts.google.com/) - Young Serif and Outfit font families

----------

## Author

-   Frontend Mentor - [@velukuberan](https://www.frontendmentor.io/profile/velukuberan)
-   GitHub - [@velukuberan](https://github.com/velukuberan)
-   Twitter - [@DevVeeKay](https://x.com/DevVeeKay)

----------

## Acknowledgments

This project was completed as part of my 100-day learning goal to master modern web development fundamentals including semantic HTML, CSS layout techniques, and responsive design patterns.

----------

## Project Structure

```
recipe-page/
├── assets/
│   └── images/
│       ├── favicon-32x32.png
│       └── image-omelette.jpeg
├── index.html
├── style.css
└── README.md

```

## How to Run

1.  Clone the repository
2.  Open `index.html` in your browser
3.  Or use a local development server:
    
    ```bash
    # Using Pythonpython -m http.server 8000# Using Node.js (http-server)npx http-server
    
    ```
    

## License

This project is for learning purposes as part of Frontend Mentor challenges.
