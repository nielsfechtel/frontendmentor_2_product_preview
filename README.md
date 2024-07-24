# Frontend Mentor - QR code component solution

Hi, Niels here.
This is a solution to the [Product preview card component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/product-preview-card-component-GO7UmttRfa). [Hosted on GH Pages](https://nielsfechtel.github.io/frontendmentor_2_product_review/).

## Table of contents

- [Frontend Mentor - QR code component solution](#frontend-mentor---qr-code-component-solution)
  - [Table of contents](#table-of-contents)
  - [Overview](#overview)
    - [Screenshot](#screenshot)
    - [What I learned](#what-i-learned)
  - [Author](#author)

## Overview

### Screenshot

![](./Screenshot.png)

### What I learned
The responsive layouting worked much better here than in the last challenge (which was the omelette-recipe-card).

I wanted to create the hover-effect by using a brightness-filter. Couldn't do that on the button itself, because that would also darken the text. I remembered a video from Kevin Powell where he talked about the idea of using a pseudo-element for a background of a button, and animating that (or darkening it, in my case).
This required using `z-index: -1` on the pseudo-element and `isolation: isolate` on the button, to create a new stacking context. As I understand it, now the button-text and the button-pseudo-element with the background can arrange themselves properly, and the background-color the container is no longer in the way.
```css
/* showing only relevant properties */
.order-button {
  position: relative;
  background-color: transparent;
  /* Create a new stacking-context separate, see z-index below */
  isolation: isolate;
}

.order-button::before {
  /* Put this element behind it's creator to serve as a darkenable (definitely a word) background */
  z-index: -1;
  position: absolute;
  inset: 0;
  content: "";
  background-color: var(--color-primary-1);
}

.order-button:hover::before {
  filter: brightness(60%);
}
```

## Author

- Website - [Niels Fechtel](https://niels-fechtel.com)
