---
permalink: "/progressive-web-apps-making-app-like-experiences-in-the-browser/"
cover: img.jpg
title: "Progressive Web Apps: Making app-like experiences in the browser"
description: "It was not so long ago that I used to have an old smartphone and just the idea of installing a new app was pretty annoying as I had to avoid the “insufficient disk space” message. Besides the fact that I had to buy a new phone, this was a reminder that before a developer I’m a user and there’s a lot of users out there that don’t have the latest device on the market or that cannot take a good approach of your app because for example lack of good internet connection. Having your users downloading your app and keeping them engage sometimes is not a simple task and on the other hand if you build for the web you have the advantage to reach billions of users just with a link but still have to deal with discoverability and user retention. We all agree that happy users mean happy developers (at least that’s what I like to think) so what if we can have some of the cool native app features like push notifications or icon on home screen into the browser that actually helps to gain user engagement: say hello to Progressive Web Apps!"
category: Web Development
img: https://miro.medium.com/max/886/1*NTVenCfEGAmHn-1vpssTLg.png
author: Laura Morinigo
authorImg: https://miro.medium.com/fit/c/96/96/1*rZUWIujvpL0YX4iV8KTKTg.jpeg
tags: [Web Development, Pwa, Progressive Web App, Web, Development]
---

# Progressive Web Apps: Making app-like experiences in the browser

It was not so long ago that I used to have an old smartphone and just the idea of installing a new app was pretty annoying as I had to avoid the “insufficient disk space” message. Besides the fact that I had to buy a new phone, this was a reminder that before a developer I’m a user and there’s a lot of users out there that don’t have the latest device on the market or that cannot take a good approach of your app because for example lack of good internet connection. Having your users downloading your app and keeping them engage sometimes is not a simple task and on the other hand if you build for the web you have the advantage to reach billions of users just with a link but still have to deal with discoverability and user retention. We all agree that happy users mean happy developers (at least that’s what I like to think) so what if we can have some of the cool native app features like push notifications or icon on home screen into the browser that actually helps to gain user engagement: say hello to Progressive Web Apps!

![](https://cdn-images-1.medium.com/max/2000/1*v7OiV8H0CXio6n7LOalJcQ.png)

Progressive Web Apps is a concept created by Frances Berriman and Alex Russel to describe apps taking advantage of new features supported by modern browsers that are built using including HTML, CSS, and JavaScript (yes, just web technologies ❤).

**Evolution of the browser**

I’m pretty sure that you are thinking: can I have access to my mobile hardware from the browser? Yes! Besides being able to play with services like camera and GPS most modern browsers today including *Samsung Internet* have the ability to access cool features like fingerprint and even Web-XR (coming soon).

![Web XR, WebAPK installation for PWAs, biometric sercurity for private browsing and Antitracking are some of the features provided by Samsung Internet](https://cdn-images-1.medium.com/max/2122/1*8lDyAutvfFlvqw-ljQAs4w.png)*Web XR, WebAPK installation for PWAs, biometric sercurity for private browsing and Antitracking are some of the features provided by Samsung Internet*

**Technically Talking…**

For developers building a PWA translates into including in your website:

* *HTTPS:*** **The web application must be served over a secure network. Being a secure site is not only a best practice, but it also establishes your web application as a trusted site especially if users need to make secure transactions. Most of the features related to a PWA work just with HTTPS otherwise you are gonna have problems, for example, using a service worker, the good news is that nowadays it’s pretty simple to get an SSL certificate so first things first: use HTTPS.

* [*Service Worker](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorker):* A service worker is a script that allows intercepting and control of how a web browser handles its network requests and asset caching. With service workers, web developers can create reliably fast web pages and offline experiences.

* [*Manifest File](https://developer.mozilla.org/en-US/docs/Web/Manifest)*: It is a JSON file that controls how your app appears to the user and ensures that progressive web apps are discoverable. It describes the name of the app, the start URL, icons, and all of the other details necessary to transform the website into an app-like format. On Samsung phones we also support[ installing PWAs using WebAPK](https://medium.com/samsung-internet-dev/new-year-new-samsung-internet-b74f282e4429) which gives an even more seamless app-like experience.

For example here is [Pigment](https://samsunginternet-pigment.glitch.me/), a Progressive Web App created by Samsung Internet that works as a color conversion between Hexa, HSL, RGB, and CMYK and even works offline. The first time that you visit the website you will find the install button just beside the URL. After installing you will be able to see the icon on your home screen just like a native app!

![](https://cdn-images-1.medium.com/max/2000/1*NTVenCfEGAmHn-1vpssTLg.png)

**So should I build a PWA?**

* *If you already have a native app***:** it doesn’t mean that it is gonna be replaced, you are adding a multiplatform experience with the ability to access from the desktop as much users do. There are a few examples in the market like Pinterest or Tinder that after building a PWA the amount of user revenue and performance has increased considerably without much cost. If you want to check more statistics related to PWA, check [pwastats.com](https://www.pwastats.com/).

* *If your product already has a website: *Definitely yes! Besides adding app-like capabilities to increase user engagement like push notifications, most of the features described previously are best practices for the web, using https to ensure security and trusted experience to the user, cache the right files in order to improve performance or set the right start url / icons into the manifest file should be as priorities.

**What’s next?**

These are exciting times for the web and we are hoping to see more cool PWAs out there. In order to help developers win more discoverability, Samsung recently announced the ability to publish [PWAs into the Galaxy Store](https://medium.com/samsung-internet-dev/introducing-progressive-web-apps-to-samsung-galaxy-store-47ecd317725b),

If you already have a PWA and are interested to publish it into the store or have any feedback about what would you like to see, reach out at [pwasupport@samsung.com](mailto:pwasupport@samsung.com).

**Time to create!**

There will be more details about PWAs in future articles but if you want to start this journey with us take a look into our codelab: [Create your first PWA](https://glitch.com/~samsunginternet-pigment-starterkit) and show us what you build!



By Laura Morinigo on November 26, 2019.

[Canonical link](https://medium.com/samsung-internet-dev/progressive-web-apps-making-app-like-experiences-in-the-browser-a15bd388963b)
