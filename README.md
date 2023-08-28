# going-buildless
A short introduction to native web components.

Why should we leverage the built-in libraries of modern web browsers? To create native web-components which are interoperable and future-ready of course!

## The problems with React

These days, complex single page web applications are built by multiple teams.  I’ve worked at several clients where there is a team which manages the web app framework (the container) and then multiple teams deploy their React components within the container.  Following the pattern, teams can often make changes and release on demand (following good CI/CD practices) and expect the complex UI to still work.

The big problem comes when you want to update the React version.  By using React, the benefits of the framework come at the cost of a global namespace and the need for multiple teams to be tied to the current React version.  The container team often has to coordinate all other teams to upgrade in lockstep.

In addition, I’ve always followed the safe practice of prefixing my CSS with my team name or my unique container name, so I don’t clash with anyone else.  The same for my components.

In addition to the global scope of naming, I’ve often come across the complexity of global state (Redux anyone?).  Despite my best effort to keep my state private, someone always goes and subscribes to it, creating a dependency that is now out of my control and that I don’t have tests for.

Overall, programming web applications feels different to serverside programming because I’m no longer able to have well encapsulated software components, exposing only the behaviour I want them to while hiding the implementation.

## How did we get here with React?

Microsoft Internet Explorer.  The scourge of web devs in the naughties where we all had to collect our CSS workarounds to avoid this:

[<img src="css-is-awesome.png">](https://github.com/cpbirch/going-buildless)

But other browsers were just as bad.  Who remembers Opera?

The beauty of Facebook’s solution was to create a single framework which provided a Virtual DOM.  All manipulation by the developer was done and tested against the Virtual DOM provided by React, leaving React to create any workarounds or do other clever things so that the web application would render the same and work in web browsers which were most in use by the general public.

React has constantly been enhanced and improved over the years to be the helpful and dominant web application framework, used by me and thousands of developers all over the world.

But it’s been legacy code since 2019.  Why?

## The Shadow DOM

Since 2004, the W3C has had competition from https://whatwg.org/ - now the defacto web standards organisation.  Since 2011 the modern web components standards have been published by https://whatwg.org/ and available in Chrome and Firefox.  Since 2019, the standards have been implemented by Edge (>v72), Chrome, Firfox and Safari.  These standards cover javascript (ES6) and the DOM, and branched away from a single global DOM to use the Shadow DOM instead.

I love the Shadow DOM.  It makes programming web application feel like… well, programming.  Just like writing some Kotlin.  Or Python.  Using ES6 and the libraries / APIs built into modern browsers, I now have scoped variables and I have a scoped DOM.  I can write my web components with css styles which are contained within my component, having no effect outside it.  I can hide how my component is implemented but I can provide a clean interface to customise the component.  My component can store and manage it’s own state, I can determine which events I want to emit and which I want to keep contained.

Using Google’s small library ( https://lit.dev 5kb ) I can easily write native web components without boilerplate.  They can be deployed onto a shared UI without clashing with other components because they’re truly encapsulated.  Multiple teams can even upgrade lit.dev independently of each other because it’s also locally scoped and very lightweight.

But most of all, I love that I can write a bit of code, save it, reload it in the browser and see my change instantly.  No need to wait for a compilation step.  No complicated tooling.

## Try it for yourself

Open either of the two files (index.html or  zoe-list-item.js), make a change and save it.  Click reload in the browser and see the change instantly.

This demo is intended to be trivial but can easily be extended to use the Fetch API to get server side data which could then be rendered by a component.

