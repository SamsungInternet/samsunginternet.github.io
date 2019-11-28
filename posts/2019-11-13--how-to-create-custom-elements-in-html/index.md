---
permalink: "/how-to-create-custom-elements-in-html/"
cover: img.jpg
title: "How to Create Custom Elements in HTML"
description: "Editor’s note: with this post, we’re welcoming the latest member of our team, Kevin Picchi. Welcome, Kevin! –Daniel Appelquist"
category: Web Development
img: https://miro.medium.com/max/900/1*qIDU1Mk5PtUvvGA15u8J6g.png
author: Kevin Picchi
authorImg: https://miro.medium.com/fit/c/96/96/2*bxiHyDC_olykuiudnMZ3Sg.png
tags: [Web Development, Custom Elements, Web Components]
---

# How to Create Custom Elements in HTML

Have you ever thought “I wish there were a HTML tag for that”? Well now you can.

*Editor’s note: with this post, we’re welcoming the latest member of our team, Kevin Picchi. Welcome, Kevin! –[Daniel Appelquist](undefined)*

![](https://cdn-images-1.medium.com/max/2000/1*qIDU1Mk5PtUvvGA15u8J6g.png)

### What Are custom elements ?

Custom Elements are a way to allow developers to create their own fully-featured HTML tag in the DOM (Document Object Model).

By using this API the developer can let the browser parser know how to properly build an element and how elements of the class must respond to changes.

With the help of Custom Elements you can make your code more readable by creating elements specific to your needs.

Custom Elements have been introduced in HTML 5 DOM specification by the W3C, here is what the specification states:
> Custom elements are part of a larger effort to “rationalise the platform”, by explaining existing platform features in terms of lower-level author-exposed extensibility points.
[https://html.spec.whatwg.org/multipage/custom-elements.html](https://html.spec.whatwg.org/multipage/custom-elements.html#custom-elements)

### What do I need ?

To create our custom element we will only need some HTML, JavaScript and CSS. We are also going to use the JavaScript APIs of Custom Element, that will allow us to define custom element and their behaviours.

I’ll tell you more about this later in that post.

### How to use it ?

Here is a step by step tutorial, that will show you how to create your first custom element. For the sake of the example shown bellow I’ve decided to show you how this very simple QuoteComponent works.

The goal of this component is to simply show a italic centered quote and the name of the author in two separated lines.

## Lets get started:

### Step 1:

First we have to define what our Custom Element will be about.
Below is the code that I want to use as a Custom Element, you can easily guess the part that I’d like to have as variables. For instance, the text inside the first and second span.

The first one is the quote (the spam with the italic class), and the second one is the author name.



This is absolutely not mandatory but here is a bit of CSS to make it look better:



### Step 2:

Now that everything looks pretty, we are going to initialize our element in JavaScript.

To do that we are going to use the JavaScript APIs of Custom Elements.
More specifically we will have to define our Custom Element using the **HTMLElement** interface, this is also the interface that is used to define other HTML tags classes. ( Example: HTMLSpanElement, HTMLImageElement, HTMLDivElement and many more.)

So I created a new class named **QuoteComponent** extended from the **HTMLElement** class.

Now we want to get/observe the values from the attributes that we set.
This is done by specifying a static get observedAttributes() method inside our class. This one should return an array containing the names of the attributes you want to be able to get/observe.

Now that the values are observable we can create a get author() method and returning the value of the attribute by using this.getAttribute('author')so we can access it more easily in our code.
I also did the same for the quote attribute.

Finally we need a render method that will define the innerHTML of our component.



Lastly, we register our custom element on the CustomElementRegistry using the define() method.

In the parameters we specify the element name, and then the class name that defines its functionality.



### Step 3 :

Last step add it to the HTML of your project:



And Voilà, you just created a “*cool*” Custom Element that you can show to all your friends.

### Browser support

![[As of 12.11.2019 — Source: https://caniuse.com/#feat=mdn-api_customelementregistry](https://caniuse.com/#feat=mdn-api_customelementregistry)](https://cdn-images-1.medium.com/max/3044/1*W4G2hqdvMV32nfquCCSI0w.png)*[As of 12.11.2019 — Source: https://caniuse.com/#feat=mdn-api_customelementregistry](https://caniuse.com/#feat=mdn-api_customelementregistry)*

As you can see on the graph above, not all of the browser are currently supporting custom elements. That’s why I recommend using a pollyfill to make sure that everyone can enjoy the benefits: [https://github.com/webcomponents/polyfills/tree/master/packages/custom-elements](https://github.com/webcomponents/polyfills/tree/master/packages/custom-elements)

### Sources:

* [https://html.spec.whatwg.org/multipage/custom-elements.html](https://html.spec.whatwg.org/multipage/custom-elements.html#custom-elements)

* [https://developer.mozilla.org/en-US/docs/Web/API/CustomElementRegistry](https://developer.mozilla.org/en-US/docs/Web/API/CustomElementRegistry)

* [https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements)

* [https://caniuse.com/#feat=mdn-api_customelementregistry](https://caniuse.com/#feat=mdn-api_customelementregistry)



By Kevin Picchi on November 13, 2019.

[Canonical link](https://medium.com/samsung-internet-dev/how-to-create-custom-elements-in-html-ae8d5a834eb2)
