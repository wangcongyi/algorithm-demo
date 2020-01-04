#### 深度优先搜索

```

深度优先搜索算法（DFS）是一种用于遍历或搜索树或图的算法
沿着树的深度遍历树的节点 尽可能深的搜索树的分支 
当节点v的所在边都己被探寻过 搜索将回溯到发现节点v的那条边的起始节点 
这一过程一直进行到已发现从源节点可达的所有节点为止
如果还存在未被发现的节点 则选择其中一个作为源节点并重复以上过程
整个进程反复进行直到所有节点都被访问为止

```

![dfs](https://github.com/wangcongyi/learning-algorithm/blob/master/images/dfs.gif)

```js

const initCallbacks = (callbacks = {}) => {
  const initiatedCallbacks = {}

  const stubCallback = () => {
  }
  const defaultAllowTraversalCallback = () => true
  initiatedCallbacks.allowTraversal = callbacks.allowTraversal || defaultAllowTraversalCallback
  initiatedCallbacks.enterNode = callbacks.enterNode || stubCallback
  initiatedCallbacks.leaveNode = callbacks.leaveNode || stubCallback
  return initiatedCallbacks
}


const depthFirstSearchRecursive = (node, callbacks) => {
  callbacks.enterNode(node)

  if (node.left && callbacks.allowTraversal(node, node.left)) {
    depthFirstSearchRecursive(node.left, callbacks)
  }
  if (node.right && callbacks.allowTraversal(node, node.right)) {
    depthFirstSearchRecursive(node.right, callbacks)
  }
  callbacks.leaveNode(node)
}

const depthFirstSearch = (rootNode, callbacks) => {
  const processedCallbacks = initCallbacks(callbacks)
  depthFirstSearchRecursive(rootNode, processedCallbacks)
}

```
