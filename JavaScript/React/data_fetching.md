# Data Fetching

* [Making your app faster with high-performance components](https://www.youtube.com/watch?v=KYzlpRvWZ6c&t=1351)
* [Model Management](https://github.com/facebook/react/wiki/Complementary-Tools#model-management)
* [React Ajax best practices](http://andrewhfarmer.com/react-ajax-best-practices/)
* [react-refetch from Heroku](https://github.com/heroku/react-refetch)
* [dataloader](https://github.com/facebook/dataloader)
* [DataLoader - Source code walkthrough](https://youtu.be/OQTnXNCDywA)

## Data Flow

No component lives in isolation. As parent components push props into their children, and as those children render their own child components, you must carefully consider how your data flows through the application. How much does each child really need to know about? Who owns the application state? Which components, if any, need local state? This is the subject of data flow.

In React, data flows in one direction only - from the parent to the child.

## Data Management Pattern

There are plenty of ways to manage your data:

* Container component (a.k.a Smart component)
* Flux - Store
* Cursor - Clojure Om?
* Relay
* Cortex - Centrally managing data with React

## Container Component

* [Let's compose some React Container](https://voice.kadira.io/let-s-compose-some-react-containers-3b91b6d9b7c8#.jd42cjjbj)

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