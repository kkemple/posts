# JavaScript At Scale - Achieving High Velocity

As developers and the creators of products, we strive to deliver a high quality solution that we can quickly and reliably adapt to the product's evolution. To me that is the only true measure of velocity and it seems I am not the only one who feels this way.

> “Velocity is the measure of your ability to adapt.” — Eric Elliott

Many companies choose JavaScript because it is touted as flexible and fast. While this may be true, that same flexibility and speed can get you in a few traps if you are not thoughtful in how you build your JavaScript ecosystem.

A few issues that come to mind are:

- Consistency across code bases
- Code reusability
- Avoiding complexity
- Ability to scale at well **at will?**
- Ability to confidently and quickly make changes to the codebase **<--this is redundant. this is what you're describing with the other points.**
- Ensuring that your third party tools and patterns enable high productivity

Having worked in a number of JavaScript heavy environments, I have seen just about every issue with scaling JavaScript applications, both on the client and on the server. What follows are all the things I wish someone told me when I started working with JavaScript [at scale]( http://addyosmani.com/largescalejavascript/).


## Some Guiding Practices/**Principles (your choice)**

Before we talk about JavaScript in context, there are some platform-independent things that can make your life much easier.

### Avoid Classical OO Patterns

JavaScript is powerful. It provides object composition with prototypal inheritance as well as functional programming. Using these two “Pillars of JavaScript” over classical OO patterns allow you to take better advantage of the power of JavaScript. The more composable and modular your application, the easier it will be for you to refactor and expand **(we're talking about scale here, so might as well say "expand")** in the future.

- [https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3#.83g2zvu9i](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3#.83g2zvu9i)
- [https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4#.pv154x5ca](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4#.pv154x5ca)


### Be Extremely Lazy

Currently there are over **200,000 modules** on NPM. Time is money; the more time you spend maintaining code that didn’t need to be written, the more expensive you are to your employers.

I’m referring to operational**(?)** services and tools as well (**i felt you need to be more specific here**). Don’t build your own analytics platform until you have scaled beyond what SaaS solutions like **Google Analytics**, **Mixpanel**, or **Keen.io** can provide. Using services to handle non product specific functionality allows you to focus on the unique thing that matters: the product.

Don’t waste time worrying about managing dependencies or other distractions. Move that work to third party solutions when possible. Use services like **greenkeeper.io** and **codeclimate.com** to ensure your software is not regressing and that your dependencies are up to date. This allows engineers to focus on generating value instead of managing code quality.

- [https://www.npmjs.com/](https://www.npmjs.com/)
- [http://greenkeeper.io/](http://greenkeeper.io/)
- [http://codeclimate.com](http://codeclimate.com)


### If You Do Nothing Else, Be Consistent

One of the biggest productivity killers is rummaging around in unfamiliar code. Use a style guide. Have identifiable patterns. The same style and patterns means new projects will feel familiar. **(When you make a point, state the shitty thing FIRST, then the good thing you're suggesting. That way you leave the reader with a positive impression.)**

I currently prefer Airbnb’s style guide. It has over 160 contributors and 169k downloads per month. They also have an ESLint plugin which means no configuration on your end unless you want to override something.

> Crowdsourcing your style guides gives you the benefit of using the current patterns and styles used by thousands of other JavaScript engineers.

Use a linter to ensure conformity among your team(s). **ESLint** is currently my favorite linter due to its plug-ability, as well as its continued support from the OS **(be more specific. do you mean all operating systems? or mac os? or something else?)** community. There are also plugins for ESLint for just about every text editor and IDE.

**Yeoman** allows you to take consistency to the next level by creating application templates that help you start each new project. This makes sure you use the same base dependencies, coding patterns, and styles for each application.

- [http://eslint.org/](http://eslint.org/)
- [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
- [https://scotch.io/tutorials/create-a-custom-yeoman-generator-in-4-easy-steps](https://scotch.io/tutorials/create-a-custom-yeoman-generator-in-4-easy-steps)


### Take Advantage of Tooling

JavaScript happens to have one of the best tooling ecosystems of any programming language. Take advantage of it! Some tools like **iron-node**, **react devtools**, and **redux devtools** simply can’t be replaced. If you are not using them, you are already losing time that could be better spent elsewhere. **(Again, reword this so that the shitty thing, which is the last sentence, is ahead of the good thing in this paragraph!)**

**Electron** and **React Native** provide access to native environments, allowing you to create applications for a multitude of platforms while getting large amounts of code reusability.

- [https://medium.com/javascript-scene/must-see-javascript-dev-tools-that-put-other-dev-tools-to-shame-aca6d3e3d925#.qztcau9fs](https://medium.com/javascript-scene/must-see-javascript-dev-tools-that-put-other-dev-tools-to-shame-aca6d3e3d925#.qztcau9fs)


### Keep Things As Small As Possible

Breaking up your applications into many smaller modules is the true key to composable JavaScript. Following the **FIRST** philosophy (Focused, Independent, Reusable, Small, Testable) helps keep down complexity while promoting testability and reuse.

> “Whether it’s a client or server-side component, a Node module or a piece of visual UI, components that are large are inherently more complex to maintain than those that are small.” — Addy Osmani

Remember that no piece of functionality is too small for a module. In fact, the smaller the module, the easier it will be to gain reuse from it.

- [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)
- [http://addyosmani.com/first/](http://addyosmani.com/first/)


### Use ES2015 (and beyond)

Use it for your APIs, your SPAs, and everything in between. **Babel**, my transpiler of choice, gives you a huge advantage. Being able to use something like **ES2105** today means you can build applications with smaller, cleaner code. Don’t let fear of vendor lock-in or the availability of these tools deter you from using them when they could save you more hours than you could possibly imagine. Babel has over 160 contributors and over 400 releases.

Just the difference in **LOC** (lines of code) is enough to show the value of using newer JavaScript features. The same functionality can be written in about 40% less LOC on average. **(Are you pulling 40% out of your ass? Someone will catch it. Provide a source.)**

There is no reason not to use Babel right now! Babel can handle plain old vanilla JavaScript right next to any other type of compiled code, meaning that you can migrate modules right back to plain ES5 at any time.

- [http://codemix.com/blog/why-babel-matters](http://codemix.com/blog/why-babel-matters)
- [https://medium.com/javascript-scene/how-to-use-es6-for-isomorphic-javascript-apps-2a9c3abe5ea2#.uo2p1hfir](https://medium.com/javascript-scene/how-to-use-es6-for-isomorphic-javascript-apps-2a9c3abe5ea2#.uo2p1hfir)


## JavaScript for APIs and Services

Building services that scale well with JavaScript is a daunting endeavor. Moving quickly and adapting to change gets tougher the larger your application grows. Be sure you are building services that are highly available and able to scale automatically.

### Create Infrastructure that Supports JavaScript Applications

JavaScript is single-threaded. This means that your application can only use a single CPU without clustering. I prefer to leave load balancing to proxies and load balancers like **ELB** or **NGINX** instead of Node’s cluster module, and I use smaller servers to run my applications. Then I can simply scale horizontally **by adding more machines (or whatever is better, you decide, but i think you need something here to be clear about what you mean by horizontally. you're trying to educate people.)** when more resources are needed. This helps minimize costs up front. If your services tend to be under a lot of load continuously it may make more sense to use beefier servers and a scheduler like **Kubernetes**.

- [https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_nodejs.html](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_nodejs.html)
- [http://kubernetes.io/](http://kubernetes.io/)


### Containerize! Containerize! Containerize!

A few of the many reasons why:

1. Containerization forces you to follow the 12 factor app principles of development. **(can you provide a link for more to this? i don't know what this is!)**
2. By containerizing your environment you allow for parity across development, staging, and production environments.
3. Containers are very easy to scale horizontally. **(if you mention above what this means, people will get it when they read this line.)**
4. You can easily move to other cloud providers. (Barring vendor lock-in to other supporting services.)

There are plenty of other reasons you should containerize your environment and it’s really not that hard once you get the basics. The headaches saved and the speed with which you can set up a new environment or release to production will quickly have you forgetting there was a time you didn’t use containers. **(<--this is your voice, but it is a little awkward sounding in an article. too conversational maybe?)**

- [http://mherman.org/blog/2015/03/06/node-with-docker-continuous-integration-and-delivery/#.VoQSGJMrKAx](http://mherman.org/blog/2015/03/06/node-with-docker-continuous-integration-and-delivery/#.VoQSGJMrKAx)
- [http://12factor.net/](http://12factor.net/)


### Build Applications that are Easy to Scale and Maintain

For my APIs and services I tend to use **Hapi** for the server itself, **Joi** for validation, and the **hapi-swagger** plugin for living documentation.

Hapi is built for modularity especially for larger applications, but it works just as well when spinning up a quick spike or simple application. What makes it so great is the encapsulation that Hapi provides. Hapi has “plugins” that are given access to the server through dependency injection. This way you can group your business logic cohesively. Breaking your application up in to these plugins makes it extremely easy to scale. Navigating the project becomes straight forward, as there is no custom plugin architecture to learn, just Hapi, which is well documented.

Joi is a validation module built by the same minds that built Hapi (Walmart Labs). Joi’s API and amazing features make validation a walk in the park. Because you can build validation schemas it’s very easy to create validation modules, the same code that can validate a form in your UI can also be used to validate an incoming request, a model, or tests. It’s really pretty amazing.

When you plug hapi-swagger into your server, you can simply tag any route as part of the API and it will create your living docs for you. Not to mention that hapi-swagger reads your Joi validations, providing developers with fine grained documentation on your API without any work from you. I imagine you can work this up with **Express** or **Koa** but I still find Hapi itself to be an amazing tool.

- [https://twitter.com/henrikjoreteg/status/666367990087073792](https://twitter.com/henrikjoreteg/status/666367990087073792)


## JavaScript for Web Applications

As with most other server side languages, there is no shortage of JavaScript frameworks that cover client-side applications. However, as with back-end applications and services, I prefer to use smaller modules and compose them together into a framework that supports scalability, maintainability, and reuse.

### Building the Client UI

For UI applications, I find **React** for the UI, **Redux** for state management, and **Joi** for data validation to be the most effective base for building scalable client applications that are easy to work through, as well as easy to test and debug (more on the amazing tooling for these libraries in a minute).

One thing I love about this combination is how easy they make following the “Two Pillars of JavaScript”. With React adding support for pure functions in v0.14, and Redux’s use of pure functions and composable reducers, the days of brittle applications using classical OO patterns are long gone.

Another huge win for this combination is the tooling that's available. Both React and Redux have a Chrome Developer Tools plugin that make debugging and walking through your application extremely simple. Supporting modules like **React Hot Loader** and **Webpack** make the feedback near instant. I suggest you give them both a hard look.

- [https://www.youtube.com/watch?v=xsSnOQynTHs](https://www.youtube.com/watch?v=xsSnOQynTHs)
- [http://gaearon.github.io/react-hot-loader/](http://gaearon.github.io/react-hot-loader/)
- [https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=en](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=en)
- [https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)


## JavaScript for Native Applications

There are really two types of native environments that you can build for: desktop and mobile. By using the following tools, you can reuse about 80% - 90% of any web based code to also build your native solutions. This gives you business logic parity across platforms while allowing you to reduce the amount of code you need to release your application across multiple platforms.

### Building for Desktop

When building for Desktop, not much changes from how I build for the web in general. Both are UIs so I tend to get a lot of reuse from my web based modules. The real difference is in the tools I use to package and release the applications.

For the application itself, I’m a big fan of **Electron**. Made by the team at Github, Electron offers a very simple solution to building cross-platform desktop applications. **Atom**, Github’s OS text editor is built on the Electron platform.

- [http://electron.atom.io/](http://electron.atom.io/)
- [https://medium.com/@Agro/developing-desktop-applications-with-electron-and-react-40d117d97564#.s16zpzohw](https://medium.com/@Agro/developing-desktop-applications-with-electron-and-react-40d117d97564#.s16zpzohw)
- [https://medium.com/developers-writing/building-a-desktop-application-with-electron-204203eeb658#.cx0mjvlxt](https://medium.com/developers-writing/building-a-desktop-application-with-electron-204203eeb658#.cx0mjvlxt)


## Building for Mobile

It’s going to come as no surprise that I recommend using React Native when it comes to build for mobile platforms. Currently React Native only supports iOS and Android platforms but unless you really need Windows support right now I suggest using React Native.

- [https://facebook.github.io/react-native/](https://facebook.github.io/react-native/)
- [https://medium.com/ios-os-x-development/an-ios-developer-on-react-native-1f24786c29f0#.7tcv13lhx](https://medium.com/ios-os-x-development/an-ios-developer-on-react-native-1f24786c29f0#.7tcv13lhx)
- [https://medium.com/@dean_mcpherson/townske-app-in-react-native-6ad557de7a7c#.mlfq4xsmx](https://medium.com/@dean_mcpherson/townske-app-in-react-native-6ad557de7a7c#.mlfq4xsmx)


## Testing JavaScript

I really like to focus tests around input and output. I only test the public APIs of my modules, never the internals. I find this much easier and more efficient.

### Keep the Feedback Loop Small

Having a full suite of tests for your application is a necessity; however, with great coverage comes lengthy test executions. Shave off a few seconds by only running your unit tests locally and running integration and end-to-end tests during the build process. This will provide the same confidence in code quality before you ship while allowing you to develop quickly.

### Only Test Public APIs

By not concerning ourselves with any internals we are free to change them at will, as long as we don’t break the public API of that module. This means tests need to change less frequently and you can be sure that you are receiving exactly what you should receive in your application.
- [https://en.wikipedia.org/wiki/Black-box_testing](https://en.wikipedia.org/wiki/Black-box_testing)

### Building a Testing Framework

As far as actually testing modules, lately I have been a big fan of **tape** and **nock**. With just those two modules I am able to cover about 99% of my tests (sometimes I want to spy on something and use Sinon). Hapi has the inject method on the server that allows you to do end-to-end testing without running the application. (This can be accomplished with Express and the supertest module.)

For end-to-end testing I use Nightmare. I try to keep my number of end-to-end tests as low as possible and only run them, and integration tests, during builds. Only running unit tests locally will provide you with faster feedback.

- [https://medium.com/javascript-scene/why-i-use-tape-instead-of-mocha-so-should-you-6aa105d8eaf4#.x144okjng](https://medium.com/javascript-scene/why-i-use-tape-instead-of-mocha-so-should-you-6aa105d8eaf4#.x144okjng)

- [https://ericelliottjs.com/product/tdd-es6-react/](https://ericelliottjs.com/product/tdd-es6-react/)

- [http://www.nightmarejs.org/](http://www.nightmarejs.org/)


## Final Thoughts

JavaScript offers some unique benefits and makes a great candidate for building applications on any platform. JavaScript is probably the most important language you can know right now, because it can be run virtually anywhere and can be written in highly reusable, composable ways.

However, those unfamiliar with the differences and “gotchas” of JavaScript may quickly find that making changes to the codebase is not as easy as it once was and changes seem to have adverse and unexpected results.

Don’t get caught caught up in writing applications like you do for other languages. Make the most of what JavaScript has to offer and work towards small and simple modules. This will help keep you sane and your love for JavaScript strong!

I would love to know how others achieve velocity and keep JavaScript heavy environments running smoothly. Please share your processes and modules of choice in the comments below!

Happy JavaScripting!
