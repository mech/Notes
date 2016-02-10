# Baobab

* [Flux vs Single State Tree](http://www.christianalfoni.com/articles/2015_11_16_Flux-vs-Single-State-Tree)

```js
import Baobab from 'baobab';

// Defining a single state tree for our application
export default new Baobab({
  todos: {
    isSaving: false,
    list: []
  }
});

// Actions and action creators - sort of :)
import tree from './tree';
import ajax from 'ajax';

function addTodo(todo) {
  tree.set(['todos', 'isSaving'], true);
  
  ajax.post('/todos', todo)
    .then(() => {
      tree.set(['todos', 'isSaving'], false);
      tree.push(['todos', 'list'], todo);
    });
}
```

With a single state tree like Baobab, you use imperative programming to do your state changes. The tree is still immutable though, so any changes to the branches of the tree will replace the whole branch, not just the value on the branch. This makes shallow checking possible when `shouldComponentUpdate` in React.

Horrible to test? No time travel debugging? Cursor is outdated? Too messy?