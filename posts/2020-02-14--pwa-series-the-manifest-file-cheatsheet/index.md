---
permalink: "/pwa-series-the-manifest-file-cheatsheet/"
cover: img.jpg
title: "PWA series: the manifest file cheatsheet"
description: "We already introduced you to the concept of Progressive Web Apps: a way to bring a native-app like experience into the browser. The technical definition says that in order to call a website a PWA we need three different features: HTTPS, a service worker, and a manifest file. Let’s go deeper into the manifest file… 🕵️‍♀️"
category: Pwa
img: https://miro.medium.com/max/1000/1*P-gXz7UCnyazZQHhy43ApQ.png
author: Laura Morinigo
authorImg: https://miro.medium.com/fit/c/96/96/1*rZUWIujvpL0YX4iV8KTKTg.jpeg
tags: [Pwa, Progressive Web App, Web Development, Web, JavaScript]
---

# PWA series: the manifest file cheatsheet



We already introduced you to the concept of [Progressive Web Apps](https://medium.com/samsung-internet-dev/progressive-web-apps-making-app-like-experiences-in-the-browser-a15bd388963b): a way to bring a native-app like experience into the browser. The technical definition says that in order to call a website a PWA we need three different features: HTTPS, a service worker, and a manifest file. Let’s go deeper into the manifest file… 🕵️‍♀️

## **What is a Manifest File?**

It’s just a JSON file with values like the name of the app or the start URL. These values called members, define how your app appears to the user including the details to make a PWA look with a similar style of an app (the homescreen icon for example) and ensures that it’s discoverable.

## 👉Cheatsheet

The basic manifest file consists of just the following members: name, short-name, description, and icon. Here we show one more advanced type in order to cover different topics and explain each value. There are more advanced fields that you can include, to explore a little bit more you can check the [MDN](https://developer.mozilla.org/en-US/docs/Web/Manifest) website.

Save this article when you need some help trying to remember which fields you need for your web-app.

    {
       **"name"**: can be used by app stores or browsers on startup screens      and prompts.
       **"short-name"**: used to display the name to the user within the icon. For example: in the homescreen.
       **"description"**: provides additional context about the app.
       **"dir"**: Direction of the text. 
              Values: ltr(left to right),
                      rtl (right to left),
                      auto
      ** "lang"**: Language of the text. 
               Example: en (English)
       **"icons"**: Array of icons that the browser can choose from, including size and type.
               [{
                 **"src"**: source,
                 **"sizes"**: i.e. "192x192",
                 **"type"**: i.e. "image/png",
                 **"purpose": **the purpose of the image in the context of the host OS.
                           Values: badge, maskable, any
                }]
        **"display": **Preferred display mode for the website.
                   Values: fullscreen,
                           standalone,
                           minimal-ui,
                           browser.
        **"scope": **it represents the set of urls that can be viewed through the installable web context, if the user navigates outside this scope, those pages will be opened in a standard browser.
                 Example:"https://example.com/", "/app/"

    **    "orientation": **you can enforce the orientation of your app, it can be ommited.
                       Example: natural (default).
        **"background_color": **tells the browser what color to use on the startup splash screen that users will see when they launch your app.
                            Example: "#456BD9"
        **"theme_color": **is used by some browsers to tint the status bar, address bar, and other parts of the browser user interface.
        **"start_url": **indicates what page should launch when someone opens your progressive web app.
        **"categories"**: This is intended to be used by app stores to categorize your app.
                      Example: ["business", "technology", "web"]

    }

## How to create a manifest file.

We can create our manifest file manually with the proper JSON format, then we should link this file into our app. We do this by adding a link element inside the head of the HTML file with an absolute path:

    <link rel=”manifest” href=”/appmanifest.webmanifest”>

You probably noticed that even though we are working with a JSON file the recommended extension is .webmanifest as some web servers recognize this extension and transfer the file using the standardized [MIME type for a manifest](https://w3c.github.io/manifest/#dfn-mime-type-for-a-manifest).

There are third parties apps like [PWAbuilder ](https://www.pwabuilder.com/generate)that allows you to create a manifest file easily completing the right values and even help you to check the right size of your icons.

## Manifest File and Standards

It’s important to take time testing your manifest file: icons/home screens and other values provided in the manifest can generate different results depending on the browser. In order to simplify efforts for developers, the [W3C ](https://www.w3.org/TR/appmanifest/)is working on standards to improve this experience and be more clear about which fields you need to add and also studying new values that can help to deploy your PWA easier.

You can see the current status, examples and more details[ here!](https://www.w3.org/TR/appmanifest/)

See you in the next PWA Series! 💪

## 📢 And here some announcements from the team:

* The first [PWA Conf ](https://javascript-conference.com/london/pwaconf/)is happening and is coming to London on Apr 19th, see you there!💥

* Do you have a PWA or you would like to make a PWA and [publish it into the Galaxy Store? ](https://medium.com/samsung-internet-dev/introducing-progressive-web-apps-to-samsung-galaxy-store-47ecd317725b)We want to hear from you!



By Laura Morinigo on February 14, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/pwa-series-the-manifest-file-cheatsheet-459b4a5e2098)
