---
permalink: "/testing-your-websites-on-real-devices/"
cover: img.jpg
title: "Testing your websites on real devices"
description: "As desktop browser developer tools improve continuously, the responsive design modes are incredibly useful for testing out designs on other screen sizes such as tablets and mobile phones. For web developers, it can be tempting to rely on these tools for full end to end development, but I want to highlight the important of testing on real devices."
category: Web Development
img: https://miro.medium.com/max/1200/1*i4G0BbzrOeUXs6XAXsGtPA.png
author: Ada Rose Cannon
authorImg: https://miro.medium.com/fit/c/96/96/1*Dn8pr_cbYLtc_KfmUNhnBA.png
tags: [Web Development, Samsung, Android, Chrome, Next Billion Users]
---

# Testing your websites on real devices

Testing your websites on real devices

### A guide to remote debugging with Samsung Internet

As desktop browser developer tools improve continuously, the *responsive design modes* are incredibly useful for testing out designs on other screen sizes such as tablets and mobile phones. For web developers, it can be tempting to rely on these tools for full end to end development, but I want to highlight the important of testing on real devices.

Real devices can often surprise you with the amount of available screen space. The browser’s chrome, the bits surrounding the screen to assist with web browsing such as URL bars and menu bars as well as the phone interfaces, will further reduce the amount of space available.

If you are lucky enough to own a Samsung Note or a Galaxy S phone or a recent iPhone you may assume that other people are using the same caliber of device as you. With lots of memory and a powerful chipset to run demanding Web Sites. Many users are not using such powerful devices

According to Google, the median device is the equivalent to a Samsung S7 from 2016. Which had 4–8 2.3Ghz processors and 4GB of RAM. Although bare in mind a web page will generally use only one of these cores and rarely at full power.

This may seem like a pretty low bar, and really not that bad a device, but this is the Median device by making this your lowest device you are excluding 50% of users!!
> # By targeting a median device like this you are already excluding 50% of users!! Ask your marketing people if they are okay with only targeting half the market.

A better device to test on would be something like the 75th or 90th percentile device.
> # My research showed the P75 worldwide to have surprisingly similar specs to the Moto G4: all A53 cores, 4–8 of them, likely 28nm process. 2GB of RAM. Older Android version.
> # — Alex Russell, Google

This device is really not very powerful, if you find testing on these devices boring because the page takes a long time to parse and render then think about how a quarter of your users are feeling!

<blockquote class="twitter-tweet" data-conversation="none" data-align="center" data-dnt="true"><p><a href="http://twitter.com/such_politics" target="_blank" title="Twitter profile for @such_politics">@such_politics</a> <a href="http://twitter.com/DasSurma" target="_blank" title="Twitter profile for @DasSurma">@DasSurma</a> <a href="http://twitter.com/jaffathecake" target="_blank" title="Twitter profile for @jaffathecake">@jaffathecake</a> As with desktop, the low end is defined by replacement. The P90 device was sold 4+ years ago. It has 512-1GB of memory and 2-4 A53 cores in the 1.1-1.4Ghz range. Memory constrains what those users can do more than anything else.</p><p>&#x200A;&#x2014;&#x200A;<a href="https://twitter.com/slightlylate/status/1230739413883187200">@slightlylate</a></p></blockquote>

Very common devices are incredibly low power, for these people many websites built with “modern frameworks” are totally unusable to people using these devices. They are a huge potential audience which developers are choosing to exclude by not testing on these low end devices.

If your metrics show you are not being used by devices which match these specs it’s likely you have already driven away these users and need to fix that ASAP.

### Getting hold of devices

* Keep your old devices, this isn’t always an option since devices break or get donated, but if you have a draw full of old phones perhaps start keeping them handy for testing on.

* Borrow your friends’ old devices, try asking ask your colleagues, it’s surprising how many old devices people keep around.

* Visit device labs, device labs can provide many different types of devices for testing on they are present in many cities.

* Set aside some of your team’s budget for buying the cheapest handsets you can get your hands on. New inexpensive devices usually have similar specs old medium spec devices.

* [Online testing tools](https://developer.samsung.com/remote-test-lab) can give you real devices to try out remotely. They aren’t ideal since there will be latency introduced by being remote, but it can be a good way to try out on newer devices with unique form factors such as the Samsung Fold.

### Setting up Remote Debugging

These instructions focus on the Web Browser, Samsung Internet (since it’s the Samsung Internet publication) but they also apply to Chrome as well.

Most mobile browsers don’t have in built inspectors but you can use Desktop Chrome to debug other mobile Chrome based browsers.

### Using a USB Cable

Requirements: Laptop, Testing Device, USB Cable which can send data.

**Step 1,** enable USB debugging

This is a little bit involved, tap on Build Number until the hidden Developer Mode is enabled, then go to developer mode to enable USB debugging.

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/2nehuCynAtc" frameborder="0" allowfullscreen></iframe></center>

**Step 2,**

Insert one end of the cable in to the device and the other end into the laptop, the phone will ask if you want to allow debugging.

![](https://cdn-images-1.medium.com/max/2160/1*Vi3n5DcwNsZGWfFlnsFr0Q.jpeg)

If your phone doesn’t present this message you may have to check a few things there are some things you can check here:
[**Chrome DevTools Devices does not detect device when plugged in**
*To get the functionality up and running: Following the above steps I got the RSA key fingerprint prompt to accept then…*stackoverflow.com](https://stackoverflow.com/a/22028058)

I had to install the Android SDK and run adb usb and put the device into image transfer mode.

**Step 3,**

On the phone open Samsung Internet (also works with Google Chrome) to the page you want to inspect.

On the desktop, open a Chromium browser (such as Chrome or Edge) and navigate to chrome://inspect. You should see a list of available web pages to debug. Press *inspect* on the page you want to debug.

![](https://cdn-images-1.medium.com/max/2000/1*GFRWjKo1kLdtk0aB6zl8bw.png)

This will open an inspector ready to debug. It will give you a live screen view of the device as you are debugging you have a terminal, full source code navigation and the ability to use break points. All of the features you would expect from developer tooling.

![DevTools running on a mobile phone.](https://cdn-images-1.medium.com/max/2532/1*i4G0BbzrOeUXs6XAXsGtPA.png)*DevTools running on a mobile phone.*

### Port forwarding

If you are running your product locally on your machine and want to share it to your device you can turn on port forwarding to forward the local http server to your device. First press the “Port forwarding…” button

![](https://cdn-images-1.medium.com/max/2000/1*eSWROsCEPpkxgIHaXbc-cQ.png)

then enter your local server details, and check “**Enable port forwarding”**

![Port forwarding settings.](https://cdn-images-1.medium.com/max/2000/1*9gFIUmAMEPIN_3FfR9Y6aw.png)*Port forwarding settings.*

The page is available on the mobile device at http://127.0.0.1:8080 replace 8080 with what ever port you are forwarding.

I hope this helps you getting your Website Working on Samsung Internet, you can find more documentation from the Samsung Internet team at:
[**Documentation**
*Documentation from the Samsung Internet team *samsunginter.net](https://samsunginter.net/docs)



By Ada Rose Cannon on February 25, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/testing-your-websites-on-real-devices-4e4f39336d7)
