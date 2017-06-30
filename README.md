# HTML5 forms autocompletion

HTML forms autocompletion is a [standard](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#autofill) feature supported by all modern desktop and mobile browsers. It saves time when users return to web pages they have already visited earlier. It works especially well with login forms: the browser would automatically fill-in the username and password the user has used in the previous visit. That creates great UX and improves user engagement.

Bad news: this feature is broken in many ways for [Web Components](https://www.webcomponents.org/) (when the native [Shadow DOM](https://www.webcomponents.org/specs#the-shadow-dom-specification) is used).

Check the [live demo](https://vlukashov.github.io/polymer-forms/) to see how HTML forms autocompletion works (or does not) with and without the Shadow DOM.

## Investigation
The spec of HTML5 forms has many features. Some of them are used more often then others. This investigation focuses on 2 of them: [autocompletion](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#autofill) and [submit on 'Enter'](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#implicit-submission).

The table below summarizes how these features are supported by the to-date versions of the major browsers: Chrome, Firefox, Safari and IE11.

| Browser   | Autocompletion | Submit on 'Enter' |
|-----------|:--------------:|:-----------------:|
|Chrome 59  | within one DOM (main or shadow) | within one DOM (main or shadow) |
|Firefox 54 | across DOMs (shady) | across DOMs (shady) |
|Safari 10.1| only in the main DOM | within one DOM (main or shadow) |
|IE 11      | across DOMs (shady) | across DOMs (shady) |

Check it yourself live: https://vlukashov.github.io/polymer-forms/

See recorded videos: https://github.com/vlukashov/polymer-forms/tree/master/videos


### Feature: Autocompletion
Full spec: [forms autofill](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#autofill)

Chrome (supports Shadow DOM natively):
- Autocompletion attributes work fine if the entire HTML form with all its elements is inside **one DOM** (either the main document, or a shadow DOM).
- Autocompletion attributes do not work if the form and its elements are scattered across several Shadow DOMs (e.g. native form with paper-inputs).

Safari (supports Shadow DOM natively):
- Autocompletion attributes work fine if the entire HTML form with all its elements is inside the **main document** (but not if they all are inside one Shadow DOM).
- Autocompletion attributes do not work if the form and / or its elements are inside a Shadow DOM.

Firefox, IE11 (do not support Shadow DOM, need the Shady DOM polyfill)
- Autocompletion attributes work fine in all cases because from the browser perspective there is no Shadow DOM, only the main document.


### Feature: Submit on 'Enter'
Full spec: [implicit submit](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#implicit-submission)

Chrome, Safari (supports Shadow DOM natively):
- Submit on 'Enter' works fine if the entire HTML form with all its elements is inside **one DOM** (either the main document, or a shadow DOM).
- Submit on 'Enter' does not work if the form and its elements are scattered across several Shadow DOMs (e.g. native form with paper-inputs).

Firefox, IE11 (do not support Shadow DOM, need the Shady DOM polyfill)
- Submit on 'Enter' works fine in all cases because from the browser perspective there is no Shadow DOM, only the main document.


## Installing the demo locally

First, make sure you have [Node](https://nodejs.org/en/) and [NPM](https://www.npmjs.com/) installed. Clone the repo and then run `npm install` to get all dependencies required to run and build the app.

## Viewing the demo locally

```
$ npm start
```

## Building the demo for deployment

```
$ npm run build
```

This will create builds of the demo application in the `build/` directory, optimized to be served in production. The `build/es5` is the version deployed to the GitHub pages.
