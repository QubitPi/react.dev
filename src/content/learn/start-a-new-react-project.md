---
title: Start a New React Project
---

<Intro>

If you want to build a new app or a new website fully with React, we recommend picking one of the React-powered frameworks popular in the community. Frameworks provide features that most apps and sites eventually need, including routing, data fetching, and generating HTML.

</Intro>

<Note>

**You need to install [Node.js](https://nodejs.org/en/) for local development.** You can *also* choose to use Node.js in production, but you don't have to. Many React frameworks support export to a static HTML/CSS/JS folder.

</Note>

## Production-grade React frameworks {/*production-grade-react-frameworks*/}

### Next.js {/*nextjs*/}

**[Next.js](https://nextjs.org/) is a full-stack React framework.** It's versatile and lets you create React apps of any size--from a mostly static blog to a complex dynamic application. To create a new Next.js project, run in your terminal:

<TerminalBlock>
npx create-next-app
</TerminalBlock>

If you're new to Next.js, check out the [Next.js tutorial.](https://nextjs.org/learn/foundations/about-nextjs)

Next.js is maintained by [Vercel](https://vercel.com/). You can [deploy a Next.js app](https://nextjs.org/docs/deployment) to any Node.js or serverless hosting, or to your own server. [Fully static Next.js apps](https://nextjs.org/docs/advanced-features/static-html-export) can be deployed to any static hosting.

### Remix {/*remix*/}

**[Remix](https://remix.run/) is a full-stack React framework with nested routing.** It lets you break your app into nested parts that can load data in parallel and refresh in response to the user actions. To create a new Remix project, run:

<TerminalBlock>
npx create-remix
</TerminalBlock>

If you're new to Remix, check out the Remix [blog tutorial](https://remix.run/docs/en/main/tutorials/blog) (short) and [app tutorial](https://remix.run/docs/en/main/tutorials/jokes) (long).

Remix is maintained by [Shopify](https://www.shopify.com/). When you create a Remix project, you need to [pick your deployment target](https://remix.run/docs/en/main/guides/deployment). You can deploy a Remix app to any Node.js or serverless hosting by using or writing an [adapter](https://remix.run/docs/en/main/other-api/adapter).

### Gatsby {/*gatsby*/}

**[Gatsby](https://www.gatsbyjs.com/) is a React framework for fast CMS-backed websites.** Its rich plugin ecosystem and its GraphQL data layer simplify integrating content, APIs, and services into one website. To create a new Gatsby project, run:

<TerminalBlock>
npx create-gatsby
</TerminalBlock>

If you're new to Gatsby, check out the [Gatsby tutorial.](https://www.gatsbyjs.com/docs/tutorial/)

Gatsby is maintained by [Netlify](https://www.netlify.com/). You can [deploy a fully static Gatsby site](https://www.gatsbyjs.com/docs/how-to/previews-deploys-hosting) to any static hosting. If you opt into using server-only features, make sure your hosting provider supports them for Gatsby.

### Expo (for native apps) {/*expo*/}

**[Expo](https://expo.dev/) is a React framework that lets you create universal Android, iOS, and web apps with truly native UIs.** It provides an SDK for [React Native](https://reactnative.dev/) that makes the native parts easier to use. To create a new Expo project, run:

<TerminalBlock>
npx create-expo-app
</TerminalBlock>

If you're new to Expo, check out the [Expo tutorial](https://docs.expo.dev/tutorial/introduction/).

Expo is maintained by [Expo (the company)](https://expo.dev/about). Building apps with Expo is free, and you can submit them to the Google and Apple app stores without restrictions. Expo additionally provides opt-in paid cloud services.

<DeepDive>

#### Can I use React without a framework? {/*can-i-use-react-without-a-framework*/}

You can definitely use React without a framework--that's how you'd [use React for a part of your page.](/learn/add-react-to-an-existing-project#using-react-for-a-part-of-your-existing-page) **However, if you're building a new app or a site fully with React, we recommend using a framework.**

Here's why.

Even if you don't need routing or data fetching at first, you'll likely want to add some libraries for them. As your JavaScript bundle grows with every new feature, you might have to figure out how to split code for every route individually. As your data fetching needs get more complex, you are likely to encounter server-client network waterfalls that make your app feel very slow. As your audience includes more users with poor network conditions and low-end devices, you might need to generate HTML from your components to display content early--either on the server, or during the build time. Changing your setup to run some of your code on the server or during the build can be very tricky.

**These problems are not React-specific. This is why Svelte has SvelteKit, Vue has Nuxt, and so on.** To solve these problems on your own, you'll need to integrate your bundler with your router and with your data fetching library. It's not hard to get an initial setup working, but there are a lot of subtleties involved in making an app that loads quickly even as it grows over time. You'll want to send down the minimal amount of app code but do so in a single client–server roundtrip, in parallel with any data required for the page. You'll likely want the page to be interactive before your JavaScript code even runs, to support progressive enhancement. You may want to generate a folder of fully static HTML files for your marketing pages that can be hosted anywhere and still work with JavaScript disabled. Building these capabilities yourself takes real work.

**React frameworks on this page solve problems like these by default, with no extra work from your side.** They let you start very lean and then scale your app with your needs. Each React framework has a community, so finding answers to questions and upgrading tooling is easier. Frameworks also give structure to your code, helping you and others retain context and skills between different projects. Conversely, with a custom setup it's easier to get stuck on unsupported dependency versions, and you'll essentially end up creating your own framework—albeit one with no community or upgrade path (and if it's anything like the ones we've made in the past, more haphazardly designed).

If you're still not convinced, or your app has unusual constraints not served well by these frameworks and you'd like to roll your own custom setup, we can't stop you--go for it! Grab `react` and `react-dom` from npm, set up your custom build process with a bundler like [Vite](https://vitejs.dev/) or [Parcel](https://parceljs.org/), and add other tools as you need them for routing, static generation or server-side rendering, and more.
</DeepDive>

## Bleeding-edge React frameworks {/*bleeding-edge-react-frameworks*/}

As we've explored how to continue improving React, we realized that integrating React more closely with frameworks (specifically, with routing, bundling, and server technologies) is our biggest opportunity to help React users build better apps. The Next.js team has agreed to collaborate with us in researching, developing, integrating, and testing framework-agnostic bleeding-edge React features like [React Server Components.](/blog/2023/03/22/react-labs-what-we-have-been-working-on-march-2023#react-server-components)

These features are getting closer to being production-ready every day, and we've been in talks with other bundler and framework developers about integrating them. Our hope is that in a year or two, all frameworks listed on this page will have full support for these features. (If you're a framework author interested in partnering with us to experiment with these features, please let us know!)

### Next.js (App Router) {/*nextjs-app-router*/}

**[Next.js's App Router](https://beta.nextjs.org/docs/getting-started) is a redesign of the Next.js APIs aiming to fulfill the React team’s full-stack architecture vision.** It lets you fetch data in asynchronous components that run on the server or even during the build.

Next.js is maintained by [Vercel](https://vercel.com/). You can [deploy a Next.js app](https://nextjs.org/docs/deployment) to any Node.js or serverless hosting, or to your own server. Next.js also supports [static export](https://beta.nextjs.org/docs/configuring/static-export) which doesn't require a server.
<Pitfall>

Next.js's App Router is **currently in beta and is not yet recommended for production** (as of Mar 2023). To experiment with it in an existing Next.js project, [follow this incremental migration guide](https://beta.nextjs.org/docs/upgrade-guide#migrating-from-pages-to-app).

</Pitfall>

<DeepDive>

#### Which features make up the React team’s full-stack architecture vision? {/*which-features-make-up-the-react-teams-full-stack-architecture-vision*/}

Next.js's App Router bundler fully implements the official [React Server Components specification](https://github.com/reactjs/rfcs/blob/main/text/0188-server-components.md). This lets you mix build-time, server-only, and interactive components in a single React tree.

For example, you can write a server-only React component as an `async` function that reads from a database or from a file. Then you can pass data down from it to your interactive components:

```js
// This component runs *only* on the server (or during the build).
async function Talks({ confId }) {
  // 1. You're on the server, so you can talk to your data layer. API endpoint not required.
  const talks = await db.Talks.findAll({ confId });

  // 2. Add any amount of rendering logic. It won't make your JavaScript bundle larger.
  const videos = talks.map(talk => talk.video);

  // 3. Pass the data down to the components that will run in the browser.
  return <SearchableVideoList videos={videos} />;
}
```

Next.js's App Router also integrates [data fetching with Suspense](/blog/2022/03/29/react-v18#suspense-in-data-frameworks). This lets you specify a loading state (like a skeleton placeholder) for different parts of your user interface directly in your React tree:

```js
<Suspense fallback={<TalksLoading />}>
  <Talks confId={conf.id} />
</Suspense>
```

Server Components and Suspense are React features rather than Next.js features. However, adopting them at the framework level requires buy-in and non-trivial implementation work. At the moment, the Next.js App Router is the most complete implementation. The React team is working with bundler developers to make these features easier to implement in the next generation of frameworks.

</DeepDive>

## Create Monorepo from Scratch {/*create-monorepo-from-scratch*/}

There are a couple of hurdles to starting a React [monorepo](https://qubitpi.github.io/monorepo.tools/). The first is that node can't process all of the syntax (such as import/export and [JSX][JSX]). The second is that we will either need to build our files or serve them somehow during development for our app to work - This is especially important in the latter situations. These issues with be handled by [Babel][Babel] and [Webpack][webpack], which we cover below

### Setup {/*setup*/}

To get started, create a new directory for our new React monorepo. Inside the monorepo directory, initialize a project with

<TerminalBlock>

yarn init

</TerminalBlock>

Thinking ahead a little bit, we'll eventually want to build our app and we'll probably want to exclude the built version and our node modules from commits, so let's go ahead and, at the root level of the monorepo, add a `.gitignore` file excluding (at least) the`node_modules`, `dist`, etc:

```gitignore
dist
/build
.DS_Store
/coverage
node_modules

.env.

npm-debug.log*
yarn-debug.log*
yarn-error.log*
```

We need to install react now:

```bash
yarn add react react-dom
```

Note that we do save those as _regular_ dependencies, i.e. without `--save-dev` option.

Next, in the new project folder, create the following directory:

```
mkdir -p packages/app/
```

Next, create the following structure inside `packages/app/`

```
.
+-- public
+-- src
```

Our `public` directory will handle any static assets, and most importantly houses our `index.html` file, which react will utilize to render our app. The following code is an example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
    <meta name="theme-color" content="#000000" />
    <link rel="manifest" href="./manifest.json" />
    <link rel="shortcut icon" href="./favicon.ico" />
    <title>My App</title>
</head>

<body>
<noscript> You need to enable JavaScript to run this app. </noscript>
<div id="root"></div>
</body>
</html>
```

The `manifest.json` and `favidon.ico` will be placed in the same directory as the `index.html`, i.e. the `public` directory.

> [The `manifest.json` provides metadata](https://developers.google.com/web/fundamentals/web-app-manifest/) used when
> our web app is installed on a user's mobile device or desktop.

#### packages/app/src/App.tsx {/*packagesappsrcapptsx*/}

The TypeScript code in **App.tsx** creates our **root component**. In React, a root component is a tree of child components that represents the whole user interface:

```typescript
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";

import MyHomeComponent from "somePathTo/MyHomeComponent";
import MySettingsPageComponent from "somePathTo/MySettingsPageComponent";

export default function App(): JSX.Element {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<MyHomeComponent />} />
        <Route path="/settings" element={<MySettingsPageComponent />} />
      </Routes>
    </Router>
  );
}
```

#### packages/app/src/index.tsx {/*packagesappsrcindextsx*/}

**index.tsx** is the bridge between the root component and the web browser.

```typescript
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root") as HTMLElement);
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

#### packages/app/src/index.css {/*packagesappsrcindexcss*/}

This file defines the styles for our React app. Here is an example:

```css
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans",
    "Droid Sans", "Helvetica Neue", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New", monospace;
}
```

Now that we've got our HTML page set up, we can start getting serious. We're going to need to set up a few more things. First, we need to make sure the code we write can be compiled, so we'll need [Babel][Babel], which we discuss next.

### Babel {/*babel*/}

Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers or environments. For example, Babel transforms syntax:

```javascript
// Babel Input: ES2015 arrow function
[1, 2, 3].map(n => n + 1);

// Babel Output: ES5 equivalent
[1, 2, 3].map(function(n) {
  return n + 1;
});
```

To install Babel in our project, **go to the top directory of our monorepo project** and run

<TerminalBlock>

yarn add -D @babel/core @babel/cli @babel/preset-env @babel/preset-react @babel/preset-typescript

</TerminalBlock>

`@babel/core` is the main babel package - We need this for babel to do any transformations on our code. `@babel/cli` allows us to compile files from the command line. `preset-env` and `preset-react` are both presets that transform specific flavors of code - in this case, the `env` preset allows us to transform ES6+ into more traditional javascript and the react preset does the same, but with JSX instead. `@babel/preset-typescript` is used by [Jest we setup later](#jest), because we will need to transpile Jest into TypeScript via [Babel][Babel]

The following 2 links explains in details why the 4 dependencies above are needed in our react app:

- [@babel/core @babel/cli @babel/preset-env](https://qubitpi.github.io/babel-website/docs/usage#overview)
- [@babel/preset-react](https://babeljs.io/docs/#jsx-and-react)

In the project root, create a Babel configuration file called **babel.config.js**. Here, we're telling babel that we're using the `env` and `react` presets (and some [typescript support for Jest testing](https://jestjs.io/docs/getting-started#using-typescript) which we discuss later):

```javascript
module.exports = function() {
  const presets = ["@babel/preset-env", "@babel/preset-react", "@babel/preset-typescript"]

  return { presets };
}
```

### TypeScript {/*typescript*/}

We integrate TypeScript by **going to the top directory of our monorepo project and running**

<TerminalBlock>

yarn add -D typescript

</TerminalBlock>

Let's set up a configuration to support JSX and compile TypeScript down to ES5 by creating a file called **tsconfig.json** in project root directory with the content of:

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "jsx": "react-jsx",
    "strict": true,
    "allowJs": true,
    "outDir": "./dist/",
    "noImplicitAny": true,
    "esModuleInterop": true,
    "moduleResolution": "node",
    "allowSyntheticDefaultImports": true
  },
  "include": ["packages"]
}
```

See [TypeScript's documentation](https://qubitpi.github.io/TypeScript-Website/tsconfig) to learn more about _tsconfig.json_ configuration options. The thing we need to mention here is the `"jsx": "react-jsx"` option. In short, [`react-jsx` is a more-modern option compared to other such as old `react`](https://stackoverflow.com/a/73518971/14312712) and we will use this newer feature.

### Jest {/*jest*/}

Let's jump into test setup with [Jest][Jest]. **At the monorepo root directory** run

<TerminalBlock>

yarn add -D jest babel-jest @types/jest ts-jest react-test-renderer @testing-library/react @testing-library/jest-dom

</TerminalBlock>

<Pitfall>

[There is a bug in Jest version 28](https://stackoverflow.com/a/73757948/14312712) and we need to make sure to **downgrade jest to some 27 version**. At the time of writing, the following versions work:

```json
"@types/jest": "^27.5.2",
"jest": "^27.4.3",
"ts-jest": "^27.1.4",
"babel-jest": "^27.4.2",
```

</Pitfall>

Jest transpiles TypeScripts before running test harness. We will need a configuration file to specify how TypeScript is going to be transpiled. The file name is **jest.config.json**:

```json
{
    "preset": "ts-jest",
    "testEnvironment": "jsdom",
    "setupFilesAfterEnv": ["<rootDir>/scripts/jest/setupTests.ts"],
    "transform": {
        "^.+\\.[t|j]sx?$": "babel-jest",
        "^.+\\.css$": "<rootDir>/config/jest/cssTransform.js",
        "^(?!.*\\.(js|jsx|mjs|cjs|ts|tsx|css|json)$)": "<rootDir>/config/jest/fileTransform.js"
    },
    "moduleNameMapper": {
        "^.+\\.module\\.(css|sass|scss)$": "identity-obj-proxy"
    }
}
```

- `"preset": "ts-jest"` and `"testEnvironment": "jsdom"` are neede by [ts-jest config][ts-jest config]
- `setupFilesAfterEnv`: This is related to the `@testing-library/jest-dom` dependency. In terms of Jest configuration, rather than import it in every test file it is better to do it in the Jest config file via the `setupFilesAfterEnv` option and then we will have a **setupTests.ts** file located inside `scripts/jest` directory with the following content

  ```javascript
  import "@testing-library/jest-dom";
  ```

- `"^.+\\.css$": "<rootDir>/config/jest/cssTransform.js",`: This was taken from an [ejected CRA](https://create-react-app.dev/docs/available-scripts#npm-run-eject) that specifies how to mock out CSS imports. We should have a file called `cssTransform.js` under `<rootDir>/config/jest/` directory with the following contents:

  <Pitfall>

  [create-react-app][create-react-app] abstracts a lot of what makes a React app work away from us - at least without ejecting it and having to tweak all of the options by hand. There are a number of reasons we may want to make our own implementation, or at least have some idea of what it's doing under the hood. **Most importantly,[create-react-app][create-react-app] is more like a "Spring Boot" in the Front End world. Those who dislike the Spring for offering quick startup but terrible customizability later might find [create-react-app][create-react-app] very frustrating.**

  </Pitfall>

  ```javascript
  "use strict";
  
  module.exports = {
    process() {
      return "module.exports = {};";
    },
    getCacheKey() {
      // The output is always the same.
      return "cssTransform";
    },
  };
  ```

  Similarly, the next line specifies file mock (same location with file name of `fileTransform.js`):

  ```javascript
  "use strict";
  
  const path = require("path");
  const camelcase = require("camelcase");
  
  // This is a custom Jest transformer turning file imports into filenames.
  // http://facebook.github.io/jest/docs/en/webpack.html
  
  module.exports = {
    process(src, filename) {
      const assetFilename = JSON.stringify(path.basename(filename));
  
      if (filename.match(/\.svg$/)) {
        // Based on how SVGR generates a component name:
        // https://github.com/smooth-code/svgr/blob/01b194cf967347d43d4cbe6b434404731b87cf27/packages/core/src/state.js#L6
        const pascalCaseFilename = camelcase(path.parse(filename).name, {
          pascalCase: true,
        });
        const componentName = `Svg${pascalCaseFilename}`;
        return `const React = require('react');
        module.exports = {
          __esModule: true,
          default: ${assetFilename},
          ReactComponent: React.forwardRef(function ${componentName}(props, ref) {
            return {
              $$typeof: Symbol.for('react.element'),
              type: 'svg',
              ref: ref,
              key: null,
              props: Object.assign({}, props, {
                children: ${assetFilename}
              })
            };
          }),
        };`;
      }
  
      return `module.exports = ${assetFilename};`;
    },
  };
  ```

- `"^.+\\.module\\.(css|sass|scss)$": "identity-obj-proxy"`: [Mocking CSS Modules](https://jestjs.io/docs/webpack#mocking-css-modules)

#### Additional Jest References {/*additional-jest-references*/}

- [General](https://jestjs.io/docs/getting-started)
- [ts-jest config][ts-jest config]
- [Setup without Create React App](https://jestjs.io/docs/tutorial-react#setup-without-create-react-app)
    - [DOM Testing](https://jestjs.io/docs/tutorial-react#dom-testing)
    - [Property 'toBeInTheDocument' does not exist](https://stackoverflow.com/a/61636112/14312712)
- [Jest - Handling Static Assets](https://jestjs.io/docs/webpack#handling-static-assets)

### Webpack {/*webpack*/}

We configure [Webpack][webpack] now. We'll need a few more packages as dev dependencies. Run the following commands
**at the root directory of our monorepo**:

<TerminalBlock>

yarn add -D webpack webpack-cli webpack-dev-server style-loader css-loader babel-loader

</TerminalBlock>

#### Setup [Webpack Dev Server][webpack dev server] {/*setup-webpack-dev-serverwebpack-dev-server*/}

We've mentioned previously the need to "build our files or serve them somehow during development for our app to work". Essentially, we will need to achieve this by enabling `yarn start` command using [Webpack Dev Server][webpack dev server]. First, we put a config file of it under `config/webpack` called **webpack.config.js**:

```javascript
const path = require("path");
const webpack = require("webpack");
const HtmlWebpackPlugin = require("html-webpack-plugin");

const imageInlineSizeLimit = parseInt(process.env.IMAGE_INLINE_SIZE_LIMIT || "10000");

module.exports = function (webpackEnv) {
  const isDevEnvironment = webpackEnv === "development";
  const isProdEnvironment = webpackEnv === "production";

  return {
    entry: "./src/index.tsx",
    mode: isProdEnvironment ? "production" : "development",
    output: {
      publicPath: "/",
      path: path.resolve(__dirname, "dist"),
      filename: isProdEnvironment ? "static/js/[name].[contenthash:8].js" : "static/js/bundle.js",
    },
    module: {
      rules: [
        {
          test: /\.(js|mjs|jsx|ts|tsx)$/,
          exclude: /(node_modules|bower_components)/,
          loader: "babel-loader",
          options: { presets: ["@babel/env"] },
        },
        {
          test: /\.css$/,
          use: ["style-loader", "css-loader"],
        },
        {
          test: [/\.bmp$/, /\.gif$/, /\.jpe?g$/, /\.png$/, /\.webp$/],
          type: "asset",
          parser: {
            dataUrlCondition: {
              maxSize: imageInlineSizeLimit,
            },
          },
        },
      ],
    },
    plugins: [
      new webpack.HotModuleReplacementPlugin(),
      // Generates an `index.html` file with the <script> injected.
      new HtmlWebpackPlugin(
        Object.assign(
          {},
          {
            inject: true,
            template: "./public/index.html",
          },
          isProdEnvironment
            ? {
                minify: {
                  removeComments: true,
                  collapseWhitespace: true,
                  removeRedundantAttributes: true,
                  useShortDoctype: true,
                  removeEmptyAttributes: true,
                  removeStyleLinkTypeAttributes: true,
                  keepClosingSlash: true,
                  minifyJS: true,
                  minifyCSS: true,
                  minifyURLs: true,
                },
              }
            : undefined
        )
      ),
    ],
    resolve: {
      extensions: [".ts", ".tsx", ".js", ".json"],
    },
  };
};
```

`entry` tells Webpack where our application starts and where to start bundling our files. The following line lets webpack know whether we're working in development mode or production build mode. This saves us from having to add a mode flag when we run the development server.

The `module` object helps define how our exported javascript modules are transformed and which ones are included according to the given array of rules.

Our first rule is all about transforming ES6 and JSX syntax. The test and exclude properties are conditions to match file against. In this case, it'll match anything outside of the `node_modules` and `bower_components` directories. Since we'll be transforming our `.js` and `.jsx` files as well, we’ll need to direct Webpack to use [Babel][Babel]. Finally, we specify that we want to use the `env` preset in options.

The next rule is for processing CSS. Since we're not pre-or-post-processing our CSS, we just need to make sure to add`style-loader` and `css-loader` to the use property. `css-loader` requires `style-loader` in order to work.

We want to use [Hot Module Replacement][Hot Module Replacement] so that we don't have to constantly refresh to see our changes. All we do for that in terms of this file is instantiate a new instance of the plugin in the plugins property, i.e. `new webpack.HotModuleReplacementPlugin()`

We need to add an `index.html` to our webpak config, so it can work with it; otherwise webpack-dev-server will simply get us a blank screen with `yarn start`[^1]. We use [html-webpack-plugin][html-webpack-plugin] for this.

```bash
yarn add -D html-webpack-plugin
```

The `new HtmlWebpackPlugin(...)` snippet above was taking from an ejected [CRA][create-react-app].

The `resolve` property allows us to specify which extensions Webpack will resolve - this allows us to import modules without needing to add their extensions[^2]. For example, we can safely put

```javascript
import App from "./App"
```

when we have a file `App.tsx`. Without `resolve` above, import above will throw a runtime-error because only `App.js`can be imported without specifying an extension.

We are going to use [dev-server][webpack dev server] through the Node.js API. But before we proceed, it is worth mentioning that the `webpack.config.js` file above does not have the `devServer` field.

<Pitfall>

If we do not use Node.js API, [`devServer` and its configs comes inside `webpack.config.js` file](https://webpack.js.org/configuration/dev-server/)

</Pitfall>

Because the field is ignored if we run dev server using Node.js API. We will, instead, pass the options as the first parameter: `new WebpackDevServer({...}, compiler)`. For separation of concerns, the option is defined in yet another config file called **webpackDevServer.config.js** (located in the same directory as webpack.config.js) and this file will be imported in Node.js API file:

```javascript
"use strict";

module.exports = function () {
  return {
    historyApiFallback: true,
  };
};
```

<Note>

The `historyApiFallback: true` above combined with the `publicPath: "/"` from the webpack.config.js file shall, if we have router defined in our app, enable page refresh on the flight. Otherwise, a 404 error on sub-router page refresh will occur[^enabling-routed-page-refresh-with-webpack].

Please checkout [Server-side rendering vs Client-side rendering][Server-side rendering vs Client-side rendering] for more background discussion.

Finally, here is our Node.js API file:

</Note>

```javascript
"use strict";

const configFactory = require("../config/webpack/webpack.config");
const devServerConfig = require("../config/webpack/webpackDevServer.config");

const Webpack = require("webpack");
const WebpackDevServer = require("webpack-dev-server");
const webpackConfig = configFactory("development");

const compiler = Webpack(webpackConfig);
const devServerOptions = { ...devServerConfig(), open: true };
const server = new WebpackDevServer(devServerOptions, compiler);

server.startCallback(() => {
  console.log("Starting server on http://localhost:8080");
});
```

We put this in `scripts/start.js` so that we will be able to call this script during `yarn start` by adding the following line to `package.json`:

```json
"scripts": {
  "start": "node scripts/start.js",
  ...
},
```

#### Creating a Production Build {/*creating-a-production-build*/}

We will use `yarn build` to create a `build` directory with a production build of our app. Inside the `build/static` directory will be our JavaScript and CSS files. Each filename inside of `build/static` will contain a unique hash of the file contents. This hash in the file name enables long term caching techniques, which allows us to use [aggressive caching techniques](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching#invalidating_and_updating_cached_responses) to avoid the browser re-downloading our assets if the file contents haven't changed. If the contents of a file changes in a subsequent build, the filename hash that is generated will be different.

```javascript
"use strict";

const Webpack = require("webpack");
const configFactory = require("../config/webpack/webpack.config");
const webpackConfig = configFactory("production");

const compiler = Webpack(webpackConfig);

console.log("Creating an optimized production build...");

compiler.run();
```

We put this in `scripts/build.js` so that we will be able to call this script during `yarn build` by adding the following line to `package.json`:

```json
"scripts": {
  ...
  "build": "node scripts/build.js",
  ...
},
```

### Project Configuration Management {/*project-configuration-management*/}

This document describes Configuration Management for Nexus Graph.

#### Context {/*context*/}

Configuration management is essential for every application that will be deployed into multiple environments, which is pretty much the majority of Apps and APIs. Focusing on React Apps in this post, we will cover how to store configurations in Nexus Graph, how to configure them, and finally how to read them.

#### Configuration Types {/*configuration-types*/}

There are different types of configurations in Nexus Graph

##### Environment Dependent {/*environment-dependent*/}

Those are configurations that change from one environment to the other. A good example would be FQDNs (Fully Qualified Domain Names). A URL in local dev environment, might point to `https://localhost:6500`, however the same URL in production, would point to `https://theresa-api.com`.

###### Storing Environment Dependent Configs {/*storing-environment-dependent-configs*/}

The way we manage these types of configurations is through **env files**. We maintain a separate env file for each environment.

We have:

- **.env**: for local dev environment
- **.env.test**: for test environment
- **.env.production**: for production

When the application is packaged for each environment by WebPack, the right configuration file will be picked up. The content of such file is key-value pair, such as below:

```conf
HTTPS=true
PORT=8500
HOST=localhost
REACT_APP_API_URL=https://localhost:6011
REACT_APP_API_PORTAL_SUBSCRIPTION=NotRequiredForLocalUse
REACT_APP_INSTRUMENTATION_KEY=NotApplication
PUBLIC_URL=https://localhost:8500
EXTEND_ESLINT = true
REACT_APP_Environment=development
```

:::caution

The content of .env files in any environment should be considered public knowledge, and there should not be any risk in exposing them to public.

:::

For .env.(environment), we should have the same set of keys in each file, with different values specific to that environment.

###### Reading from .env File {/*reading-from-env-file*/}

We will use [dotenv](https://www.npmjs.com/package/dotenv) in our project

1. Create **.env** file at the root of project

   ```
   API_URL=http://localhost:8000
   ```
   
2. Install dotenv

   ```bash
   yarn add dotenv
   ```
   
3. Config webpack to add env variables

   ```javascript
   const webpack = require('webpack');
   const dotenv = require('dotenv');
   
   module.exports = () => {
     // call dotenv and it will return an Object with a parsed key 
     const env = dotenv.config().parsed;
   
     // reduce it to a nice object, the same as before
     const envKeys = Object.keys(env).reduce((prev, next) => {
       prev[`process.env.${next}`] = JSON.stringify(env[next]);
       return prev;
     }, {});
   
     return {
       plugins: [
       new webpack.DefinePlugin(envKeys)
     ]
   };
   ```

Lastly, to access these config values, we simply use **process.env.(key-name)**, such as `process.env.API_URL`

:::tip

In the world of TypeScript, reading the env variables requires us to enforce type-safety. So we might need to, in case env is a string, do

```typescript
process.env.API_URL as string
```

In the case of [number]: https://github.com/nodejs/help/issues/2217#issuecomment-742274290

```typescript
Number(String(process.env.JWTEXPIRES))
```

:::

##### Static Configurations {/*static-configurations*/}

Static configurations are the ones that don't change from one environment to the other. Examples would be telephone numbers, company names, messages and copies, etc. We simply store these values in a separate file, as they might be subject to change from time to time, and this makes it easier to find and change them.

###### Storing Static Configuration Values {/*storing-static-configuration-values*/}

One way to manage these configs, is to store them in simple json file, such as below:

```json
{
  "locations": {
    "fetchCountriesUrl": "v1/countries"
  },
  "seo": {
    "domain": "https://test.com",
    "siteName": "Test",
    "defaultTitle": "Test | Fast Engineering Eco-Systems with No Compromise",
    "defaultDescription": "...",
    "contact": {
      "email": "info@test.com",
      "phone": "+61 2 816238786"
    },
    "address": {
      "streetAddress": "U7 678 Orouke Rd",
      "addressLocality": "RedFern",
      "addressRegion": "NSW",
      "addressCountry": "Australia",
      "postalCode": "2000"
    }
  }
}
```

JSON structure also enables us to store the values in a specific hierarchy which makes it easier to manage.

###### Reading Static Config Values {/*reading-static-config-values*/}

All we need to do to access such config values, is to import it in our `.ts/.tsx` files and access the values like any other json object:

```typescript
import config from '../../config.json';
```

and then I can write:

```typescript
config.locations.fetchCountriesUrl
```

##### Constants {/*constants*/}

The other alternative to manage static values in code, is through TS objects. We typically manage two types of values using TS objects:

- To store/read those values that are highly unlikely to change from time to time, but we want to keep them separate from our code anyway
- To store/read those values that won't be stored in JSON files as they are (and not as strings), such as Regular Expressions (RegEx)

An example would look like below, and you can read them exactly like Option 2, as above:

```typescript
export const Auth = {
    PasswordRegEx: /^(?=.*[A-Z])(?=.*[\W])(?=.*[0-9])(?=.*[a-z]).{8,128}$/,
    PasswordFailMessage: "Passwords must have at least 8 characters, 1 lowercase, 1 upper case, 1 number, and 1 special character."
}
```

### Creating a new Package {/*creating-a-new-package*/}

In general, each sub-package should have 3 basic components to start with:

1. **src** that contains the package source files
2. **package.json** which hosts the package specific info and dependencies (and dev dependencies)
3. **index.ts**

   <DeepDive>
   
   #### What's index.ts for?

   Inside _my-package/index.ts_ we would simply do something like this:

   ```typescript
   import MyComponent from './src/MyComponent.tsx';

   export default MyComponent;
   ```

   and that's it. This is helpful because inside other components or containers we can do this:

   ```typescript
   import MyComponent from '../my-package';
   ```

   because it tries to access the _index.ts_ file by default thus not requiring any more info from us. It would import automatically the _index.ts_ file which imports the actual component itself. If we did not have an _index.ts_ file we would have had to do this:

   ```typescript
   import MyComponent from '../my-package/src/MyComponent';
   ```
   
   which is kind of awkward. I

   </DeepDive>

At the end of the day, a package fits into a monorepo with the following file structure:

```
.
└── monorepo/
    ├── packages/
    │   └── my-package/
    │       ├── src
    │       ├── index.ts
    │       └── package.json
    ├── tsconfig.json
    ├── package.json
    └── ...
```

### Troubleshooting {/*troubleshooting*/}

#### Some warnings pops up from some test files while running `yarn test`: {/*some-warnings-pops-up-from-some-test-files-while-running-yarn-test*/}

```
  ● Console

    console.error
      Warning: An update to ToolbarPlugin inside a test was not wrapped in act(...).

      When testing, code that causes React state updates should be wrapped into act(...):

      act(() => {
        /* fire events that update state */
      });
      /* assert on the output */

      This ensures that you're testing the behavior the user would see in the browser. Learn more at https://reactjs.org/link/wrap-tests-with-act
```

We need to do 2 things:

1. To prepare a component for assertions, we need to wrap the code rendering it and performing updates inside an `act()` call. This makes our test run closer to how React works in the browser.
2. Someone out there points out using `waitFor` construct, although I have no idea why that works[^mysterious]

For example:

```javascript
import React from "react";
import { render, screen, waitFor } from "@testing-library/react";
import { act } from 'react-dom/test-utils';
import MyComponent from "./MyComponent";

test("renders component properly", async () => {
  act(() => render(<MyComponent />));

  await waitFor(() => {
    const linkElement = screen.getByText(/My Great App/i);
    expect(linkElement).toBeInTheDocument();
  });
});
```

[Babel]: https://qubitpi.github.io/babel-website/

[create-react-app]: https://github.com/facebook/create-react-app

[Hot Module Replacement]: https://webpack.js.org/guides/hot-module-replacement/
[html-webpack-plugin]: https://github.com/jantimon/html-webpack-plugin

[Jest]: https://qubitpi.github.io/jest/
[JSX]: https://www.w3schools.com/react/react_jsx.asp

[Server-side rendering vs Client-side rendering]: https://stackoverflow.com/a/36623117

[ts-jest config]: https://kulshekhar.github.io/ts-jest/docs/getting-started/installation/#jest-config-file

[webpack]: https://webpack.js.org/
[webpack dev server]: https://github.com/webpack/webpack-dev-server

[^1]: https://stackoverflow.com/a/44987447/14312712
[^2]: https://stackoverflow.com/a/63152687/14312712
[^enabling-routed-page-refresh-with-webpack]: https://stackoverflow.com/a/72383988
[^mysterious]: https://stackoverflow.com/a/65811603
[^transformIgnorePatterns]: https://stackoverflow.com/a/49676319
