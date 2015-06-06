# Trees

## Preorder

```
PreorderTraverse(node)
  Visit node
  For Each child
    PreorderTraverse(child)
```

Visit the node means do whatever you want to do with the node. Print it on screen, modify the value, etc.

Breadth-first use queue to remember the current adjacent level across the node.

## Sorted Trees

Can grow tall and skinny and become a linked list with poor performance.