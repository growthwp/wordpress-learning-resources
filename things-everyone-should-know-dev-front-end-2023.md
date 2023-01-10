# WordPress Development "Things Everyone Should Know" in 2023 (Front-end)

For simple use-cases, jQuery, together with React and using the core team's provided tooling will get most of the job done. However, if you're developing your own product, such as a page builder,
you are a full-fledged JS developer.

## Tooling

[TypeScript](https://www.typescriptlang.org/) - no project is written in vanilla JS anymore. You should be decent at it.
- You don't need to be able to write complex generics, but should understand what they are/be able to read them.
- Be acquaintanted with the more common utility types (Required, Omit, etc...)
- Understand how generics and types work together.

[ESLint](https://eslint.org/) - As with PHPCS, you want a tool that does auto-formatting, tells you about issues in your code and so on. However, this will most likely be setup for you.

[The JS debugger](https://developer.chrome.com/docs/devtools/javascript/reference/) - A life-saver. You can see what the value of each variable is, go through code call by call and so on. No more `console.log` hell.

[Jest](https://jestjs.io/) - Jest is a very nice (and, currently, the most popular) JS testing library. However, when it comes to React, there's also [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/), which I'd argue is useless for most people, but nice to know about in case you need testing for React components specifically.

[Building Tools](https://themeselection.com/javascript-build-tools/) - A build tool looks at your shiny code and transforms it such that browsers can understand it. Well, part of it! A build tool is able to that through plugins (in that case, Babel). Plugins vary wildly in scope, some clean JS code, some fix paths, some allow you for aliasing and so on. While this will be setup for you, you should be able to recognize when there's an issue in the code that could be solved by some Dev Ops changes. Don't need to understand this, but again, you should be able to understand how your code might end up looking/behaving differently than you think.

**CSS Tools/Paradigms** - Each company does as they see fit. Some use CSS-in-JS, some use CSS Components (the smart ones ;) ), some use a mix. It's expected of you to, at the very least, know about what these do, some of their limitations/benefits and be proficient with at least one approach, so that you can start work on something. Familiarity with all approaches makes onboarding easier. Alas, it's not **required** to know all of them, but it's required to know about them.

[Storybook](https://storybook.js.org/) - While you probably won't be writing stories yourself, you'll definitely interact with Storybook. Storybook is a tool that allows a team to put its UI library work (but not limited to) inside a system that allows for easy viewing/testing/adjusting for everyone to see.

## Libraries

[React Query](https://react-query-v3.tanstack.com/) - you'll need to talk a lot to the server, so, make sure you use a library that knows how to do that for you. While it's nice to have things such as auto-expiration, invalidation and cache, when it comes to WordPress, the requests you're making (that I can think of) don't really, really make use of these, they're there, but have no impact, **unless they do**! All in all, you should be fine without `react-query`, but should have something like `axios` ready to go. You don't want to be adding headers/managing requests using just `fetch` (atlhough, it's 2022, so, it's not really that bad).

[React](https://reactjs.org/) - Goes without saying. Everything and anything is React nowadays. The better understanding of the library you have, the merrier.

**State Management Libraries** - There's practically no big project that doesn't use some form of state management. Be it Mobx or Redux, it's always there. You should know about the higher-level ideas and what global state (together with its benefits and issues) is.

[Lodash](https://lodash.com/) - Nowadays, front-end work has become pretty involved. You'll need a library to help you with a lot of the heavy work when it comes to your objects/arrays. It's good to know some of the more used functions of `lodash` so that you don't have to (re)write them yourself.

When it comes to libraries, I can't identify anything else that *any* developer should know that are constant for every project. There are **very** popular libraries such as `lerna`.

## Closing Thoughts

It's 2022. Front-end work is very involved and complex. You're no different than a back-end developer. It's expected of you to know about data types/optimizations and know how to arrange your data such that it makes sense. I can't find any difference (in terms of complexity) between back-end and front-end work and, when it comes to WordPress, it's no different. In fact, I'd argue that, front-end really doesn't care about your overall architecture/back-end, it's always the same level of difficulty.

