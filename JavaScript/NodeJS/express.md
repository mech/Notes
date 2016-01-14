# Express.js

Node has a built in `http` module that allows us to create a server. The problem is that configuration is pretty overwhelming and difficult (memory leaks, etc.). Most people use express.js even there is still a bit of configuration going on, but it has a welcoming API.

* [Production best practices](http://expressjs.com/en/advanced/best-practice-performance.html)

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
npm i -g nodemon
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

## Middleware

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

## Security

* [Express.js Security Tips](http://webapplog.com/express-js-security-tips/)

## Sample

* [react-webpack-node](https://github.com/choonkending/react-webpack-node)
* [tjholowaychuk's single app.js](https://github.com/visionmedia/screenshot-app/blob/master/app.js)

## Deprecation

`app.configure()` is deprecated in version 4.