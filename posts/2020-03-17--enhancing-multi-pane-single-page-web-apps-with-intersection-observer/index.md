---
permalink: "/enhancing-multi-pane-single-page-web-apps-with-intersection-observer/"
cover: img.jpg
title: "Enhancing Multi Pane, Single Page Web Apps with Intersection Observer"
description: "In the previous article we built a magazine style page layout of horizontal scrolling panes using only CSS and HTML, link to the demo. This works really well and is great experience with touch and mouse."
category: CSS
img: https://miro.medium.com/max/1081/1*3J1hHOWCD9Q_adAndvuOnQ.png
author: Ada Rose Cannon
authorImg: https://miro.medium.com/fit/c/96/96/1*Dn8pr_cbYLtc_KfmUNhnBA.png
tags: [CSS, HTML, JavaScript, Web Development, Samsung Internet]
---

# Enhancing Multi Pane, Single Page Web Apps with Intersection Observer

Using IntersectionObserver and history APIs

In the previous article we built a magazine style page layout of horizontal scrolling panes using only CSS and HTML, [link to the demo](https://pink-paper.glitch.me/#article1). This works really well and is great experience with touch and mouse.
[**Horizontally Scrolling Panes with clean HTML and modern CSS**
*This used to be a really hard problem, new CSS tools make it simpler. Here’s how it works…*medium.com](https://medium.com/samsung-internet-dev/horizontally-scrolling-panes-with-clean-html-and-modern-css-7372596932c7)

There are some improvements we can make by being aware of what the user is currently looking at. The two which are most important are displaying what article is currently in view in the navigation element ( <nav> ) and ensuring that the history is correctly updated so that the back and forward buttons work.

![3 Pane Layout](https://cdn-images-1.medium.com/max/2162/1*3J1hHOWCD9Q_adAndvuOnQ.png)*3 Pane Layout*

### Updating the Nav on Scroll

![Navigation Bar with ‘Article 2’ highlighted.](https://cdn-images-1.medium.com/max/2512/1*bCKlPZ3imXnVKr_Nkm4o5A.png)*Navigation Bar with ‘Article 2’ highlighted.*

We will need to do this in JavaScript, to be aware of what is currently in view we will use the [IntersectionObserver](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) API this is a JavaScript API which runs a callback when an observed element is scrolled into view in a root element.

    function callback(entries) {
      for (const entry of entries) {
        console.log(
          entry.target,
          entry.isIntersecting,
          entry.intersectionRatio
        );
      }
    }

    const myIntersectionObserver = new IntersectionObserver(callback, {
        root: document.querySelector('main'),
        threshold: 0.5
    });

    myIntersectionObserver.observe(someEl);

The threshold option lets you set when and how frequently the callback function is called. I’ve set it to 0.5 so it tells us whenever a pane becomes more than half visible or goes below half visible. For finer feedback you can use an array of entries. e.g. [0,0.33,0.66,1] will tell you when it has started becoming visible, two intermediate points and when it has become fully visible so that you can respond appropriately.

For our example we just need to know if it is more than half Intersecting the viewport so 0.5 works great for us. When an element is more than half visible we will highlight the appropriate link in the navigation by giving it the focus class.

    function callback(entries) {
      for (const entry of entries) {

        if (entry.isIntersecting && entry.intersectionRatio > 0.5) {
            const hash = '#' + entry.target.id;
            const navEl = document.querySelector(`a[href="${hash}"]`);
            navEl.classList.add('focus');
        } else {
            navEl.classList.remove('focus');
        }

      }
    }

### Updating the [History](https://developer.mozilla.org/en-US/docs/Web/API/History) on Scroll

The links in the header [use links with fragment URLs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a#Linking_to_an_element_on_the_same_page) for mouse control, which are internal links to other parts of the document e.g. <a href="#part2"></a> which links to an element with the id of "part2".

This has the added benefit of when the user refreshes the page or shares the URL it takes them to the last item they looked at because it’s stored in the the URL’s hash. Clicking on one of these links will push a new entry to the history stack and update the URL. Which is the exact behaviour we want.

Now we need to add this behaviour to swiping as well. To update the URL we will use:

    history.pushState({}, window.title, hash);

We can call this function from inside out IntersectionObserver when we would add the class but we shouldn’t use it directly.

Unlike doing window.location.hash = hash; this won’t trigger any scrolling so it won’t clash with the scrolling the user is already doing.

We will also need to check to make sure that we are not storing the same hash multiple times in a row since the user may scroll out of a pane and back in quickly. Clicking a link will the scroll the page triggering this behaviour, but it also adds an item to the history anyway. so we don’t want an entry being added twice by clicking the link by discarding duplicates we avoid this:

    if (window.location.hash !== hash) {
      history.pushState({}, window.title, hash);
    }

The user may choose to rapidly flick through lots of articles without stopping to read them, we don’t want to add every single entry to the history stack.

The smooth scrolling behaviour will gently pan the between the pages firing the intersection observer on each one! Adding each intermediate article to the history stack would also be not what the user expected.

So we will move this into a function and throttle it to run after a second if nothing has since called it again.

    function updateHistory(hash) {
      clearTimeout(updateHistory.timeout);
      updateHistory.timeout = setTimeout(function () {
        if (window.location.hash !== hash) {
          history.pushState({}, window.title, hash);
        }
      }, 1000);
    }

This now behaves as expected, if you rapidly swipe between panes nothing happens but when you settle on an article the URL will update.

### Adding the expected forward/back button behaviour

Pressing forward and back to change page is expected behaviour in the web, and pressing back to go back is expected behaviour in apps/web-apps.

Links with fragment URLs , like we are using, don’t have this behaviour. Pressing forward or back after clicking some links like these will not scroll the page it will only change the URL.

To implement this behaviour, we can listen for the URL hash changing and find the correct article element which is in the according to the hash part of the URL something like #article2, then we use el.scrollIntoView() to scroll it into view:

    window.addEventListener('hashchange', function (e) {

      const articleToShow =
        document.querySelector(window.location.hash) ||
        document.querySelector('article');

      articleToShow.scrollIntoView();

      e.preventDefault();
    }, false);

Now pressing forward and back will move between the panes we were last looking at whether we got there by swiping or clicking on links.

### Progressive Enhancement

The nice thing about the way this project works is that because the core functionality was written with CSS and HTML, they will always work.

The features we have added today are *Progressive Enhancements:* they improve usability and give a better experience, but should the JavaScript fail to load, or the JavaScript we’ve written doesn’t work in the users’ browser, the core experience will still work. This takes advantage of the robust nature of CSS and HTML.

Unfortunately in the demo I made the article content is also loaded by some clientside JavaScript to keep the HTML easy to read so is a poor example of progressive enhancement.

I hope you give IntersectionObserver a go as it’s really powerful and a great way to performantly respond to the user’s scrolling.



By Ada Rose Cannon on March 17, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/enhancing-multi-pane-single-page-web-apps-with-intersection-observer-5929e2c0c6b)
