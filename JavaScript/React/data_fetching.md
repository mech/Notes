# Data Fetching

* [Making your app faster with high-performance components](https://www.youtube.com/watch?v=KYzlpRvWZ6c&t=1351)
* [Model Management](https://github.com/facebook/react/wiki/Complementary-Tools#model-management)
* [React Ajax best practices](http://andrewhfarmer.com/react-ajax-best-practices/)
* [react-refetch from Heroku](https://github.com/heroku/react-refetch)

## Data Management Pattern

There are plenty of ways to manage your data:

* Container component (a.k.a Smart component)
* Flux - Store
* Cursor - Clojure Om?
* Relay
* Cortex - Centrally managing data with React

## Container Component

Create a new stateful component whose single responsibility is communicating with the remote API, and passing data and callbacks down as props. Some people call this type of component a container component.

Your `App` is still pure component, and your `AppContainer` will be the one that is stateful!

```js
class ContactsAppContainer extends Component {
  constructor() {
    super()
    this.state = {
      contacts: []
    }
  }
  
  componentDidMount() {
    fetch('/contacts')
    .then(res => res.json)
    .then(data => {
      this.setState({contacts: data})
    }).catch(err => console.warn(err))
  }
  
  render() {
    return <ContactsApp contacts={this.state.contacts} />
  }
}

class ContactsApp extends Component {
  // I am sort of pure app component
}
```