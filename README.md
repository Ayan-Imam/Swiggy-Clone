# Swiggy Home Page Clone

A pixel-faithful clone of the [Swiggy](https://www.swiggy.com/) home page, built with **only HTML and CSS**. There is no JavaScript, no framework and no build step.

The whole page scales proportionally to the screen width, so it can be viewed on phones, tablets, laptops and large monitors.

---

## Sections

1. **Hero:** navbar (logo, Swiggy Corporate, Partner with us, Get the App, Sign in), headline, location and restaurant search boxes, and the three big cards (Food Delivery, Instamart, Dineout) with the veggies and sushi pictures in the corners.
2. **Order our best food options:** a grid of dish images.
3. **Shop groceries on Instamart:** a sideways-scrolling row of grocery categories.
4. **Discover best restaurants on Dineout:** a sideways-scrolling row of restaurant cards (photo, rating, cuisine, price, distance, offer pill, bank offer and PAYTMNEW line).
5. **Get the Swiggy App banner.**
6. **Cities with food delivery:** a 4-column grid of city links with a "Show More" button.
7. **Footer:** Company, Contact us, Legal, Available in, Life at Swiggy, social icons, and the App Store / Google Play badges.

---

## Project structure

```
.
├── index.html    # all the page markup
├── Style.css     # all the styling (including the responsive system)
└── README.md
```

---

## Getting started

No installation is needed.

1. Download or clone the project.
2. Keep `index.html` and `Style.css` in the same folder.
3. Open `index.html` in any modern browser.

You need an internet connection, because the images and the Gilroy fonts are loaded from Swiggy's CDN.

---

## How the responsiveness works

The page is designed once, at a **1440px-wide desktop**, and then shrinks proportionally on smaller screens. Every device sees the same layout, just smaller (like zooming out on a desktop site). Above 1440px the page stays full size and centred.

It is built on a single CSS variable declared at the top of the new-code section of `Style.css`:

```css
:root {
    --design-width: 1440;
    --u: min(1px, calc(100vw / var(--design-width)));
}
```

`--u` means "one design pixel":

| Screen width | Value of `--u` |
| --- | --- |
| 1440px or wider | `1px` |
| Narrower than 1440px | `screen width / 1440` |

Every size is written with it:

```css
.foodHead {
    font-size: calc(25 * var(--u));   /* 25px on a big screen, smaller on a small one */
}
```

**Tips**

- Add new rules using `calc(N * var(--u))` instead of `Npx`, so they scale like the rest of the page.
- To make the page shrink less on small screens, lower `--design-width` (for example to `1000`). The layout will then differ from the full desktop design.
- Text gets very small on phones, so users pinch-zoom to read it.

---

## Customising

| I want to... | Do this |
| --- | --- |
| Add more dishes to "Order our best food options" | Copy an `<img>` line inside the first `.dish` block and change the file name (for example `Pizza.png`). |
| Add more Instamart categories | Copy a `<div><img><p></p></div>` tile inside `.dish2`. |
| Add or edit a Dineout restaurant | Copy a `.dcard` block inside `.dineout` and change the photo, name, rating and offers. |
| Resize the Dineout cards | Change `--dcard-w` on `.dineout` in `Style.css`. |
| Use my own carousel arrows | Replace the `sv1,sv2` placeholder text in `.foodHead` with your SVGs, then delete the "carousel arrows" block in `Style.css`. |
| Swap any image | Change the `src` of the `<img>`; the layout adapts automatically. |

---

## Tech

- **HTML5**
- **CSS3** (Flexbox, Grid, custom properties, `calc()` and `min()`)
- **Font:** Gilroy (Medium, SemiBold, Bold), loaded from Swiggy's CDN

---

## Known limitations and to-do

- The carousel arrows are visual only. Without JavaScript, scroll the rows with a trackpad, mouse wheel or swipe.
- All links point to `#`, and "Show More" and the city dropdown are static.
- Images and fonts are hot-linked from Swiggy's CDN and may change or disappear.
- Small clean-ups still to do in `index.html`: the `<link>` and `<style>` tags sit outside `<head>`, and "Partener with us" is a typo.

---

## Acknowledgements

Design, brand and assets by [Swiggy](https://www.swiggy.com/). This clone was made for learning purposes only.
