# Express.js

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


## Security

* [Express.js Security Tips](http://webapplog.com/express-js-security-tips/)

## Sample

* [react-webpack-node](https://github.com/choonkending/react-webpack-node)
* [tjholowaychuk's single app.js](https://github.com/visionmedia/screenshot-app/blob/master/app.js)

## Deprecation

`app.configure()` is deprecated in version 4.