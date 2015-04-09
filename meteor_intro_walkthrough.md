# Meteor Intro Walkthrough

Go to http://serixscorpio.meteor.com/.  This is an example of a simple hacker news clone built in meteor.

source: https://github.com/serixscorpio/microscope

### Magical Meteor
The most fascinating aspect of Meteor, I think, is _reactive templating_.  It means when you change some source of information in Meteor, it is immediately reflected in your template.  An example is multiple people collaborating on a google doc.  You can see what other people are typing in while they are typing without the need to reload.  That's _reactivity_.

### Start with a Demo App
1. Assuming meteor is already [installed](https://www.meteor.com/install):
```bash
> meteor create mdemo
> cd mdemo
```
1. In this directory, there are 3 files (`mdemo.css`, `mdemo.html`, and `mdemo.js`) plus a hidden directory `.meteor` that contains meteor related stuff.

1. Take a look at the html. It has a title, and a single __template__ named `hello`.
1. Let's run this app and see what happens:
```bash
> meteor
[[[[[ ~/code/mdemo ]]]]]
...
=> App running at: http://localhost:3000/
```
1. Open `http://localhost:3000/` on a browser. How does this corresponds to the html?
   * The braces and angle bracket syntax `{{> hello}}` means: go find a template called `hello`, and stick whatever is in that template here.
   * The template is defined using the `tempalte` tag, with a name attribute called `hello`.
   * `{{counter}}` refers to something in the javascript code (see `mdemo.js`)
1. Template helpers
   * In `mdemo.js`, there is a call to `Template.hello.helpers(...)`.  In the parameter, we can specify a dictionary of helper functions by name.  A helper function named `foo` can be used within the template using the `{{foo}}` syntax.  [More details about template helpers](http://docs.meteor.com/#/full/template_helpers).
1. Session variable
   * `Session` is a client-side global object that can be used for storing arbitrary key-value pairs.
1. Open up a browser console, and enter `Session.set({counter: 1})`.  Notice in the browser, it automatically updates the counter from 0 to 1 without a page reload.
1. This brings us to __reactive templating__ terminology.
   * __reactive source__ (__reactive data__): Making a javascript object reactive is like training a dog to bark if it feels a need to pee.  If something inside the javascript object changes, you want to be notified whenever something inside it changes.
   * __reactive computations__ (__reactive contexts__): When a dog barks, you want to be around to take the dog outside.  Otherwise it'd be pointless to train the dog.  Similarly, a reactive source needs something to 'listen' to its notifications.  A reactive computation is a block of code that will _re-run whenever a reactive source within the block changes_.
   * Session variabls are __reactive sources__
   * Template helpers are __reactive computations__
   * putting these two concepts together: the `counter` helper will re-run whenever the `counter` Session variable changes.  This is the basis of Meteor's reactivity.

### If time permits ...
1. talk about reactive composition

### References
1. [Naomi Seyfer: Meteor 101 - Meteor Devshop 2](https://www.youtube.com/watch?v=lSAKFkxq4jA&spfreload=10)
1. [Reactivity Basics: Meteor's Magic Demystified](https://www.discovermeteor.com/blog/reactivity-basics-meteors-magic-demystified/)
1. [Reactivity with Contexts](https://www.eventedmind.com/feed/meteor-reactivity-with-contexts)
