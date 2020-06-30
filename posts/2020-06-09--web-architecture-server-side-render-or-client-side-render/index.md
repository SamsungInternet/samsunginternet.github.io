---
permalink: "/web-architecture-server-side-render-or-client-side-render/"
cover: img.jpg
title: "Web Architecture: Server-Side Render or Client Side Render?"
description: "Every time that we have to put our hands working in a new app, before starting to code there are a few things that we have to decide. Which technology is the best option, what design patterns, check user requirements, and in times like these, which of the 10000 JavaScript frameworks suits best for our app? This can be fun while we analyze which are the final results that we want to deliver to the user. When it’s time to make decisions around the web, we have to keep in mind its evolution and how currently we have more options to build web apps like the way we can render a website, whether it is client-side render or server-side render."
category: Web Development
img: https://miro.medium.com/max/1200/1*MoEYq4rtAyhIJWgkl3CZxQ.jpeg
author: Laura Morinigo
authorImg: https://miro.medium.com/fit/c/96/96/1*rZUWIujvpL0YX4iV8KTKTg.jpeg
tags: [Web Development, Web Architecture, JavaScript, Software Development]
---

# Web Architecture: Server-Side Render or Client Side Render?

(building in construction)

Every time that we have to put our hands working in a new app, before starting to code there are a few things that we have to decide. Which technology is the best option, what design patterns, check user requirements, and in times like these, which of the 10000 JavaScript frameworks suits best for our app? This can be fun while we analyze which are the final results that we want to deliver to the user. When it’s time to make decisions around the web, we have to keep in mind its evolution and how currently we have more options to build web apps like the way we can render a website, whether it is client-side render or server-side render.

## A brief of history

Remember those golden times where Jquery was the place to go? (If not, I suggest to take a look at one of the 10 years old JavaScript library survivor.) Well, during those times the web was a place to show information, most of the time, web pages were static content without the chance to be more interactive for the user. Later on, with libraries like Jquery, a certain level of interactivity was added but the way that a website was rendered was loading your HTML pages on the server-side. Over the past years, the addition of the new JavaScript frameworks and libraries like React and Angular made the creation of dynamic content possible, and with this the chance to use client-side rendering. For example, modern web sites usually load your index.html, then your assets, and later your javascript files. There is something related to this and is called [Critical Path](https://developer.mozilla.org/en-US/docs/Web/Performance/Critical_rendering_path): the process of delivering the most important pieces of content to the browser so it can render your page. Optimizing the critical render path improves render performance, but let’s see each option to render your website first.

## Server Side Render (SSR)

With SSR, the website is fully rendered on the server. This was the usual way to go and this is how technologies like PHP, WordPress, or Node currently work. Every time that the website loads, the entire page is requested by the browser to the server. The first load can be fast but overall so you forget about the famous initial load spinner, anyway as you have to make a lot of full load requests, performance can be affected. It’s a good approach for a website with a lot of static content. If you work with JavaScript, Node has also the chance to use [template engines ](https://expressjs.com/en/guide/using-template-engines.html)so you can use static template files in your application. At runtime, the template engine replaces variables in a template file with actual values and transforms the template into an HTML file sent to the client. This approach makes it easier to design an HTML page, everything from the server, a good way to start playing around this is with [PugJS](https://pugjs.org/api/getting-started.html).

## Client-Side Render (CSR)

Client-side rendering (CSR) allows the website to be updated in the browser when navigating to different pages the content is rendered by the client-side (browser). This method requires an initial download hit and effort to load every resource as it’s doing a lot of round trips to the server, therefore the first visit to the webpage can be slower even though after the first load, this turns faster. You have to keep in mind the Javascript SEO that can be affected too, I suggest to take a look at this really [good article](https://medium.com/@benjburkholder/javascript-seo-server-side-rendering-vs-client-side-rendering-bc06b8ca2383) by [Benjamin Burkholder](undefined).

## A combination of both worlds

Good news! If you are thinking if there’s a way to use both depending on your solution, yes! You can mix SSR with CSR, and if you keep in mind a good cache strategy, like render the first time on the server and cache its content so later you leave the rest for the client-side render you can improve your performance. This can be seen using the ‘app shell’ architecture where the website loads a minimal user interface as soon as possible and then uses the cache to make the content available offline next time the user visits the page. This is a common concept applied to Progressive Web Apps.

As usual, one solution doesn’t fit all. It’s important to check which kind of data you need to retrieve and listen to your main boss: the user!



By Laura Morinigo on June 9, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/web-architecture-server-side-render-or-client-side-render-f16b61cd6299)
