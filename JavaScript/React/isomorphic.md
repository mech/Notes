# Isomorphic

* [**Isomorphic React app with Rails**](https://medium.com/@olance/isomorphic-reactjs-app-with-ruby-on-rails-part-1-server-side-rendering-8438bbb1ea1c)
* [Setting up a simple isomorphic React app](http://jmfurlott.com/tutorial-setting-up-a-simple-isomorphic-react-app/)
* [What is an isomorphic application](https://www.lullabot.com/articles/what-is-an-isomorphic-application)
* [True isomorphic app with baobab](https://www.codementor.io/reactjs/tutorial/true-isomorphic-apps-react-baobab#/)
* [Rendering React - Server-side](https://www.beaconreader.com/beacon-engineering-blog/rendering-react)
* [Foundation of Universal JavaScript](https://strongloop.com/strongblog/the-foundations-of-universal-or-isomorphic-javascript/)
* [From AirBnB](https://github.com/goatslacker/iso)

```js
// on the server you can render the app to a string
res.write(ReactDOMServer.renderToString(<App />));

// then the client can pick it up
ReactDOM.render(<App />, elementTheServerRenderedInto);
```

* [example-react-router-server-rendering-lazy-routes](https://github.com/rackt/example-react-router-server-rendering-lazy-routes)