# Build

People suck at repetitive tasks.

* Linting
* Transpiling
* Minifying
* Combining (concat)
* [Goodbye Compass](http://bensmithett.com/goodbye-compass/)
* [Goodbye, Sprockets! A Grunt-based Rails Asset Pipeline](http://blog.pedago.com/2014/01/21/goodbye-sprockets-a-grunt-based-rails-asset-pipeline/)
* [Taking the asset pipeline out of Rails](http://pivotallabs.com/taking-asset-pipeline-rails/)
* [Getting your PageSpeed score up](https://www.youtube.com/watch?v=pNKnhBIVj4w)
* [Takana - Like BrowserSync?](http://usetakana.com/)
* [Creating a web app with Grunt](http://tech.tmw.co.uk/2014/10/creating-a-web-app-with-grunt-part-1/)

## Make?

* [Tim Lucas's approach](https://gist.github.com/toolmantim/6200029)
* [The ultimate fronted build tool: `make`](https://algorithms.rdio.com/post/make/)
* [I love the Unix philosophy, but...](http://mntr.dk/2014/i-love-the-unix-philisophy-but/)

## package.json

* [Cheatsheet](http://package.json.jit.su/)

## Component vs Bower

Bower is meant to work with build tools rather than replace them.
Bower is not built with opinions on scripting loader or modular loading. It is not concerned with how the assets it manages get included in your web pages.

* [Some arguments with @visionmedia](https://github.com/bower/bower/pull/62)

## Glob

* `!name` - Matches any single character not in `name`
* `{s1, s2, s3}` - Matches any of the strings given (separated by commas)

## Browser Sync

* [Cross browser CSS injection](http://css-tricks.com/cross-browser-css-injection/)

## Gulp

Gulp has built-in watcher.
Grunt uses JSON-like data configuration files; Gulp uses leaner, simpler JavaScript code.

```
gulp.src(glob)   /* Returns a readable stream */
gulp.dist(glob)  /* Returns a writable stream */

// 1 read and 2 writes
gulp.task('build-stuff', function() {
  return gulp.src('js/**/*.js')
    .pipe(concat('all.js'))
    .pipe(gulp.dest('build'))
    .pipe(uglify())
    .pipe(rename('all.min.js'))
    .pipe(gulp.dest('build'))
});
```

* [A blank project with Gulp.js as build system](https://github.com/kyleconrad/blank-gulp)
* [Presentation on Gulp](http://slid.es/contra/gulp)
* [Gulp - The streaming build system](http://www.bram.us/2014/01/20/gulp-the-streaming-build-system/)
* https://www.youtube.com/watch?v=Blqaio9HaHA
* [Error management in gulp](https://gist.github.com/floatdrop/8269868)

### Plugins

* [gulp-browser-sync](https://github.com/shakyShane/gulp-browser-sync)
* [gulp-jshint](https://github.com/wearefractal/gulp-jshint)
* [gulp-autoprefixer](https://github.com/Metrime/gulp-autoprefixer)
* [gulp-changed](https://github.com/sindresorhus/gulp-changed)
* [gulp-imagemin](https://github.com/sindresorhus/gulp-imagemin)
* [gulp-strip-debug](https://github.com/sindresorhus/gulp-strip-debug)
* [gulp-uglify](https://github.com/terinjokes/gulp-uglify)
* [gulp-concat](https://github.com/wearefractal/gulp-concat)
* [gulp-svgmin](https://github.com/ben-eb/gulp-svgmin)
* [gulp-cssmin](https://github.com/chilijung/gulp-cssmin)
* [gulp-htmlmin](https://github.com/jonschlinkert/gulp-htmlmin)
* [jshint-stylish](https://github.com/sindresorhus/jshint-stylish)
* [grunt-montage](https://github.com/globaldev/grunt-montage)
* [gulp-if](https://github.com/robrich/gulp-if)
* [gulp-load-plugins](https://github.com/jackfranklin/gulp-load-plugins)
* [gulp-colorguard](https://github.com/pgilad/gulp-colorguard)
* [Critical path](https://github.com/addyosmani/critical)


## Grunt

No context between transformations. More tasks, more slow-down. TMP file hell!

* [Grunt plugins reviewed](http://cognition.happycog.com/article/grunt-plugins-reviewed)
* [grunt-pagespeed](https://github.com/jrcryer/grunt-pagespeed)

### Plugins

* [grunt-uncss](https://github.com/addyosmani/grunt-uncss)
* [grunt-spritesmith](https://github.com/Ensighten/grunt-spritesmith)

## Broccoli

* [Broccoli - A fast, reliable asset pipeline](https://github.com/joliss/broccoli)
* [Architecture of Broccoli](http://www.solitr.com/blog/2014/02/broccoli-first-release/)

## JSHint

* [Plato.js](https://github.com/es-analysis/plato)
* [JavaScript Code Style Checker](https://github.com/mdevils/node-jscs)

```
"maxparams": 4
"maxdepth": 4
"maxstatements": 20
"maxlen": 100
"maxcomplexity": 7
```