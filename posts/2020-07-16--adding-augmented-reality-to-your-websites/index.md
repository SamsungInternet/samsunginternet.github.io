---
permalink: "/adding-augmented-reality-to-your-websites/"
cover: img.jpg
title: "Adding Augmented Reality to your Websites"
description: "Last week we told you about our latest Beta, 12.1, which offers a host of quality-of-life improvements for end users. We’re also really glad to announce that with this beta we are also shipping modules for the WebXR Device API that enable Augmented Reality (AR) content to be built right in the browser: including the “hit test” module. Hit testing allows you to detect the position of the real world at a single point on the screen which can be used correctly position virtual objects in the real world."
category: Webxr
img: https://miro.medium.com/max/1200/1*MFpA5cjyCTdwAQF-QK3B-g.png
author: Ada Rose Cannon
authorImg: https://miro.medium.com/fit/c/96/96/1*Dn8pr_cbYLtc_KfmUNhnBA.png
tags: [Webxr, Augmented Reality, Samsung Internet, Mobile Web, Web Development]
---

# Adding Augmented Reality to your Websites

Adding Augmented Reality to your Websites

### Samsung Internet 12.1 Beta adds support for Augmented Reality — here’s how to try it out today

Last week we [told you about our latest Beta](https://medium.com/samsung-internet-dev/samsung-internet-12-1-f5dbff60ec41?source=collection_home---4------0-----------------------), 12.1, which offers a host of quality-of-life improvements for end users. We’re also really glad to announce that with this beta we are also shipping modules for the [WebXR Device API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) that enable Augmented Reality (AR) content to be built right in the browser: including the “[hit test](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API/Targeting)” module. Hit testing allows you to detect the position of the real world at a single point on the screen which can be used correctly position virtual objects in the real world.

One of the reasons we’re especially excited about this is because Samsung Internet have been playing a leadership role in developing the [WebXR spec](https://www.w3.org/TR/webxr/) [in W3C](https://www.w3.org/immersive-web/), along with [many other companies and organizations](https://www.w3.org/groups/wg/immersive-web/participants).

You can try AR out for yourself using the XR Dinosaurs demo to place a dinosaur in your environment:

**Step 1.** Download the Samsung Internet Beta from the Play Store or the Galaxy Store: [https://galaxy.store/internetbeta](https://galaxy.store/internetbeta)

**Step 2.** Go to [https://xrdinosaurs.com](https://xrdinosaurs.com) and choose Augmented Reality

![Accept AR Notification](https://cdn-images-1.medium.com/max/2160/1*D-NA5joGoArlOnzhW_7_ww.jpeg)

When you run this demo you will see this message, this means that the demo is able to place the virtual objects onto your environment but it cannot actually record the camera feed so you don’t have to worry about it recording what you are doing.

**Step 3.** Select a place on the floor to place the dinosaur

![XR Dinosaurs was built by [Brandon Jones (Tojiro)](https://twitter.com/tojiro) using THREE.js.](https://cdn-images-1.medium.com/max/2000/1*uKvPUe6WKQQ0JtIejnXNvw.gif)*XR Dinosaurs was built by [Brandon Jones (Tojiro)](https://twitter.com/tojiro) using THREE.js.*

### Making your own AR Web Sites

This method of AR uses the Augmented Reality features of the [WebXR Device API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API).

Here is a sample project you can use to help you get started:
> [**A-Frame Hit Test Demo**
*Remix to make your own augmented reality scenes.* hit-test.glitch.me](https://hit-test.glitch.me/?1)

![Snapshot of the scene](https://cdn-images-1.medium.com/max/2000/0*sifSVby1YajqDB_3)*Snapshot of the scene*

To make your own press the fish button then the remix on glitch button:

![How to remix the app](https://cdn-images-1.medium.com/max/2000/1*9A0ZSl7pU-wVptkXThl1fg.png)*How to remix the app*

It shows a 3D object and some basic shapes around and lets the user reposition them as they need. You can then add interactivity or other models and 3D shapes to the scene.

Once the user enters VR a Reticle is used to select the location to place the objects. The hit-test API casts ray out from the center of the screen and works out that real world position and places the reticle there.

Once the user taps the screen it then places the objects in the scene.

If you want to hide an object in AR at the hide-in-ar-mode attribute. It will make objects in visible when AR gets turned on.

In the demo this has been done for the ‘a-sky’ element and the ‘world’ element. The world element contains the objects. When the user enters AR we make it invisible so it’s not floating in the air, we make it visible again once the user has selected the location.

I hope this helps you have fun adding Augmented Reality to your Websites. Please send us your feedback and let us know if you have any questions, either via [Twitter](https://twitter.com/SamsungInternet) or on [our developer forum](https://forum.developer.samsung.com/c/samsung-internet/25).



By Ada Rose Cannon on July 16, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/adding-augmented-reality-to-your-websites-236cb3257c7a)
