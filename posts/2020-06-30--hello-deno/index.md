---
permalink: "/hello-deno/"
cover: img.jpg
title: "Hello Deno!"
description: "It’s been a while since we last heard any huge game changing news around Javascript or even new frameworks or libraries around (well maybe two days…) but recently the Javascript community is excited about a new way of working: Deno!"
category: Web Development
img: https://miro.medium.com/max/1200/1*FAR2HAOsTukGu4BrI1Lkew.jpeg
author: Laura Morinigo
authorImg: https://miro.medium.com/fit/c/96/96/1*rZUWIujvpL0YX4iV8KTKTg.jpeg
tags: [Deno, Web Development, JavaScript, Javascript Development, Nodejs]
---

# Hello Deno!

A first look at this new “secure runtime for JavaScript and TypeScript” and how it differs from Node.js

![](https://cdn-images-1.medium.com/max/4000/1*FAR2HAOsTukGu4BrI1Lkew.jpeg)

It’s been a while since we last heard any huge game changing news around Javascript or even new frameworks or libraries around (well maybe two days…) but recently the Javascript community is excited about a new way of working: Deno!

## What is it?

[Deno](https://deno.land) is a runtime for JavaScript and TypeScript that uses V8 and is built in Rust. It’s designed to replace Node to let you write code to run on the server.
> Fun fact! Deno is an anagram of node.

## Behind the scenes

Deno originates from Ryan Dahl, the creator of NodeJS. This is one of the reasons why there is so much expectation around the Deno project. Dahl announced Deno during JSConfEu during his talk “[10 things I regret about Node.js](https://www.youtube.com/watch?v=M3BM9TB-8yA&vl=en)” focusing on his choices of not using [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) in [API](https://en.wikipedia.org/wiki/API) design and explaining how some decisions around the architecture of Node.js could be better.At the end of the talk announcing the first prototype of Deno with the promise to build a better, more secure runtime environment.

## Run Environment, hello world and goodbye package.json!

After installing Deno, let’s create our first “hello world” app.

First create a file called index.ts, we are using Typescript as Deno handles it natively, so we get all the benefits of typescript without the extra overhead. Installing the Deno extension in your favorite editor automatically sets up the correct typescript configuration.

```javascript

import { serve } from "https://deno.land/std@0.59.0/http/server.ts";

const s = serve({ port: 8000 });

for await (const req of s) {

    req.respond({ body: "Hello World\n" });

}
```

If you are used to node you may be familiar with using require() to import modules. Deno uses [ES Module import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) statements just like you would use in a web browser. So there is no node_modules folder or a package.json!

Deno has modules referenced as URLs, either full URLs for modules to be downloaded or local paths to local files. The [Deno standard library](https://deno.land/std#deno-standard-modules) is maintained and hosted online and can be accessed via their URLs like the server in the example above. Deno also maintain a list of [recommended 3rd modules](https://deno.land/x) for wider functionality such as database access.

Let’s compare our hello world server in Deno (above), to the same hello world in Node, shown below.

```javascript

const express = require(‘express’)
const app = express()
const port = 3000

app.get(‘/’, (req, res) => res.send(‘Hello World!’))

app.listen(port, () => console.log(`Listening at [http://localhost:${port}`](http://localhost:${port}`)))
```

The main difference here is that we are not using callbacks, all asynchronous actions in Deno return a promise instead, this enables us to use [Async-Await syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) to write the asynchronous code using synchronous control structures such as for loops keeping our code tidy.

Normally async-await requires that await is used in a function marked as async, Deno lets you use await syntax even at the top level so you can use it to pull in your data without needing to embed it in a function.

For example with fetch, which returns a promise you can do:

```javascript

const response = await fetch('https://some.url');
const data = await response.json();
```

The next step is running your server:

```javascript

deno run --allow-net index.ts
```

The allow-net instruction gave approval for the network. The app still can’t read or write to the file system like that, we would have to allow it manually first. By explicitly enabling certain functions we can feel a bit more secure that the modules and Deno apps we download aren’t going to do something we do not allow.

![](https://cdn-images-1.medium.com/max/2560/1*rHvT4w_MqRxDd6oHPGat2g.jpeg)

## Node.js Versus Deno recap

So, is deno the new node or is just its little brother? Node successfully build a strong community with a lot of open source projects, stability and documentation.

Deno on the other hand uses ESModules for it’s imports, so cannot use the old node modules but it is able to share modules written with new ES Module syntax. Many modern libraries and frameworks now provide a ESModule version for use in browsers and with bundlers like web pack and rollup that there is alrady a large ecosystem of packages.

We have to wait a little bit more to see how developers are using this technology in production and to see if it gains popularity among the modern tech world. Anyway we can see that it can have a lot of potential bringing security and fast runtime web apps.

### In the meantime let’s recap some differences:

* Node uses npm package and node modules. Deno doesn’t use npm anymore, it uses modules referenced as URLs or file paths, it includes a built-in package manager for resource fetching.

* Node uses package.json in order to make a reference to its libraries installed. Deno does not use package.json in its module resolution algorithm.

* Deno requires permissions for file, network, and environment access.

* Deno uses “ES Modules” and does not support require(). Deno can import third party modules from any location on the web, like GitHub, a personal webserver, or a CDN.

* All async actions in Deno return a promise.

* It supports Typescript out of the box, therefore redesigns API to utilize [Promises](https://en.wikipedia.org/wiki/Futures_and_promises), [ES6](https://en.wikipedia.org/wiki/ECMAScript) and TypeScript features

We are looking forward to hear more about what the community is doing with Deno, we are also building some open source projects with [Ada Rose Cannon](undefined) to show you how it works. Stay tuned! 🦕



By Laura Morinigo on June 30, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/hello-deno-ed1f8961be26)
