---
permalink: "/why-you-wont-hear-us-say-twa/"
cover: img.jpg
title: "Why You Won’t Hear Us Say TWA"
description: "Google’s Trusted Web Activities are an important new feature that has come to Android that use Chrome Custom Tabs to present web content without browser UI. They can be used inside of a native Android app or as a wrapper for a Progressive Web App. They’re available right now in Google Chrome, and they are coming soon to Samsung Internet as well. You can read more about Trusted Web Activities on Google’s developer site. They’re a great solution for developers who want to integrate web content into their native app on Android or who want to wrap a Progressive Web App in order to submit it to the Play store. We’ve already been hearing a lot about Trusted Web Activities at events (such as Chrome Dev Summit) and many are using the acronym TWA to refer to them."
category: Web Development
img: https://miro.medium.com/max/1200/1*NbMMhcCgMoBxJ8csBx3W8Q.png
author: Daniel Appelquist
authorImg: https://miro.medium.com/fit/c/96/96/1*Imqw3OWsQ7lFIxZJw9wnSg.jpeg
tags: [Web Development, Progressive Web App, Trusted Web Activities, Mobile Browser, Samsung Internet]
---

# Why You Won’t Hear Us Say TWA

Trusted Web Activities are definitely a thing; Progressive Web Apps are more important

![An appropriate use of the acronym TWA.](https://cdn-images-1.medium.com/max/2400/1*NbMMhcCgMoBxJ8csBx3W8Q.png)*An appropriate use of the acronym TWA.*

Google’s [Trusted Web Activities](https://www.chromestatus.com/feature/4857483210260480) are an important new feature that has come to Android that use Chrome Custom Tabs to present web content without browser UI. They can be used inside of a native Android app or as a wrapper for a Progressive Web App. They’re available right now in Google Chrome, and they are coming soon to Samsung Internet as well. You can read more about Trusted Web Activities on [Google’s developer site](https://developers.google.com/web/updates/2019/02/using-twa). They’re a great solution for developers who want to integrate web content into their native app on Android or who want to wrap a Progressive Web App in order to submit it to the Play store. We’ve already been hearing a lot about Trusted Web Activities at events (such as Chrome Dev Summit) and many are using the acronym TWA to refer to them.

Meanwhile, here at Samsung Internet, we’re pretty excited about Progressive Web Apps (PWAs) which give people (across different devices, OSs and form factors) a lot of the benefits of a native application while still taking full advantage of the web platform.

Unfortunately, because “TWA” sounds a lot like “PWA,” there has been some confusion in the web developer community about what Trusted Web Activities are and how they related to Progressive Web Apps. For example, some people have wondered if Trusted Web Activities make Progressive Web Apps obsolete. Trusted Web Activities and Progressive Web Apps are two different, and complementary, things, but the similar acronyms (along with some less-than-clear messaging) has been a factor in creating this confusion.

That is one reason you won’t hear our developer advocates using the acronym TWA, unless it’s to refer to the now defunct [Trans World Airlines](https://en.wikipedia.org/wiki/Trans_World_Airlines). Also, at Samsung Internet, we also do not think Trusted Web Activities are the best way to get Progressive Web Apps onto your device. As we [announced last month](https://medium.com/samsung-internet-dev/introducing-progressive-web-apps-to-samsung-galaxy-store-47ecd317725b), we are allowing developers to directly list PWAs in our Galaxy store, which then installs the PWA directly using [WebAPK](https://developers.google.com/web/fundamentals/integration/webapks). The feedback we’ve had from developers indicates that they prefer this approach to having to wrap a PWA in a Trusted Web Activity. This wrapping also creates the possibility of a confusing user experience as the Android OS would see a Trusted-Web-Activity-wrapped PWA as a separate thing from the same PWA saved as a WebAPK (for example, via our web app installation button in the URL bar).

So, while you are going to see Trusted Web Activity support coming soon to Samsung Internet, we are going to continue to emphasize WebAPK-based install of Progressive Web Apps as we think this is the best and simplest approach for developers and for the people installing and using PWAs.



By Daniel Appelquist on December 17, 2019.

[Canonical link](https://medium.com/samsung-internet-dev/why-you-wont-hear-us-say-twa-544d51bdedec)
