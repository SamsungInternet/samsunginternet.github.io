---
permalink: "/pwa-series-service-workers-the-basics-about-offline/"
cover: img.jpg
title: "PWA Series: Service Workers, the basics about offline"
description: "[ Version en español aquí ]"
category: Pwa
img: https://miro.medium.com/max/1200/1*pM4aOxnAalcSMSQS33JcYA.jpeg
author: Laura Morinigo
authorImg: https://miro.medium.com/fit/c/96/96/1*rZUWIujvpL0YX4iV8KTKTg.jpeg
tags: [Pwa, Progressive Web App, Web Development, Web, Service Worker]
---

# PWA Series: Service Workers, the basics about offline

[ Version en español aquí ]

In previous articles, we’ve been talking about what a [Progressive Web App](https://medium.com/samsung-internet-dev/progressive-web-apps-making-app-like-experiences-in-the-browser-a15bd388963b) is and the features needed to make a PWA: HTTPS, [a manifest file](https://medium.com/samsung-internet-dev/pwa-series-the-manifest-file-cheatsheet-459b4a5e2098), and service workers.

![](https://cdn-images-1.medium.com/max/6688/1*pM4aOxnAalcSMSQS33JcYA.jpeg)

### The offline experience

Even though devices and apps are designed to use them online with a fast network, we should not be surprised to find out that usually, this is not the common scenario. Taking a flight, arriving at a place with a bad connection or just taking the underground can take the user offline and don’t forget that we’ve all been in the situation where data is metered for your mobile device. Having access to a fast and reliable web app should be a priority for users regardless of the quality of our network. There are many different strategies that we can use to improve this experience and service workers play a huge role in this.

Before we start going through some definitions around service workers, remember that FIRST, we need to apply HTTPS to our website (even though for the purpose of testing localhost count as a secure context).

Besides making sure that our app is secure and trusted for the users, having HTTPS allows your website to have access to many modern browser features like geolocation, payment and *service workers*.

## So what is a service worker?

A service worker is a script written in javascript that allows intercepting and control of network requests and asset caching from the web browser. With service workers, web developers can create reliably fast web pages and offline experiences. It’s a browser feature but it doesn't have access to the DOM, its role is different than a normal JS script.

As service Workers have access to manage network requests, they can be very powerful, especially if used maliciously by an attacker, allowing things like script injection or replacing the whole site. This is why HTTPS is so important here, in order to prevent third parties from injecting them into your website.

## How can I implement a service worker?

To install a service worker we have some steps to follow:

**1- Register**

Before installing, the browser should check if the service worker already exists, in order to do this we called the process of “registration”.

Add this script into the head of your HTML:



Let’s review this, the very first part check if a property called serviceworker that belongs to the object navigator exists, if yes, it means there’s no need to register as it’s already there. Otherwise, we can call the method register that will call our service worker. As you can see, it’s calling a file with the name “serviceworker.js” that contains the code to install and manage the functionality of your service worker.

**2- Install**

In our service worker script file called “serviceworker.js” let’s implement the rest of the functionality.

The very first event is *install, *here we are going to tell which files are going to be cached, the content you add to the “urlsToCache” will be added immediately to the cache and service from the cache whenever a page requests it.




**3- Fetch**

Now you’ve got your site files cached, these files can be images, scripts or whatever you feel it’s important to manage offline. There are different cache strategies for choosing whether to load them or go to the network. We should choose carefully and be responsible to manage which files we are going to be stored offline at once as resources are limited.

Once you have cached resources, you need to tell service workers to manage and do something with that content. There’s an event called *fetch *that allows you to do this.

A fetch event runs every time any document in the scope of a service worker is fetched, such as when a page is loaded or when a resource like a script or an image is added or an API call is made. You can attach a fetch event listener to the service worker, then call the respondWith() method on the event to manage your HTTP responses and do something with it, like showing an offline message.

The example below is a simple cache strategy, if we have already cached the resource, it will be returned from the cache immediately, otherwise, we will get it from the network. This works great for static content but if we have dynamic content, it will never be updated.



**4- Activate**

You need to be able to manage your cached resources, for example, old files that don't exist anymore or include new files. You can do this with the *activate *event. In the following code, you can see a basic way of how to make this work, the browser will check if these resources are in the previous cache list, if they don’t exist anymore it will remove them. This is good maintenance to do as browsers have a complex relationship with storage space for resources.




## You’ve created your first service worker!

These are the basic steps to create a service worker and start playing around the capability of offline requirements. There are many different tools to make these steps easier, for example, with [PWA builder](https://www.pwabuilder.com/) you can even choose a service worker template, set up parameters and then download the script.

There are different caching strategies to review, besides start learning the lifecycle of a service worker, as we have so many topics to discuss we are going to approach more lessons in the next PWA series! In the meantime, you can check [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) to learn more about this topic. **Stay tuned… **🤓

## Team Announcement!!

If you like to learn more about PWA or if you are in the tech space and want to share something with us, we have exciting news! We are doing virtual office hours with Samsung Internet as a way to keep social (online) interaction, keep talking about web and cool stuff around. Check our new [meetup page](https://www.meetup.com/Samsung-Internet-Meetup/) to see our next events!

And if you have something cool that you are working on (especially around the web), we are looking for you as a special guest!!! We made[ this form](https://docs.google.com/forms/d/e/1FAIpQLScV-hhmM2MGVP2WIij5WlArxic6KEl9sYnBkHf21oNXEIUjxA/viewform) if you like to participate! Every virtual office hour is an opportunity to reach an audience from all around the world and learn from each other. Let’s keep connected (virtually) 💪🏽



By Laura Morinigo on April 3, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/pwa-series-service-workers-the-basics-about-offline-a6e8f1d92dfd)
