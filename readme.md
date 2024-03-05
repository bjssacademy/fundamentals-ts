# TypeScript Primer - A Whistlestop Tour

We're going to assume here you have some experience in JavaScript, or another programming language, to understand this course. And when we say it's a whistlestop tour, it's very much an overview of why TypeScript is a good choice, and why it's used.

At the end you'll have the chance to install and play with TypeScript, but we are leaving a lot to you as there are many, many places with examples and courses, a couple of which we will include at the end.

There are various concepts in TypeScript that we cover but don't explain. So if you're not sure about types, interfaces, inheritance and so forth from OOP, you may want to check out some other [resources](https://archive.is/SiQLV) first - however, even if you just use TypeScript to make you JavaScript experience safer then you'll still get some of the benefits!

## Why this primer exists
TypeScript is becoming more popular…

![](<img/TypeScript Primer0.png>)[^1]

…and it’s taking ground from the ‘traditional languages':

![](<img/TypeScript Primer1.png>)[^2]

## A brief history of JavaScript

It all started in 1995….
* JavaScript was *intended* for small-scale websites (before ‘apps’ was a word!)
  * Small
  * Simple
  * Accessible
  * Run in the browser
* Java for complex business applications
  * Required protection for engineers
  * Prevent some type of error (i.e. picked up at compile time)
  * Run anywhere

---

Back in ‘95, there was a desire to move beyond static sites, so Netscape decided to add a scripting language to Navigator. They pursued two routes to achieve this: collaborating with Sun Microsystems to embed the Java programming language, while also hiring Brendan Eich to embed the Scheme language. 

Netscape management soon decided that the best option was for Eich to devise a new language, with syntax similar to Java and less like Scheme or other extant scripting languages. Although the new language and its interpreter implementation were called LiveScript when first shipped as part of a Navigator in September 1995, the name was changed to JavaScript for the official release in December.

The choice of the JavaScript name has caused confusion, implying that it is directly related to Java. 

At the time, the dot-com boom had begun and Java was the hot new language, so Eich considered the JavaScript name a marketing ploy by Netscape.

### How it Started

Adding some simple interactivity to you static site via an alert:

![](<img/TypeScript Primer2.png>)

### And then what happened?

JavaScript took over the world.

![](<img/TypeScript Primer3.png>)

* JavaScript on the Server  became a thing
  * [Netscape's](https://en.wikipedia.org/wiki/Netscape) LiveWire Pro Web (1997)
  * …and then NodeJS (2009)
    * [event-driven programming](https://en.wikipedia.org/wiki/Event-driven_programming)
    * open source
    * enabling development of fast web servers (NodeJS)
    * scalable, without using [threading](https://en.wikipedia.org/wiki/Thread_(computing))
* _Who uses it?_
  * *LinkedIn, Netflix, Uber, Trello, PayPal, NASA, eBay*

---

Over 97% of websites use JavaScript on the client side for web page behavior, often incorporating third-party libraries. All major web browsers have a dedicated JavaScript engine to execute the code on users' devices. 

**JavaScript is a event-driven language**

Event loops in JavaScript allow you run numerous tasks without waiting for other tasks to complete. This helps in responding to events in real time, handling multiple tasks parallelly, and allowing multiple devices to respond to the same event. This contributes to a great extent in saving precious battery power.

**JavaScript is single threaded**

Only one statement is executed at a time, but supports asynchronous execution so that it doesn’t block (via callbacks).

### How it's Going

![](<img/TypeScript Primer5.png>)

Express is a web framework:

- It has > 25k  related packages

- [Total number of packages > 1.3 million in 2020](https://blog.npmjs.org/post/615388323067854848/so-long-and-thanks-for-all-the-packages)

It's used for [crypto](https://github.com/KomodoPlatform/atomicDEX-Desktop), and even by [SpaceX](https://www.infoq.com/news/2020/06/javascript-spacex-dragon/).

## Everything is fine

Of course, JavaScript is a dynamic language. Which means you don't run into errors until runtime.

And it can result in some quite strange outcomes that often leave you saying "Wat?".

Watch the below to see some of the more head-scratching things you can do in dynamic languages:

[ https://www.destroyallsoftware.com/talks/wat](https://www.destroyallsoftware.com/talks/wat)

### Other examples

**JavaScript**
```js
var name = "Danger"

// Also OK

var name = 1

var name = false

var name = ["2018-02-03", "2019-01-12"]
```

All of the above is *perfectly valid* in JavaScript. You will get no errors at run time. Whilst variables are mutable, even their *type* is changeable!

**Java**
```java
String name = "Danger";

// Not OK, the code wouldn't be accepted by Java = Compiler error

String name = 1;

String name = false

String name = new String[]{"2018-02-03", "2019-01-12"};
```
Java, an example of a statically-typed language, won't allow you to do this.

## Why is this a problem?

![](<img/TypeScript Primer9.jpg>)

**<u> Using ‘other’ code can lead to bugs </u>**

- Many systems are made up of hundreds of thousands of files.

- A single change to one individual file can affect the behaviour of any number of other files

- Validating the connections between every part of your project takes time

- Unit tests offer some protection

Type-checked languages offer ***more*** protection

---

If you know every line of code, and totally understand the domain, and you have a rich model, you might be okay. BUT, what about the code you didn’t write?

## How can we protect ourselves?

* Safety
* Remove bugs
* Limit what developers can do
* Tell them what they can do
* But still allow them to shoot themselves in the foot
* Introducing TypeScript!

## JavaScript *is* TypeScript

* TypeScript is *not* JavaScript
* TypeScript is a *superset* of JavaScript
  * TypeScript ⊃ JavaScript

```js
// hello.js

var name = "Danger"

console.log("Hello, " + name)
```  

```ts
// hello.ts

var name = "Danger"

console.log("Hello, " + name)
```

# How does TypeScript Help

* Easier refactoring
* Easier to orienting oneself in bigger systems
* Catches easy to confuse mistakes
* You will need to try harder to do strange things, e.g. 	`“4” + “20” = “420”`
* You can avoid *'undefined' is not a function*.
* Allows OOP-style code

![](<img/TypeScript Primer11.png>)

## Typing TypeScript (Implicit vs Explicit)

  * Types in TypeScript can be both implicit and explicit.
  * If you do not explicitly write your types, the compiler will use *type inference* to infer the types you are using.

  > Scratching your head wondering what a type is? Check out our [fundamentals guide on types](https://github.com/bjssacademy/fundamentals-general/blob/main/types.md).

```ts
// Implicit

let anExampleVariable = "Hello World"  ;

anExampleVariable = false  ;

console.log(anExampleVariable);
```

```ts
// Explicit

let anotherVariable: string  ;

anotherVariable = "Hello Again"  ;

anotherVariable =   false  ;

console.log(anotherVariable);
```

Both of this will cause errors, because once the variable's type has been set - either implicitly or explicitly - then you cannot change the underlying type the variable is.

This means we can catch errors *far earlier* than at runtime!

## Typing TypeScript (Any)

Of course, you *could* decide that you need a variable to be completely flexible because you don't understand types and write completely bulletproof code that nobody will ever use or have to support...

Ok, so we're just letting you know this exists and you *can* do it. But just because you can, doesn't mean you should.

```ts
// ‘Any’ typing

let anythingVariable: any;

anythingVariable = "Hello Again";

anythingVariable = false;

console.log(anythingVariable);

// ------- Is the same as, the below, which is valid JavaScript -------

let anythingVariable;

anythingVariable = "Hello Again";

anythingVariable = false;

console.log(anythingVariable);
```
## How Does it Work?

Well, browsers don't understand TypeScript, but they do understand JavaScript. So whilst TypeScript helps us avoid errors at compile-time, we actually need to use the TypeScript Compiler (TSC) to convert TS into JS.

* TypeScript > `TSC` > JavaScript > Runtime
  * Similar to compilation
  * TypeScript becomes JavaScript by deletion (of types)

TSC removes all the type annotations and other TypeScript-specific syntax, essentially converting TypeScript code into plain JavaScript.

This process allows developers to leverage the benefits of TypeScript during development while still being able to run code in any JavaScript environment.

## Features – because it’s JavaScript

So, because TypeScript is JavaScript, it has many of the same features:

* Objects
  * Behaviour
  * State

TypeScript supports objects with both behaviour and state, much like JavaScript.

* Functions as first-class citizens

Functions can be treated as values and passed around like any other variable.

* Fast start times
* Portability
* A lot of libraries

![](<img/TypeScript Primer12.png>)

## Language Features Because it’s Not JavaScript

* Strong typing
  * Compile time checking

![](<img/TypeScript Primer13.png>)

### Familiar inheritance model (like Java, C#)

![](<img/TypeScript Primer14.png>)

### Interfaces

![](<img/TypeScript Primer15.png>)

[What's an interface then?](https://tommcfarlin.com/understanding-interfaces/)

### Enums

![](<img/TypeScript Primer16.png>)

### Unit types
  * Unit types are subtypes of primitive types that contain exactly one primitive value

![](<img/TypeScript Primer17.png>)

### Type Aliases

![](<img/TypeScript Primer18.png>)

# What Next?

1. Read the TypeScript Handbook	[https://www.typescriptlang.org/docs/handbook/intro.html](https://www.typescriptlang.org/docs/handbook/intro.html)
2. Get familiar with the playground
3. Read the examples
    * [https://www.typescriptlang.org/play#show-examples](https://www.typescriptlang.org/play#show-examples)
4. [Set up TypeScript](#setting-up-typescript) to run locally
5. Learn about [testing](#setting-up-tests-with-jest) with Jest
6. Do the [exercise](#exercise) below.

## Exercise

* Build a Key Value Store using TypeScript
* The store must:
  * Allow items to be added, removed, retrieved
  * Store meta data alongside each item, including
    * When it was added
    * When it was last accessed
    * Who added it
  * Allow different storage mechanisms to be used, i.e.
    * In-memory,
    * File
    * Database

## Setting up TypeScript

- Install [Node Version Manager (nvm)](https://github.com/nvm-sh/nvm)

  - Note: nvm also supports Windows in some cases. It should work through WSL (Windows Subsystem for Linux) depending on the version of WSL. It should also work with GitBash (MSYS) or Cygwin. Otherwise, for Windows, a few alternatives exist,of which we recommend [nvm-windows](https://github.com/coreybutler/nvm-windows)

- Install Nodejs (`nvm install --lts`)

  - What's Node? Well, in the simplest sense, node allows you to run JavaScript on your computer without using a browser. It does other things too, but if you've not come across node before now, then just think of it as something that lets you run JavaScript outside of a browser.

- Create a node project (`npm init`)

- Install TypeScript (`npm install typescript --save-dev`)

- Create a sample `helloWorld.ts` file

- Transpile it (`npx tsc <your_ts_file>`)

- Find the created JavaScript file on your file system

- Run the JavaScript file (`node <your_js_file>`)

## Setting up Tests with JEST

- `npm install --save-dev typescript jest @types/jest ts-jest`

- `npx tsc --init`

- In the `tsconfig.json`, change the “rootDir” folder to target the root of the source (generally, ./src)

- `npx ts-jest config:init`

- Run any tests using: `npx jest`

A base test is: 	
```ts
test("Dummy unit test", () => {

  const actual = null; // not implemented yet

  expect(actual).toBe(1);

});
```
Ref: [https://medium.com/swlh/jest-with-typescript-446ea996cc68](https://medium.com/swlh/jest-with-typescript-446ea996cc68)

## Other resources

- [TypeScript Tutorial](https://www.w3schools.com/typescript/index.php) - all online with executable code and free from W3Schools

# About

## What does NVM do?

NVM (Node Version Manager) is a tool used to download, install, manage, and upgrade Node.js versions. It allows you to maintain multiple versions of Node.js on your system and change the active version depending on your current needs.

### Common commands
```
// check version
node -v || node --version

// list locally installed versions of node
nvm ls

// list remove available versions of node
nvm ls-remote

// install specific version of node
nvm install 18.16.1

// set default version of node
nvm alias default 18.16.1

// switch version of node
nvm use 20.5.1

// install latest LTS version of node (Long Term Support)
nvm install --lts

// install latest stable version of node
nvm install stable
```

## What is NPM

NPM (Node Package Manager) is the default Node.js package management tool that comes as a part of the Node.js installation.

It enables you to install libraries, frameworks, and other development tools for your project, similar to installing a mobile application from an app store.

When you clone a repository, one of the first things you will need to do is install all the dependencies listed in `package.json` using `npm install`

### Common commands

```
//install dependent packages
npm install

//install a particular package
npm install -g [package name]

//update a package
npm update [package name]

```

## Package.json

When you add packages to your project that it depends on, these are stored in the package.json file.

Not all fields available in package.json will apply to you, but we can achieve some powerful benefits by recording information about our application in its package.json file.

* Sections
  * Name
  * License
  * Author
  * Version
  * Main
  * Private (prevents accidental publishing)
  * Scripts
  * Dependencies
  * Dev Dependencies

## Dependencies

  * Dependencies
    * npm install …
  * Dev Dependencies
    * npm install … -- save-dev

## Versioning

    * Semver
    * special characters
      * ^ = minor
      * ~ = patch
      * <= any version up to and including that specified
      * no special = only that version (aka pinned)

## Dependency Risk Mitigatations

* Version pinning (or not)
* Commit package.lock
* Commit node_modules??
* Private repository
  * Artifactory
  * Npm Enterprise
  * Security oversight

## Node scripts

* `Npm run <name of script>`
* Testing
  * Unit
  * Integration
* Linting
* Formatting
* Deploying
* Building
* Anything you can think of….
  * …But think about running on different platforms

## Automation

* Create an npm task to run app code
* Create an npm task to run your unit tests
* Create an npm task to automatically format your code using prettier
* Create an npm task to build your app to a dist folder
* Set up a githook to automatically run your unit tests before you can commit
  * If the tests fail, then the commit should be aborted

---

[^1]:The top graph shows the most commonly used languages for professional developers in 2021
Ref: https://insights.stackoverflow.com/survey/2021#most-popular-technologies-language-prof 

[^2]:The second graph shows the trends in questions asked on Stackoverflow over time: 
https://insights.stackoverflow.com/trends?tags=c%23%2Cjava%2Cjavascript%2Ctypescript
TypeScript = growing!, but it’s continuous growth.