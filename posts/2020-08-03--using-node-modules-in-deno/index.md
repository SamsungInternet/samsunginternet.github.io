---
permalink: "/using-node-modules-in-deno/"
cover: img.jpg
title: "Using node modules in Deno"
description: "Last time we introduced about Deno and discussed how it compares to node, like node, Deno is a server side code-execution environment based on web technology."
category: Web Development
img: https://miro.medium.com/max/1200/0*9AWwWyhHQ6rbvokL
author: Ada Rose Cannon
authorImg: https://miro.medium.com/fit/c/96/96/1*Dn8pr_cbYLtc_KfmUNhnBA.png
tags: [Web Development, Nodejs, JavaScript, Deno, Samsung Internet]
---

# Using node modules in Deno

Using node modules in Deno

### A bad practice but sometimes there is no alternative.

[Last time we introduced about Deno](https://medium.com/samsung-internet-dev/hello-deno-ed1f8961be26) and discussed how it compares to node, like node, [Deno](https://deno.land/) is a server side code-execution environment based on web technology.

* Node uses JavaScript with commonjs modules and npm/yarn as it’s package manager.

* Deno uses Typescript or JavaScript with modern javascript import statements. It does not need a package manager.

To import a module as usual in deno you reference it by URL:

```javascript

import { serve } from "https://deno.land/std/http/server.ts";
```

You can find many of the modules you may need in the [Deno standard library](https://deno.land/std) or in the [Deno third party modules list](https://deno.land/x) but they don’t have everything.

Sometimes you need to use a module which the maintainers have only made available through the npm ecosystem. Here are some methods from most convenient to least:

### 1. If the module already uses ES modules import/export syntax.

The libraries you use from deno don’t have to come from the recommended Deno packages they can come from any URL, provided they use the modern import syntax. Using unpkg is a great way to access these files directly from inside an npm repo.

```javascript

import throttle from [https://unpkg.com/lodash@4.17.19/throttle.js](https://unpkg.com/lodash@4.17.19/throttle.js)
```

### 2. If the module itself doesn’t use imports but the source code does

If the module is compiled or in the wrong format though npm you may still have some luck if you take a look at the source code. Many popular libraries have moved away from using commonjs in their source code to the standards compliant es module import syntax.

Some packages have a separate src/ and dist/ directory where the esmodule style code is in src/ which isn’t included in the package available through npm. In that case you can import from the source directly.

```javascript

import throttle from "https://raw.githubusercontent.com/lodash/lodash/master/throttle.js";
```

I got this URL by clicking on the “raw” button on github to get the raw JS file. It’s probably neater to use a [github cdn](https://raw.githack.com/) or to see if the file is available through github pages, but this works.

**NB: **Some libraries use esmodules with webpack, or a module loader which lets them import from node modules like this:

```javascript

**Bad:**

import { someFunction } from "modulename";

import { someOtherFunction } from "modulename/file.js";
```

The standard for imports is that they need to start with ./ or be a URL to work

```javascript

**Good:**

import { someOtherFunction } from "./folder/file.js";
```

In that situation try the next method:

### 3. Importing commonjs modules

Fortunately there is a service called [JSPM](https://jspm.org/) which will resolve the 3rd party modules and compile the commonjs modules to work as esmodule imports. This tool is for using node modules in the browser without a build step. But we can use it here too.

![The JSPM logo](https://cdn-images-1.medium.com/max/2000/1*o58qtVB981PVm9XV67ZTJg.png)*The JSPM logo*

In my most recent project i wanted to do push notifications, which involves generating the credentials for VAPID, there is a deno crypto library which can do encryption but doing the full procedure is difficult and I’d rather use the popular [web-push](https://www.npmjs.com/package/web-push) library. I can import it using the JSPM CDN using the URL like below:

```javascript

import webPush from "https://dev.jspm.io/web-push";
```

I can now use it like any other module in deno.

This almost worked 100% some of the bits which relied on specific node behaviors such as making network requests failed in this situation I had to work around this to use the standardised fetch API deno uses.

### Getting Typescript types working

One nice feature of typescipt, which deno uses, is that it provides really good autocomplete for modules. The deno extension for my editor even can autocomplete for third part modules if it knows the type definitions.

This isn’t essential to getting the code to work but can provide huge benefits for helping you maintain your code.

When I was importing another module called [fast-xml-parser](https://www.npmjs.com/package/fast-xml-parser) when I was looking through the source code I noticed it had a type definitions file which is a file which ends in .d.ts . These files describe the various interfaces and even work for even for JavaScript .js files. You can sometimes also find the type definitions files in the @types\somemodule repo.
[**DefinitelyTyped/DefinitelyTyped**
*The repository for high quality TypeScript type definitions. - DefinitelyTyped/DefinitelyTyped*github.com](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types)

Using this file typescript can auto complete on things imported from JavaScript files. Even for files imported using JSPM:

```javascript

// Import the fast-xml-parser library
import fastXMLParser from "https://dev.jspm.io/fast-xml-parser";

// Import the type definition file from the source code of fast-xml-parser
import * as FastXMLParser from "https://raw.githubusercontent.com/NaturalIntelligence/fast-xml-parser/master/src/parser.d.ts";

*// Use the parser with the types
const* parser = fastXMLParser as typeof FastXMLParser;
```

I import the type definitions from the definition files as FastXMLParser (note the uppercase F) this doesn’t contain any working code but is an object which has the same type as the code we want to import.

I import the code from JSPM as fastXMLParser (lowercase f) which is the working code but has no types.

Next I combine them together to make parser which is fastXMLParser with the type of FastXMLParser .

Thank you for reading, I hope you give [deno](https://deno.land) a go. The ability to use any module made for the web and even some which were made for node/npm really gives this new server side library ecosystem a good foundation to get started from. 🦕



By Ada Rose Cannon on August 3, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/using-node-modules-in-deno-2885600ed7a9)
