---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Node.js - part 2/12
Back-End Development
- [ ] Use modules when coding a Node.js application
- [ ] Setup a remote repository using Github

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
TODO: fill in anchor href above to point to github repo for these slides
-->

---
transition: slide-left
---

# Recap
(10 min) What website can you search to check if there is an npm module for that topic?

- What is the basic command to run a node file?
- Global variables:
```js
console.log("__dirname is: ", __dirname);
console.log("__filename is: ", __filename);
console.log("global is: ", global);
console.log("module is: ", module);
console.log("exports is: ", exports);
console.log("process is: ", process) // see .argv
```

- What is the npm command to initialize a node project? 
- what is the command to install a module via `npm`?
   - where do these installations go?

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
-->

---
transition: slide-left
---

# Modules
(30 min) How are modules created and used?

- Create math.js file with add/subtract functions and export/import it to use it
   - try old CJS `module.exports` way
   - try new ES6 `import` way
   - try old CJS `exports` way
- `npm install` https://www.npmjs.com/package/random-poll and try using it
   - change my index.js file so it uses `module.exports` way
   - change my index.js file so it uses `import` way
- instead of `node index.js` use `npm start` way

---
transition: slide-left
---

# Built-in Modules for Node.js
Node.js has core internal modules

- Other built-in modules include: `http` `fs` `path` `url` `events` `crypto` etc...
- Node Docs: [http](https://nodejs.org/api/http.html#httpcreateserveroptions-requestlistener) (we did an example of this last week)

```js
import http from 'http';
  
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.write('<h1>hello world</h1>');
  res.end();
});

server.listen(3030)
```

<!--
-->

---
transition: slide-left
---

# `fs`
(5 min) Provides utilities for working with the file system

- Node Docs: [fs](https://nodejs.org/api/fs.html)
- can create, read, append, delete, rename files

```js
const fs = require('fs');

const content = 'Hello, Node.js File System!';

fs.writeFile('example.txt', content, (err) => {
  if (err) {
    console.log('Error writing file:', err);
  } else {
    console.log('File created and content written successfully!');
  }
});
```
- Exercise: write a server that serves an HTML file or an image from the file system when a specific route (ex: `/about`) is accessed.  Combine modules `http` with `fs` for this
   - [How to work with Files in Node](https://www.freecodecamp.org/news/how-to-work-with-files-in-node-js/)
   - [How to Read/write Files with Node](https://www.freecodecamp.org/news/how-to-read-and-write-files-with-nodejs/)
<!--
-->

---
transition: slide-left
---

# `path`
(5 min) Provides utilities for working with file and directory paths 

```js
const path = require("node:path"); // note: `path` is internal

// get file name
console.log(path.basename("/Desktop/temp2/index.js"));

// get a directory name
console.log(path.dirname("/Desktop/temp2/index.js"));

// join path segments
console.log(path.join("folder", "subfolder", "file.txt"));
```

<!--
-->

---
transition: slide-left
---

# `url` vs `URL`
(5 min) Provides utilities for working with url

- Node Docs: [url](https://nodejs.org/api/url.html)

```js
// const url = require('url');

const urlString = 'https://www.example.com:8080/pathname/?search=test#hash';
// const parsedUrl = url.parse(urlString); // hover over .parse > depracated
const parsedUrl = new URL(urlString); // this is the recommended way 

console.log(parsedUrl);
```

<!--
-->

---
transition: slide-left
---

# `events`
(5 min) Work with event-driven programming

- Node Docs: [events](https://nodejs.org/api/events.html)

```js
const EventEmitter = require("events");

// Create a new EventEmitter instance
const eventEmitter = new EventEmitter();

// Register an event listener for the 'greet' event
eventEmitter.on("greet", (name) => {
  console.log(`Hello, ${name}! Welcome to Node.js.`);
});

// Emit the 'greet' event
eventEmitter.emit("greet", "Alice");
eventEmitter.emit("greet", "Bob");
```

<!--
-->

---
transition: slide-left
---

# `crypto`
(5 min) Provides cryptographic functionality such as hashing and encrypting

- Node Docs: [crypto](https://nodejs.org/api/crypto.html)

```js
const crypto = require("crypto");

const hash = crypto.createHash("sha256");
hash.update("Hello, world!");
console.log(hash.digest("hex")); // Output: SHA-256 hash of 'Hello, world!'

```

<!--
-->

---
layout: image-right
transition: slide-left
image: /assets/rauch.png
backgroundSize: 500px 300px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:

- ▶️ [Run Node scripts from command line](https://nodejs.org/en/learn/command-line/run-nodejs-scripts-from-the-command-line)
- ▶️ [Node.js crash course](https://www.youtube.com/watch?v=32M1al-Y6Ag)
- 🍎 [Node tutorial](https://www.w3schools.com/nodejs/nodejs_modules.asp)
- 📂 [File system Module](https://github.com/nodejs/nodejs.dev/blob/aa4239e87a5adc992fdb709c20aebb5f6da77f86/content/learn/node-js-modules/node-module-fs.en.md)
- 📖 [Git and GitHub Tutorial article](https://www.freecodecamp.org/news/git-and-github-for-beginners/)
- ▶️ [Git and Github Tutorial video](https://www.youtube.com/watch?v=RGOj5yH7evk)

<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

<!-- 
- take attendance
-->

---
transition: slide-left
---

# External Packages and `npm`

- common 3rd party modules:  `body-parser` `dotenv` `uuid` `cors` `lodash` `date-fns`

<!--
- import { myWords } from "mywords";
- const story = `<p width: 500px; font-size: 24px; line-height: 1.5>${myWords.getWord()}...`
- document.body.innerHTML = story
-->

---
transition: slide-left
---

# `body-parser`
(5 min) Parse incoming request bodies in middleware before your handlers, available under `req.body`, making it easy to access data sent by clients (via form submissions, JSON data)

- review: html form submits via GET/POST requests automatically
- npmjs.com: [body-parser](https://www.npmjs.com/package/body-parser)

```js
const express = require("express");
const bodyParser = require("body-parser");

const app = express();
app.use(bodyParser.json()); // Middleware to parse JSON data

app.post("/data", (req, res) => {
  console.log(req.body); // or req.query if via GET
  res.send("Data received");
});

app.listen(3000, () => console.log("Server running on port 3000"));
```

- test above using Postman

---
transition: slide-left
---

# what about GET requests?
(5 min) when using `express` can parse GET requests via `req.query` 

```js
const express = require('express');
const app = express();

// Route to handle GET requests
app.get('/search', (req, res) => {
  // Access query parameters via req.query
  const { name, age } = req.query;
  console.log(`Name: ${name}, Age: ${age}`);  // Logs query parameters from the URL
  
  res.send(`Searching for name: ${name}, age: ${age}`);
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

<!--
-->

---
transition: slide-left
---

# `dot-env`
(5 min) Securely manage environment variables

- in terminal type: `echo "DB_PASSWORD=123456789" > .env`

```js
require("dotenv").config();

console.log(process.env);
console.log(process.env.DB_PASSWORD);
```


<!--
-->

---
transition: slide-left
---

# `uuid`
(5 min) Generates unique identifiers

```js
const { v4: uniqId } = require("uuid");

console.log(uniqId());
console.log(uniqId());
console.log(uniqId());
```

<!--
-->

---
transition: slide-left
---

# Exercise
(remainder of time) Challenge + Github exercise

- Challenge: Create server code that gets a search term from the command line (ex: happy) and makes a fetch request to [Giphy API](https://developers.giphy.com/explorer/) using the given API_KEY to display gifs related to the search term
- Tips: [Nullish coalescing operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing) How to debug in node?
- Github Exercise: 
   1. Create Github Repo
   1. Commit and push code to repo 

---
transition: slide-left
---

# Homework

- Assignment #2 due this Apr. 13 midnight EST
- Goto: https://www.freecodecamp.org/learn/back-end-development-and-apis/
- Start Freecodecamp ["Managing Packages with NPM"](https://www.freecodecamp.org/learn/back-end-development-and-apis/) followed by "Basic Node and Express"
