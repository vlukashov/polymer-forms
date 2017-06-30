# HTML5 forms autocompletion

HTML forms autocompletion is a [standard](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#autofill) feature supported by all modern desktop and mobile browsers. It saves time when users return to web pages they have already visited earlier. It works especially well with login forms: the browser would automatically fill-in the username and password the user has used in the previous visit. That creates great UX and improves user engagement.

Bad news: this feature is broken in many ways for [Web Components](https://www.webcomponents.org/) (when the native [Shadow DOM](https://www.webcomponents.org/specs#the-shadow-dom-specification) is used).

Check the [live demo](https://vlukashov.github.io/polymer-forms/) to see how HTML forms autocompletion works (or does not) with and without the Shadow DOM.


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
