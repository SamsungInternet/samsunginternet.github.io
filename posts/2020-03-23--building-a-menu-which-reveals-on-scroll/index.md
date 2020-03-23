---
permalink: "/building-a-menu-which-reveals-on-scroll/"
cover: img.jpg
title: "Building a menu which reveals on scroll."
description: "I built this demo as a quick experiment when we were working on an Internal Samsung product. One feature I implemented was the menu where items reveal themselves as you scroll down."
category: Web Development
img: https://miro.medium.com/freeze/max/300/1*7qJTWPouMUzkKUYir50J2g.gif
author: Ada Rose Cannon
authorImg: https://miro.medium.com/fit/c/96/96/1*Dn8pr_cbYLtc_KfmUNhnBA.png
tags: [Web Development, CSS, HTML, JavaScript, Samsung Internet]
---

# Building a menu which reveals on scroll.

I built this demo as a quick experiment when we were working on an Internal Samsung product. One feature I implemented was the menu where items reveal themselves as you scroll down.

This is a perfect use case for IntersectionObserver, the API which tells you when things enter the screen.

You can try [this demo live on glitch](https://slide-on-scroll.glitch.me/), and I have pasted a GIF below:

![The final demo](https://cdn-images-1.medium.com/max/2000/1*4FDEnrezCUGy6kEX9UJDnQ.gif)*The final demo*

### Writing the Demo

First build the HTML and CSS, which in this case is a list:

**HTML**

    <ul>
      <li>Black</li>
      <li>Navy</li>
      <li>DarkBlue</li>
      <li>MediumBlue</li>
      <li>Blue</li>
      <li>DarkGreen</li>
      ...
    </ul>

**CSS**

    ul {
      list-style: none;
      margin: 0;
      padding: 0;
    }

    li {
      padding: 3em 1em;
      margin: 0.5em 0;
      border-radius: 1em;
      background: white;
    }

### Intersection Observer

[Intersection observer](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) works by detecting when an element enters the screen, yet these elements appear to slide in from off the right of the screen, so how does IntersectionObserver detect them?

The secret is before they are detected, they are in their final position but invisible with visibility:hidden; items with this property effect the layout of the page as usual but are not painted by the browser so are pretty efficient.

When the IntersectionObserver detects them it makes it visible and at the same time begin an animation. This animation is on the transform css property so that it slides in, transform is a very efficient property to animate compared to animating the margin-left or left property for example, so the animation is smooth even on low power devices.

We then stop the IntersectionObserver from observing them since we don not want the animation to trigger again.

### In code it looks like this,

1. first make each li invisible:

    Array.from(document.querySelectorAll('li')).forEach(li => {
      li.style.visibility = 'hidden';
    });
> **NB** It would be simpler to make them invisible in our css file **BUT **if we did that then if the JavaScript failed to load then nothing would ever be visible. It’s important so that it only becomes invisible if we know it can be revealed later.
> The techniques of building robust sites which are not broken when JS fails is known as **progressive enhancement**.

**2.** Set up the [Intersection Observer](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)

The intersection observer is set to trigger once 25% of the element has been revealed using threshold: 0.25 , it returns an array of entries which have had their amount of intersection changed, when it changes and lets us know if they are intersecting, if they are we will do something (in the next step).

    const observer = new **IntersectionObserver**(entries => entries.forEach(function onIntersection({
      **isIntersecting**,
      target
    }) {
      if (**isIntersecting**) {

        // Do something

      }
    }), {
      **threshold: 0.25**
    });

    Array.from(document.querySelectorAll('li')).forEach(li => {
      **observer.observe**(li);
    });

**3.** Make it visible, Do the animation, Stop observing:

We use the [Web Animation API](https://developer.mozilla.org/en-US/docs/Web/API/Animation) for the animation, it’s not yet supported in Safari so you can either include [the polyfill](https://github.com/web-animations/web-animations-js#quick-start) or use a fallback method such as CSS animations. Currently if we do nothing the element will just become visible then error on the animation so it will still be usable even if it is broken.

We animate the transform property which only effects compositing, it does not cause the page to be laid out or trigger repaint so is very efficient, giving us smooth animation.

    // Make it visible
    target.style.visibility = '';

    // stop observing the element
    observer.unobserve(target);

    // Do the animation with the Web Animation API
    target.animate(
      {'**transform**': ['translateX(100vw)','translateX(0)']},
      {
        easing: 'cubic-bezier(0.550, 0.055, 0.675, 0.190)',
        duration: 700,
        fill: 'forwards'
      }
    );

If you want to make an exciting reveal animation, try experimenting with using 3D transforms like rotate3d in the transform with the [perspective](https://developer.mozilla.org/en-US/docs/Web/CSS/perspective) CSS property set to get a 3D animation as it reveals.

### Final code:

I hope you found this guide handy please share if you liked it.

<iframe src="https://cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fglitch.com%2Fembed%2F%23%21%2Fembed%2Fslide-on-scroll%3FpreviewSize%3D100%26attributionHidden%3Dfalse%26sidebarCollapsed%3Dfalse%26path%3Dscript.js%26previewFirst%3Dfalse&amp;dntp=1&amp;display_name=Glitch&amp;url=https%3A%2F%2Fglitch.com%2Fembed%2F%23%21%2Fembed%2Fslide-on-scroll&amp;image=https%3A%2F%2Fglitch.com%2Fedit%2Fimages%2Flogos%2Fglitch%2Fsocial-card%402x.png&amp;key=a19fcc184b9711e1b4764040d3dc5c07&amp;type=text%2Fhtml&amp;schema=glitch" allowfullscreen frameborder="0" scrolling="no"></iframe>

![](https://cdn-images-1.medium.com/max/2000/1*7qJTWPouMUzkKUYir50J2g.gif)



By Ada Rose Cannon on March 23, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/building-a-menu-which-reveals-on-scroll-557f92909fd8)
