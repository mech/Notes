# Express.js

Node has a built in `http` module that allows us to create a server. The problem is that configuration is pretty overwhelming and difficult (memory leaks, etc.). Most people use express.js even there is still a bit of configuration going on, but it has a welcoming API.

* [express.js Repo](https://github.com/strongloop/express)
* [Production best practices](http://expressjs.com/en/advanced/best-practice-performance.html)
* [jshttp - Low-level JavaScript HTTP-related Modules](https://github.com/jshttp)
* [Performance at rest](http://hueniverse.com/2014/08/20/performance-at-rest/)

Node.js is a single-threaded event loop. It enqueues and dequeues events. That's all.

```js
var express = require('express');
var bodyParser = require('body-parser');

var app = express();

app.set('port', process.env.PORT || 3000);

// Using middleware
app.use(bodyParser.json());

// Using route
app.get('/', function(req, res) {
});

// Boot up the app
var server = http.createServer(app);
server.listen(app.get('port'), function() {
  console.info('Express listening on port ' + app.get('port'));
});
```

## nodemon

```
▶ npm i -g nodemon
```

## Structuring

* [Code structure](https://github.com/focusaurus/express_code_structure)
* [Or simply use Kraken.js](http://krakenjs.com/)
* [base-express](https://github.com/terlici/base-express)

```js
require('./config/routes')(app, express);

// In config/routes
module.exports = function(app, express) {
  app.use(express.static(path.join(__dirname, 'public')));
};
```

## Routes

With Express 4, we can now have more than one router. Think of router as module with its own routing and middleware stack and functionality. The global `app` will still control global middleware and configuration and setup routing for the other routers we make.

Finally, we can have more than one router.

```js
var app = express();
var candidateRouter = express.Router();

candidateRouter.get('/profile', function(req, res) {
  // This will be /ca/profile
});

app.use('/ca', candidateRouter);
```

```js
// At app.js or server/index.js
require('./routes')(app);

// At routes/index.js
var fs = require('fs');
var path = require('path');

module.exports = function(app) {
  fs.readdirSync('./routes').forEach(function(file) {
    // Avoid current file
    if (file === path.basename(__filename)) { return; }

    require('./' + file)(app);
  });
};

// For any new routes, just add like routes/auth.js
module.exports = function(app) {
  app.get('/login', function(req, res) {
    res.render('login');
  });
};
```

## Request and Response

```js
res.json()
res.send() // also convert to JSON

res.status(500).send(error)

req.body // using Fetch API with JSON.stringify body and express will convert the JSON to JavaScript object
req.params
```

[request is not used for CORS](https://github.com/request/request/issues/986)

## Blocking

* [node-blocked](https://github.com/tj/node-blocked)
* [The case of the blocked event loop](http://zef.me/4561/node-js-and-the-case-of-the-blocked-event-loop/)

Node.js is more I/O bound than CPU bound. Intensive computation like Fibonacci or Prime Number really has no place in a Node.js program.

If you `JSON.parse()` a 15MB of JSON file it will take about 2 seconds and also block all other requests.

## Middleware

* [Makara - Internationalization](https://github.com/krakenjs/makara)
* [Lusca - Security](https://github.com/krakenjs/lusca)

Express uses middleware to modify and inspect incoming request.

Middleware can run any code, change the request and response objects, end the request-response cycle, and call the next middleware in the stack.

Middleware is an amazingly useful pattern that allows developers to reuse code and share it with others via NPM modules.

```js
// Mounting by prefixing the middleware
app.use('/admin', function(req, res, next) {
  
  next();
});
```

There are 3rd party, router-level, application-level, error-handling and built-in middleware.

```js
// Error-handling middleware
app.use(function (err, req, res, next) {});
```

Nice for handling authentication also. Here, we are using middleware on a route.

```js
var checkAuth = require('./util/checkauth');

app.get('/users', [checkAuth()], function(req, res) {
  // Auth is good here
});
```

It is sort of like Rails's `before_action`.

```js
app.all('/ca/*', [isAuthenticated, isCandidate], function(req, res, next) {
});

app.all('*', function(req, res, next) {
  if (req.isAuthenticated()) {
    next();
  } else {
    next(new Error(401)); // 401 Unauthorized
    // Or
    res.status(401).send({message: 'access denied'});
  }
});
```

Name your function:

```js
app.use(function forceLiveDomain(req, res, next) {
  // ...
  return next();
});
```

Performance of middleware should be quick. Do not make too many HTTP request in middleware as it run series from top of the stack to the bottom. Use Async.js for making HTTP requests.

```js
function parallel(middlewares) {
  return function(req, res, next) {
    async.each(middlewares, function(mw, cb) {
      mw(req, res, cb);
    }, next);
  };
}

app.use(parallel([
  getUser,
  getSiteList,
  getCurrentSite,
  getSubscription
]));
```

## Controllers

```js
var controller = require('./controller');

module.exports.initialize = function(app, router) {
  router.get('/', controller.index);

  router.get('/login', controller.login);
  router.post('/login', controller.processLogin);

  router.post('/movies', controller.addMovie);

  app.use('/', router);
};

// In controller.js
var request = require('request');

module.exports = {
  index: function(req, res) {
  },

  addMovie: function(req, res) {
  }
};
```

## Security

* [Express.js Security Tips](http://webapplog.com/express-js-security-tips/)

## Sample

* [react-webpack-node](https://github.com/choonkending/react-webpack-node)
* [tjholowaychuk's single app.js](https://github.com/visionmedia/screenshot-app/blob/master/app.js)

## Deprecation

`app.configure()` is deprecated in version 4.