# GSAP Scroll Type Study

A small study of scroll-driven typography with [GSAP](https://gsap.com) 3.13, ScrollTrigger and SplitText, built as patterns that could drop into a Shopify theme.

**Live page:** https://bcwalke7.github.io/gsap-scroll-study/

## What's in it

| Effect | Technique |
| --- | --- |
| Headline letters rise in on load | SplitText + a time-based, staggered tween, with a scrubbed exit on scroll |
| Words fill in as you read | SplitText words + a scrubbed, staggered tween |
| Letters flip while the section holds still | CSS `position: sticky` + one scrubbed timeline |
| A marquee driven by the scrollbar | Scrubbed `xPercent` on two rows |
| Cards that slide in | A `<scroll-anim>` web component that reads its motion from attributes |
| "How it's built" dropdowns | GSAP tweening `height: auto`, then `ScrollTrigger.refresh()` |

Each effect on the page includes its JavaScript, the Shopify Liquid and section schema that would drive it, and the settings a merchant would control in the theme customizer.

## Notes

- **Theme editor ready:** each section's animations live in their own `gsap.matchMedia()` context, so they are torn down on `shopify:section:unload` and rebuilt on `shopify:section:load`.
- **Reduced motion:** with `prefers-reduced-motion: reduce`, no animations are built and every section renders in a readable, static layout.
- **Fonts first:** SplitText measures text, so splitting waits for `document.fonts.ready`.
- **Accessible dropdowns:** real `<button>` elements with `aria-expanded` and `aria-controls`; closed panels are hidden from keyboard and screen readers.

The Liquid and schema are prototypes written to Shopify's section format; they have not yet been run in a live theme.

## Run it

It's a single `index.html` with no build step. Open it in a browser, or serve the folder with any static server. GSAP loads from the jsDelivr CDN.
