# Webpack

We want to write modular code. But browsers cannot run modularised code, so we need a module bundler. UIs aren't just JavaScript though. Our UI components can also depend on images, fonts, and CSS. Webpack recognises that and with the help of loaders, supercharges the `require` function so you can explicitly require all of your dependencies.

Webpack uses "loaders" to preprocess files while browserify uses "transforms".

```
npm init -y

npm i webpack --save-dev

npm i file-loader --save-dev
npm i url-loader --save-dev

npm i css-loader --save-dev
npm i style-loader --save-dev
npm i postcss-loader --save-dev
npm i postcss-cssnext --save-dev

npm i babel-core --save-dev
npm i babel-loader --save-dev

npm i eslint --save-dev
npm i eslint-loader --save-dev
npm i babel-eslint --save-dev

npm i babel-preset-es2015 babel-preset-react --save-dev

npm i babel-plugin-syntax-class-properties --save-dev
npm i babel-plugin-syntax-decorators --save-dev
npm i babel-plugin-syntax-object-rest-spread --save-dev

npm i babel-plugin-transform-class-properties --save-dev
npm i babel-plugin-transform-decorators-legacy --save-dev
npm i babel-plugin-transform-object-rest-spread --save-dev

npm i babel-plugin-react-transform --save-dev
npm i react-transform-hmr --save-dev

npm i babel-preset-react-hmre --save-dev

npm i react react-dom --save
```

OLD

```
▶ npm install react --save --save-exact
▶ npm install --save normalize.css
▶ npm install --save-dev babel-loader # Will add webpack also
▶ npm install --save-dev babel-eslint
▶ npm install --save-dev eslint-loader
▶ npm install --save-dev eslint-plugin-react
▶ npm install --save-dev url-loader
▶ npm install --save-dev css-loader
▶ npm install --save-dev style-loader
▶ npm install --save-dev sass-loader
▶ npm install --save-dev postcss-loader
▶ npm install --save-dev autoprefixer-core
▶ npm install --save-dev react-hot-loader
▶ npm install --save-dev extract-text-webpack-plugin
▶ npm install --save-dev webpack-dev-server
▶ npm install --save-dev assets-webpack-plugin
▶ npm install --save camelize
```

* [**A modern React starter pack based on webpack**](http://krasimirtsonev.com/blog/article/a-modern-react-starter-pack-based-on-webpack)
* [**A new Webpack boilerplate with hot reloading**](https://github.com/gaearon/react-transform-boilerplate)
* [**Very nice component library setup**](https://medium.com/@yamalight/building-modular-javascript-applications-in-es6-with-react-webpack-and-babel-538189cd485f)
* [**Backend Apps with Webpack**](http://jlongster.com/Backend-Apps-with-Webpack--Part-I)
* [**Survive JS**](http://survivejs.com/)
* [**React Webpack Cookbook**](https://christianalfoni.github.io/react-webpack-cookbook/)
* [How to test React components using Karma and webpack](http://nicolasgallagher.com/how-to-test-react-components-karma-webpack/)
* [**Creating a workflow with WebPack**](http://christianalfoni.github.io/javascript/2014/12/13/did-you-know-webpack-and-react-is-awesome.html)
* [**React-seed**](https://github.com/badsyntax/react-seed)
* [**React with Webpack**](http://jslog.com/2014/10/02/react-with-webpack-part-1/)
* [**Webpack Cookbook**](http://christianalfoni.github.io/react-webpack-cookbook/)
* [Pete Hunt Webpack Howto](https://github.com/petehunt/webpack-howto)
* [Webpack presentation](https://unindented.github.io/webpack-presentation)
* [react-hot-boilerplate](https://github.com/gaearon/react-hot-boilerplate)
* [react-starterkit](https://github.com/wbkd/react-starterkit)
* [react-kickstart](https://github.com/vesparny/react-kickstart)
* [Official Webpack's react-starter](https://github.com/webpack/react-starter)
* [hjs-webpack](https://github.com/HenrikJoreteg/hjs-webpack)
* [webpack_assets](https://github.com/knomedia/webpack_assets)
* [Browserify vs Webpack JS Drama](http://blog.namangoel.com/browserify-vs-webpack-js-drama)
* [Browserify for webpack users](https://gist.github.com/substack/68f8d502be42d5cd4942)
* [Browserify vs Webpack](http://mattdesl.svbtle.com/browserify-vs-webpack)
* [Good issue discussion](https://github.com/webpack/webpack/issues/378)
* [Browserify Handbook](https://github.com/substack/browserify-handbook)
* [Single page modules with Webpack](http://dontkry.com/posts/code/single-page-modules-with-webpack.html)
* [HMR](http://stackoverflow.com/questions/24581873/what-exactly-is-hot-module-replacement-in-webpack)
* [fetch polyfills](http://mts.io/2015/04/08/webpack-shims-polyfills/)
* [Fetch polyfill with webpack](https://gist.github.com/Couto/b29676dd1ab8714a818f)
* [Modularity](http://jlongster.com/Modularity)
* [**react-bare-bones-starter-kit**](https://github.com/rob-balfre/react-bare-bones-starter-kit)
* [**react-boilerplate**](https://github.com/mxstbr/react-boilerplate)
* [Webpack aliases and relative paths](http://xabikos.com/javascript%20module%20bundler/javascript%20dependencies%20management/2015/10/03/webpack-aliases-and-relative-paths.html)

The webpack core can be extended with loaders and plugins.

## Loaders

The loaders will only kick into action when you try to `require` something that match the `test` patterns.

## Plugins

## webpack.config.js

* [Example](https://github.com/glebm/gulp-webpack-react-bootstrap-sass-template/blob/master/webpack.config.litcoffee)
* [Example](https://github.com/MoOx/eslint-loader/issues/23)
* [React ES6 boilerplate](https://github.com/arnarthor/react-es6-boilerplate)
* [From christianalfoni](https://github.com/christianalfoni/webpack-example)
* [Using gulp to inject hashes to HTML?](https://github.com/glebm/gulp-webpack-react-bootstrap-sass-template/blob/master/webpack.config.litcoffee)
* [React starter kit](https://github.com/kriasoft/react-starter-kit/)
* [react-boilerplate](https://github.com/hudakdidit/react-boilerplate)
* [react-way-getting-started](https://github.com/RisingStack/react-way-getting-started)
* [react-component-boilerplate](https://github.com/bebraw/react-component-boilerplate)
* [**starter-kit**](http://unicornstandard.com/packages/boilerplate.html)
* [**A modern React starter pack based on webpack**](http://krasimirtsonev.com/blog/article/a-modern-react-starter-pack-based-on-webpack)
* [React+Webpack+Express+Redux](https://github.com/choonkending/react-webpack-node)

```js
// Here when you compile the code it will be temporarily saved into build/js folder.
// Webpack Dev Server will in turn make that folder's scripts available at the URL /public/assets/js

module.exports = {
  context: path.resolve('js').
  entry: [],
  output: {
    path: path.resolve('build/js/),
    publicPath: '/public/assets/js',
    filename: 'bundle.js'  },
  
  devServer: {
    contentBase: 'public'  }};
```

Single entry or multiple entries for code splitting.

Webpack is mainly a JavaScript-bundler. Its "native" language is JavaScript and every other source requires a loader which transforms it to JavaScript.

## CSS in Webpack

* [**Smart CSS build with Webpack**](http://bensmithett.com/smarter-css-builds-with-webpack/)
* [Combine SCSS with Webpack](http://stackoverflow.com/questions/26851120/how-can-i-setup-webpack-to-minify-and-combine-scss-and-javascript-like-codekit)
* [React: CSS in JS](https://speakerdeck.com/vjeux/react-css-in-js)
* [JSS](https://github.com/jsstyles/jss)
* [See issues#31 for Sass import statement](https://github.com/jtangelder/sass-loader/issues/31)

You divide your modules by folders and include both CSS and JavaScript files in those folders. See `entry`.

In Webpack, each Sass file is complied in isolation. It means you need to `@import` dependencies like variables and mixins wherever you use them!?

```
// header.scss
@import 'config/colors'

.header { color: $red; }
```

```
// Loaders will be applied from right to left, piping?
// Use ! to chain loaders
style!css!sass?includePaths[]=
```

* style-loader - take a string, create a `<style>` and handed to DOM
* css-loader - returns JavaScript string, resolve `@import` and `url`
* sass-loader
* file-loader - for css-loader to include images assets

`style-loader` injects `<style>` tag at runtime so it should not work server-side. You can load CSS as just text and then inject it manually.

If `include` isn't set, Webpack will traverse all files within the base directory. This can hurt performance! It is a good idea to set up `include` always. There's also `exclude` option that may come in handy. Prefer `include`, however.

## webpack-dev-server

Deprecated? Replaced by webpack-hot-middleware? webpack-hot-middleware allows you to add hot reloading into an existing server without webpack-dev-server.

A Node.js express server using `webpack-dev-middleware` to serve webpack bundle.

## Hot Module Replacement (HMR)

* [What exactly is HMR?](http://stackoverflow.com/questions/24581873/what-exactly-is-hot-module-replacement-in-webpack)
* [React hot loader](https://gaearon.github.io/react-hot-loader/2014/07/23/integrating-jsx-live-reload-into-your-react-workflow/)
* [Don't trigger module reloading when there were errors generating the bundle](https://github.com/webpack/webpack-dev-server/issues/42)
* [**You need to do module.hot at main entry file**](https://github.com/christianalfoni/react-webpack-cookbook/wiki/Hot-loading-components)
* [Troubleshooting guide for react-hot-loader issues](https://github.com/gaearon/react-hot-loader/blob/master/docs/Troubleshooting.md)
* [**react-transform-webpack-hmr**](https://github.com/rackt/redux/pull/690/files)

Without hot loading, the browser essentially refreshes with a flash and loses all states.

## Feature Flags



## Production

Run uglify dead-code elimination.

```
webpack -p -d // source-map in production (minified also)
```

## HTML Hash Injection

* [**assets-webpack-plugin - Emits JSON file**](https://github.com/sporto/assets-webpack-plugin)
* [Loading webpack bundles with hashed filenames](https://github.com/webpack/webpack/issues/86)
* [html-webpack-plugin](https://github.com/ampedandwired/html-webpack-plugin)
* [html-loader](https://github.com/webpack/html-loader)
* [template-html-loader](https://github.com/jtangelder/template-html-loader)

Use `assets-webpack-plugin` to access the JSON stats object.

## Splits and Lazy Loading

Webpack allows you to split bundles in various ways. You can even load them dynamically as your application gets executed. This sort of lazy loading comes in handy for large applications. You can load dependencies as you need them.

## Webpack with Rails

* [**react-rails-webpack**](https://netguru.co/blog/react-rails-webpack)
* [**Building stateless Rails API with React**](http://fredguest.com/2015/03/06/building-a-stateless-rails-api-with-react-and-twitter-oauth/)
* [**Flux/Flummox, React/Router, Immutable, Webpack, Babel on Rails**](https://github.com/zepplock/FFRRIWB)
* [How to use webpack with Rails](http://clarkdave.net/2015/01/how-to-use-webpack-with-rails/)
* [Rails with Webpack](https://www.reinteractive.net/posts/213-rails-with-webpack-why-and-how)
* [assets-webpack-plugin](https://github.com/sporto/assets-webpack-plugin)
* [webpack_and_rails](https://github.com/mindreframer/webpack_and_rails)
* [webpack_rails_demo](https://github.com/flarnie/webpack_rails_demo)
* [rails-webpack-react-flux](https://github.com/nambrot/rails-webpack-react-flux)
* [Setting up webpack with Rails](https://medium.com/brigade-engineering/setting-up-webpack-with-rails-c62aea149679)
* [React Webpack Rails](https://github.com/justin808/react-webpack-rails-tutorial)
* [swig-webpack-plugin - Better than assets-webpack-plugin?](https://github.com/jaylinski/swig-webpack-plugin)
* [Basic React.js with Rails without react-rails gem](https://labs.chie.do/creating-a-basic-reactjs-app-with-rails-serving-the-api-without-react-rails/)
* [rails-starter](https://github.com/chiedojohn/rails-starter/tree/react/#sthash.KExty8ov.dpuf)
* [**react-universal-starter**](https://github.com/vasanthk/react-universal-starter)
* [hjs-webpack - Helpers/presets for setting up webpack](https://github.com/HenrikJoreteg/hjs-webpack)

Use JSON manifest file for production fingerprinting.

1. Forget about Rails Asset Pipeline.
2. Have a folder called "front-end", "fe" or "webpack"
3. Use [foreman](https://github.com/ddollar/foreman) to start Rails server + webpack watcher
4. Ask webpack to build assets for us and put it directly in `/public` folder.
5. Generate JSON file with the hashes fingerprinting for Rails view to use. See [assets-webpack-plugin](https://github.com/sporto/assets-webpack-plugin)
6. Do not commit the generated bundle from webpack! gitignore it also.


## Videos

* [Webpack module bundler](https://www.youtube.com/watch?v=qs9TjH7VheA)
* 
