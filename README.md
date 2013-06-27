#Front-end Job Interview Questions

@version 2.0.0

**Note:** This version contains additional questions from various companies I interviewed with for Frontend Developer, as well as answers for most of the questions that I believe is right.

This repo contains a number of front-end interview questions that can be used when vetting potential candidates. It is by no means recommended to use every single question here on the same candidate (that would take hours). Choosing a few items from this list should help you vet the intended skills you require.

[Rebecca Murphey](http://rmurphey.com/)'s [Baseline For Front-End Developers](http://rmurphey.com/blog/2012/04/12/a-baseline-for-front-end-developers/) is also a great resource to read up on before you head into an interview.

**Note:** Keep in mind that many of these questions are open ended and could lead to interesting discussions that tell you more about the person's capabilities than a straight answer would.

####Original Contributors

The majority of the questions were plucked from an [oksoclap](http://oksoclap.com/) thread created originally by [Paul Irish](http://paulirish.com) ([@paul_irish](http://twitter.com/paul_irish)) and contributed to by the following individuals:

* [@bentruyman](http://twitter.com/bentruyman) - http://bentruyman.com
* [@cowboy](http://twitter.com/cowboy) - http://benalman.com
* [@ajpiano](http://ajpiano) - http://ajpiano.com
* [@SlexAxton](http://twitter.com/slexaxton) - http://alexsexton.com
* [@boazsender](http://twitter.com/boazsender) - http://boazsender.com
* [@miketaylr](http://twitter.com/miketaylr) - http://miketaylr.com
* [@vladikoff](http://twitter.com/vladikoff) - http://vladfilippov.com
* [@gf3](http://twitter.com/gf3) - http://gf3.ca
* [@jon_neal](http://twitter.com/jon_neal) - http://twitter.com/jon_neal
* [@wookiehangover](http://twitter.com/wookiehangover) - http://wookiehangover.com
* [@darcy_clarke](http://twitter.com/darcy) - http://darcyclarke.me
* [@iansym](http://twitter.com)

### General Questions:

* What did you learn yesterday/this week?
* What excites or interests you about coding?
* Talk about your preferred development environment. (OS, Editor, Browsers, Tools etc.)
* Can you describe your workflow when you create a web page?
* Can you describe the difference between progressive enhancement and graceful degradation?
  * Bonus points for describing feature detection
  * **Answer**: Progressive Enhancement essentially means starting from the bottom up. Make sure your website works at its minimial level (without any technologies), and then enhance it layer by layer (adding interaction, css, etc) to improve user experience while being mindful of older browsers that cannot support the newer technologies (having static page when ajax can't work, noscript javascript tags, etc). Put Content First.
  * **Answer**: Graceful Degradation essentially means starting from the top and working down. Your website is designed using HTML5, CSS3, javascript, and all of those latest technologies. Then from there, you add in compatibilities for older browsers (IE using conditional tags). 
* Explain what "Semantic HTML" means.
  * **Answer**: It means using HTML markup to represent the content and meaning of the website rather than presentation.
* How would you optimize a websites assets/resources?
  * Looking for a number of solutions which can include:
    * File concatenation
    * File minification
    * CDN Hosted
    * Caching
    * etc.
* Why is it better to serve site assets from multiple domains?
  * How many resources will a browser download from a given domain at a time?
  * **Answer**: To improve speed. Each browser has as limit on concurrent connections per domain. Chrome, for example, only allows 6 http connections at once per host.
* Name 3 ways to decrease page load. (perceived or actual load time)
  * **Answer**: Compress content, using gzip compression for example. Also can minify content to reduce resources' size.  Putting CSS and javascript in external files, referencing css at the top of the webpage, and javascript files at the end of the webpage. Also cache whenever possible.
* If you jumped on a project and they used tabs and you used spaces, what would you do?
  * Suggest the project utilize something like EditorConfig (http://editorconfig.org)
  * Conform to the conventions (stay consistent)
  * `issue :retab! command`
* Write a simple slideshow page
  * Bonus points if it does not use JS.
* What tools do you use to test your code's performance?
  * Profiler, JSPerf, Dromaeo
* If you could master one technology this year, what would it be?
* Explain the importance of standards and standards bodies.
* What is FOUC? How do you avoid FOUC?

### HTML-Specific Questions:

* What's a `doctype` do?
  * **Answer**: Defines the document type
* What's the difference between standards mode and quirks mode?
  * **Answer**: Quirks mode emulates behavior and layout for old browsers like NetScape or IE5. Standards emulates behavior described by the HTML and CSS standards.
* What are the limitations when serving XHTML pages?
  * Are there any problems with serving pages as `application/xhtml+xml`?
* How do you serve a page with content in multiple languages?
  * What kind of things must you be wary of when design or developing for multilingual sites?
* What are `data-` attributes good for?
  * **Answer**: Custom data variables, can be easily accessed using the dataset property of DOM.
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
 * **Answer**: HTML5 at its core is still a layout language that gives structure to your sites. The building blocks are just the various semantic tags that give your site meaning and structure.
* Describe the difference between cookies, sessionStorage and localStorage.
  * **Answer**: Cookies are permanent (until they expire) key-value pairs logged by a website in your hard drive, can be used by all browsers (not browser-specific). session and localStorage are supported only on HTML5 browsers. sessionStorage stores key-value pairs of data, but are cleaned when a user closes the browser. localStorage stores key-value pairs forever until deleted by user or the website. 

### Browser-Internals Questions
* Main Flow and Render Tree - What are they?
  * **Answer**: The mainflow of the browser rendering engine is something like this: Parses the HTML tags to DOM nodes to produce a DOM tree --> Parsing the CSS and styling information to construct a render tree --> Layout of the render tree --> Paint the render tree
  * **Answer**: The render tree is similar to DOM tree but with styling information along with visual instructions in HTML. These are simply a list of elements that are to be rendered (for example display: none html elements will not be on this tree, neither would script or head tags).
* Describe what happens when a user clicks a link in a browser
* **Answer**: This is a very open-ended question. First the javascript event handlers trigger and run the associated functions with that. Afterwards it will issue a HTTP Get request (constructing the HTTP header), first to a local DNS resolver to resolve the domain name. If the domain is not found in the local DNS server, then depending on how your cache is set up, it will pass on the request to either the 1) Root DNS Server, 2) Top Level DNS Server, or 3) authoritive DNS server. From there it returns the associated IP address and port. Once your browser knows the IP address of the destination, it sends its request directly to that web server (can discuss how packets are constructed and routed and forwarded in a network), and the webserver generates a response (its associated header and response payload).

### Misc Technologies To Know
* Less and Sass for CSS Preprocessing
* Tools useful for JS 
  * JSLint
  * Grunt.Js
  * YUI Compressor
  * JCharts and HighCharts

### JS-Specific Questions

* Explain event delegation
  * **Answer**: Two models - event bubble and event capture. Event bubbling describe that an event will 'bubble up' to all of its parents when initiated. Event capture describes that an event will 'propagate down' to all of its children when initiated.
* Explain how `this` works in JavaScript
  * **Answer**: `this` refers to the object of the current execution context and scope. `this` is redetermined everytime a new execution context is ran.
* Explain how prototypal inheritance works
  * **Answer**: Javascript is a dynamic, weakly typed language. Unlike other languages, Javascript does not have classes. In terms of inheritance, objects is the only thing that Javascript have. But it has the notion of a prototypical object, an object used as a template from which to get the initial properties for a new object. Any object can specify its own properties, either when you create it or at run time. In addition, any object can be associated as the prototype for another object, allowing the second object to share the first object's properties. 
* How do you go about testing your JavaScript?
  * **Answer**: Custom tests using eval, using the debugger on firebug/javascript console (step-by-step debugging), putting a watch on all the variables and observe the stack at each step. Can also use try and catch statements too. 
* AMD vs. CommonJS?
* What's a hashtable?
* What are `undefined` and `undeclared` variables?
  * **Answer**: `undefined` is when variables are declared but not initalized (does not have a value). `undeclared` variables means just that - variables that are not declared yet. Will throw a reference error when ran.
* What is a closure, and how/why would you use one?
  * Your favorite pattern used to create them? argyle (Only applicable to IIFEs)
  * **Answer**: A closure is like keeping a copy of all the local variables, just as they were when a function exited. Like a stack-frame which is not deallocated when the function returns. Useful because it is convenient making your code more clear and readable, although you can achieve the same things without them.
* What's a typical use case for anonymous functions?
  * **Answer**: Code brevity, scope management (Anonymous functions can be used to create temporary/private scope), useful in closures. 
* Explain the "JavaScript module pattern" and when you'd use it.
  * Bonus points for mentioning clean namespacing.
  * What if your modules are namespace-less?
* How do you organize your code? (module pattern, classical inheritance?)
* What's the difference between host objects and native objects?
* Difference between:
```javascript
function Person(){} var person = Person() var person = new Person()
```
  * **Answer**: new creates an instance of a new object. Without new, ```var person``` will not be allocated and will be undefined after.
* What's the difference between `.call` and `.apply`?
  * **Answer**: They do the same thing except that .call function is invoked with separated arguments (explicitly) whereas .apply takes in an array of arguments.
* explain `Function.prototype.bind`?
  * **Answer**: Binds the execution environment to a current context (creating a boundary).
* When do you optimize your code?
* When would you use `document.write()`?
  * Most generated ads still utilize `document.write()` although its use is frowned upon
* What's the difference between feature detection, feature inference, and using the UA string
* Explain AJAX in as much detail as possible
* Explain how JSONP works (and how it's not really AJAX)
* Have you ever used JavaScript templating?
  * If so, what libraries have you used? (Mustache.js, Handlebars etc.)
* Explain "hoisting".
  * **Answer**: Variable declarations can be anywhere in javascript function, but they are 'hoisted' to the top of the function at runtime.
* Describe event bubbling.
* What's the difference between an "attribute" and a "property"?
* Why is extending built in JavaScript objects not a good idea?
* Why is extending built ins a good idea?
* Difference between document load event and document ready event?
* What is the difference between `==` and `===`?
  * **Answer**: `==` is evil, only checks for value equality, whereas `===` checks for both type and value.
* Explain how you would get a query string parameter from the browser window's URL.
  * **Answer**: No standard way, but can use document.baseURI to get the URL and use regexp to extract the query.
* Explain the same-origin policy with regards to JavaScript.
* **Answer**: It's a security policy to protect the confidentially and integrity of information of on the web. It prevents a website scripts from interacting with other scripts in other websites.
* Make this work:
```javascript
[1,2,3,4,5].duplicate(); // [1,2,3,4,5,1,2,3,4,5]
```
  * **Answer**:

```javascript
Array.prototype.duplicate = 
function(){var len = this.length;
for(var i =0; i < len; i++)
{
this.push(this[i])
}}
```
* Describe a strategy for memoization (avoiding calculation repetition) in JavaScript.
* Why is it called a Ternary expression, what does the word "Ternary" indicate?
  * **Answer**: It is used as an if-else expression. Ternary is composed of three items, that's because there are only 3 items in the expression. [conditional expression] ? [if expression is true] : [if expression is false]
* What is the arity of a function?
* What is `"use strict";`? what are the advantages and disadvantages to using it?
  * **Answer**: It catches some common coding bloopers, throwing exceptions and It prevents, or throws errors, when relatively "unsafe" actions are taken.
    * Disallows global variables - cause it is bad practice using them!
    * Cannot delete undeletable properties! Would throw an error!
    * Assigning values to non-writable properties - would throw an error!
    * All properties named in an object literal be unique! `var o = { p: 1, p: 2 }; // !!! syntax error`
    * Function argument parameters also need to be unique!
* Write a calender system which can show scheduled meetings (from - to) and attendees. Sort the meetings according to some rules (ex: starting time in ascending order). Find out how many meetings are overlapped.
  * **Answer**: http://pastebin.com/yCEvrz3r
* Implement the Math.sqrt() function that takes the square root of a given number.
  * **Answer**: http://goo.gl/zIkLP

### JS-Code Examples:

```javascript
~~3.14
```
Question: What value is returned from the above statement?
**Answer: 3** This is because `~~` is a shortcut for Math.floor function.

```javascript
"i'm a lasagna hog".split("").reverse().join("");
```
Question: What value is returned from the above statement?
**Answer: "goh angasal a m'i"** Reversed string. Note if you just want the words to be reversed, like "hog lasagna a i'm", then you would use `.split(' ').reverse().join(' ')`

```javascript
( window.foo || ( window.foo = "bar" ) );
```
Question: What is the value of window.foo?
**Answer: "bar"**
only if window.foo was falsey otherwise it will retain its value.

```javascript
var foo = "Hello"; (function() { var bar = " World"; alert(foo + bar); })(); alert(foo + bar);
```
Question: What is the outcome of the two alerts above?
**Answer: "Hello World" & ReferenceError: bar is not defined**

```javascript
var foo = [];
foo.push(1);
foo.push(2);
```
Question: What is the value of foo.length?
**Answer: `2`

```javascript
var foo = {};
foo.bar = 'hello';
```
Question: What is the value of foo.length?
**Answer: `undefined` This is because length is only part of the Array prototype, not Object. Although Array is an object and will inherit object prototype methods, object will not inherit array's.

### jQuery-Specific Questions:

* Explain "chaining".
* Explain "deferreds".
* What are some jQuery specific optimizations you can implement?
* What does `.end()` do?
  * **Answer**: Goes back to the state before filtering
* How, and why, would you namespace a bound event handler?
* Name 4 different values you can pass to the jQuery method.
  * Selector (string), HTML (string), Callback (function), HTMLElement, object, array, element array, jQuery Object etc.
* What is the effects (or fx) queue?
* What is the difference between `.get()`, `[]`, and `.eq()`?
  * **Answer**: .get() returns a DOM element, .eq() returns a jQuery object (can use jquery functions on it), and [] is the same as .get()
* What is the difference between `.bind()`, `.live()`, and `.delegate()`?
  * **Answer**: .bind() attaches an eventlistener to all the selectors that are matched. Very expensive, not good, not dynamic. .live() attaches an eventlistener to the document object (only once). Can use dynamic, but depreciated, useless selection since only attaches to document, cannot use chaining. .delegate() is like .live() but you can pick what selector to attach. Dynamic and can use chaining. 3 parameters instead $(selectorAnchor).delegate(selectorEvent, event, function)
* What is the difference between `$` and `$.fn`? Or just what is `$.fn`.
* Optimize this selector:
```javascript
$(".foo div#bar:eq(0)")
```
* Difference between 'delegate()' and 'live()'?


### CSS-Specific Questions:

* Describe what a "reset" CSS file does and how it's useful.
  * **Answer**: Reduce browser inconsistencies by setting like default line heights, margins, font sizes, etc. Blueprint and Bootstrap.
* Describe Floats and how they work.
* What are the various clearing techniques and which is appropriate for what context?
* **Answer**: 1) Can add a new div with style `clear:both` to html 2) Can use the psuedo class `:after` to do the same thing but also with `content:' ';` 3) lastly can set overflow to either hidden or auto and width 100% (or any)
* Explain CSS sprites, and how you would implement them on a page or site.
* What are your favourite image replacement techniques and which do you use when?
* CSS property hacks, conditionally included .css files, or... something else?
* How do you serve your pages for feature-constrained browsers?
  * What techniques/processes do you use?
* What are the different ways to visually hide content (and make it available only for screen readers)?
  * **Answer**: Absolute positioning 0 height overflow hidden, or position overflow and move offscreen, or clip
* Have you ever used a grid system, and if so, what do you prefer?
  * **Answer**: Most reset css provides a grid system, like Bootstrap
* Have you used or implemented media queries or mobile specific layouts/CSS?
  * **Answer**: `@media (max-width: 600px) and (min-width: 700px) and (orientation: landscape)`
* Any familiarity with styling SVG?
* How do you optimize your webpages for print?
  * **Answer**: Separate CSS, can use `@media print`
* What are some of the "gotchas" for writing efficient CSS?
* What are the advantages/disadvantages of using CSS preprocessors? (SASS, Compass, Stylus, LESS)
  * If so, describe what you like and dislike about the CSS preprocessors you have used.
* How would you implement a web design comp that uses non-standard fonts?
  * Webfonts (font services like: Google Webfonts, Typekit etc.)
  * **Answer**: Can link external fonts like Google Webfonts or Adobe Edge Web Fonts
* Explain how a browser determines what elements match a CSS selector?

### Optional fun Questions:

* What's the coolest thing you've ever coded, what are you most proud of?
* What are your favorite parts about the developer tools you use?
* Do you have any pet projects? What kind?
* What's your favorite feature of Internet Explorer?
