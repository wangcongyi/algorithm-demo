#### 广度优先搜索

```

广度优先搜索算法（BFS）
BFS 是从根节点开始，沿着树的宽度遍历树的节点
如果所有节点均被访问 则算法中止

```

![bfs](https://github.com/wangcongyi/learning-algorithm/blob/master/images/bfs.gif)


```js

const initCallbacks = (callbacks = {}) => {
  const initiatedCallback = callbacks
  const stubCallback = () => {
  }
  const defaultAllowTraversal = () => true

  initiatedCallback.allowTraversal = callbacks.allowTraversal || defaultAllowTraversal
  initiatedCallback.enterNode = callbacks.enterNode || stubCallback
  initiatedCallback.leaveNode = callbacks.leaveNode || stubCallback

  return initiatedCallback
}


const breadthFirstSearch = (rootNode, originalCallbacks) => {
  const callbacks = initCallbacks(originalCallbacks)
  const nodeQueue = new Queue()
  nodeQueue.enqueue(rootNode)

  while (!nodeQueue.isEmpty()) {
    const currentNode = nodeQueue.dequeue()
    callbacks.enterNode(currentNode)
    if (currentNode.left && callbacks.allowTraversal(currentNode, currentNode.left)) {
      nodeQueue.enqueue(currentNode.left)
    }

    if (currentNode.right && callbacks.allowTraversal(currentNode, currentNode.right)) {
      nodeQueue.enqueue(currentNode.right)
    }

    callbacks.leaveNode(currentNode)
  }
}

```
