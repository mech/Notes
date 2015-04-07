# Webpack

We want to write modular code. But browsers cannot run modularised code, so we need a module bundler. UIs aren't just JavaScript though. Our UI components can also depend on images, fonts, and CSS. Webpack recognises that and with the help of loaders, supercharges the `require` function so you can explicitly require all of your dependencies.

Webpack uses "loaders" to preprocess files while browserify uses "transforms".

```
▶ npm install --save react
▶ npm install --save-dev babel-loader # Will add webpack also
```

* [**React-seed**](https://github.com/badsyntax/react-seed)
* [**React with Webpack**](http://jslog.com/2014/10/02/react-with-webpack-part-1/)
* [Pete Hunt Webpack Howto](https://github.com/petehunt/webpack-howto)
* [Webpack presentation](https://unindented.github.io/webpack-presentation)
* [react-starterkit](https://github.com/wbkd/react-starterkit)
* [react-starter](https://github.com/webpack/react-starter)
* [webpack_assets](https://github.com/knomedia/webpack_assets)
* [Browserify vs Webpack JS Drama](http://blog.namangoel.com/browserify-vs-webpack-js-drama)
* [Browserify for webpack users](https://gist.github.com/substack/68f8d502be42d5cd4942)
* [Browserify vs Webpack](http://mattdesl.svbtle.com/browserify-vs-webpack)
* [Creating a workflow with WebPack](http://christianalfoni.github.io/javascript/2014/12/13/did-you-know-webpack-and-react-is-awesome.html)
* [Good issue discussion](https://github.com/webpack/webpack/issues/378)
* [Browserify Handbook](https://github.com/substack/browserify-handbook)
* [Single page modules with Webpack](http://dontkry.com/posts/code/single-page-modules-with-webpack.html)
* [HMR](http://stackoverflow.com/questions/24581873/what-exactly-is-hot-module-replacement-in-webpack)
* [Rails with Webpack](https://www.reinteractive.net/posts/213-rails-with-webpack-why-and-how)

## webpack.config.js

* [Example](https://github.com/glebm/gulp-webpack-react-bootstrap-sass-template/blob/master/webpack.config.litcoffee)
* [Example](https://github.com/MoOx/eslint-loader/issues/23)
* [React ES6 boilerplate](https://github.com/arnarthor/react-es6-boilerplate)

Single entry or multiple entries for code splitting.

Webpack is mainly a JavaScript-bundler. Its "native" language is JavaScript and every other source requires a loader which transforms it to JavaScript.

## CSS in Webpack

* [**Smart CSS build with Webpack**](http://bensmithett.com/smarter-css-builds-with-webpack/)
* [Combine SCSS with Webpack](http://stackoverflow.com/questions/26851120/how-can-i-setup-webpack-to-minify-and-combine-scss-and-javascript-like-codekit)

In Webpack, each Sass file is complied in isolation. It means you need to `@import` dependencies like variables and mixins wherever you use them!?

```
// header.scss
@import 'config/colors'

.header { color: $red; }
```

```
// Loaders will be applied from right to left, piping?
style!css!sass?includePaths[]=
```

* style-loader - returns JavaScript string as `StyleSheet`
* css-loader - returns JavaScript string, resolve `@import` and `url`
* sass-loader
* file-loader - for css-loader to include images assets