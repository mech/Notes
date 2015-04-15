# Webpack

We want to write modular code. But browsers cannot run modularised code, so we need a module bundler. UIs aren't just JavaScript though. Our UI components can also depend on images, fonts, and CSS. Webpack recognises that and with the help of loaders, supercharges the `require` function so you can explicitly require all of your dependencies.

Webpack uses "loaders" to preprocess files while browserify uses "transforms".

```
▶ npm install --save react
▶ npm install --save normalize.css
▶ npm install --save-dev babel-loader # Will add webpack also
▶ npm install --save-dev babel-eslint
▶ npm install --save-dev eslint-loader
▶ npm install --save-dev url-loader
▶ npm install --save-dev css-loader
▶ npm install --save-dev style-loader
▶ npm install --save-dev sass-loader
▶ npm install --save-dev postcss-loader
▶ npm install --save-dev autoprefixer-core
▶ npm install --save-dev react-hot-loader
▶ npm install --save-dev extract-text-webpack-plugin
```

* [**Creating a workflow with WebPack**](http://christianalfoni.github.io/javascript/2014/12/13/did-you-know-webpack-and-react-is-awesome.html)
* [**React-seed**](https://github.com/badsyntax/react-seed)
* [**React with Webpack**](http://jslog.com/2014/10/02/react-with-webpack-part-1/)
* [**Webpack Cookbook**](http://christianalfoni.github.io/react-webpack-cookbook/)
* [Pete Hunt Webpack Howto](https://github.com/petehunt/webpack-howto)
* [Webpack presentation](https://unindented.github.io/webpack-presentation)
* [react-hot-boilerplate](https://github.com/gaearon/react-hot-boilerplate)
* [react-starterkit](https://github.com/wbkd/react-starterkit)
* [Official Webpack's react-starter](https://github.com/webpack/react-starter)
* [webpack_assets](https://github.com/knomedia/webpack_assets)
* [Browserify vs Webpack JS Drama](http://blog.namangoel.com/browserify-vs-webpack-js-drama)
* [Browserify for webpack users](https://gist.github.com/substack/68f8d502be42d5cd4942)
* [Browserify vs Webpack](http://mattdesl.svbtle.com/browserify-vs-webpack)
* [Good issue discussion](https://github.com/webpack/webpack/issues/378)
* [Browserify Handbook](https://github.com/substack/browserify-handbook)
* [Single page modules with Webpack](http://dontkry.com/posts/code/single-page-modules-with-webpack.html)
* [HMR](http://stackoverflow.com/questions/24581873/what-exactly-is-hot-module-replacement-in-webpack)
* [Rails with Webpack](https://www.reinteractive.net/posts/213-rails-with-webpack-why-and-how)

## Loaders

The loaders will only kick into action when you try to `require` something that match the `test` patterns.

## webpack.config.js

* [Example](https://github.com/glebm/gulp-webpack-react-bootstrap-sass-template/blob/master/webpack.config.litcoffee)
* [Example](https://github.com/MoOx/eslint-loader/issues/23)
* [React ES6 boilerplate](https://github.com/arnarthor/react-es6-boilerplate)
* [From christianalfoni](https://github.com/christianalfoni/webpack-example)
* [Using gulp to inject hashes to HTML?](https://github.com/glebm/gulp-webpack-react-bootstrap-sass-template/blob/master/webpack.config.litcoffee)
* [React starter kit](https://github.com/kriasoft/react-starter-kit/)

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

## webpack-dev-server

A Node.js express server using `webpack-dev-middleware` to serve webpack bundle.

## Hot Module Replacement (HMR)

* [What exactly is HMR?](http://stackoverflow.com/questions/24581873/what-exactly-is-hot-module-replacement-in-webpack)
* [React hot loader](https://gaearon.github.io/react-hot-loader/2014/07/23/integrating-jsx-live-reload-into-your-react-workflow/)
* [Don't trigger module reloading when there were errors generating the bundle](https://github.com/webpack/webpack-dev-server/issues/42)
* [**You need to do module.hot at main entry file**](https://github.com/christianalfoni/react-webpack-cookbook/wiki/Hot-loading-components)


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

## Videos

* [Webpack module bundler](https://www.youtube.com/watch?v=qs9TjH7VheA)
* 
