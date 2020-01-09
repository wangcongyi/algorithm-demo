####

```

Kruskal的算法是最小生成树算法，该算法查找连接森林中任意两棵树的权重最小的边缘
它是图论中的一种贪婪算法，因为它为连接的加权图找到最小生成树，并在每个步骤中增加了成本弧
这意味着它将找到形成一棵包括每个顶点的树的边缘子集，其中树中所有边缘的总权重被最小化
如果该图未连接，则它将找到最小生成树（每个连接的组件的最小生成树）

```

```js

import Graph from 'data-structures/graph/Graph'
import QuickSort from 'sorting/quick-sort/QuickSort'
import DisjointSet from 'data-structures/disjoint-set/DisjointSet'

const kruskal = (graph) => {
  if (graph.isDirected) {
    throw new Error('Kruskal\'s algorithms works only for undirected graphs')
  }
  const minimumSpanningTree = new Graph()
  const sortingCallbacks = {
    compareCallback: (graphEdgeA, graphEdgeB) => {
      if (graphEdgeA.weight === graphEdgeB.weight) {
        return 1
      }

      return graphEdgeA.weight <= graphEdgeB.weight ? -1 : 1
    },
  }
  const sortedEdges = new QuickSort(sortingCallbacks).sort(graph.getAllEdges())
  const keyCallback = graphVertex => graphVertex.getKey()
  const disjointSet = new DisjointSet(keyCallback)

  graph.getAllVertices().forEach((graphVertex) => {
    disjointSet.makeSet(graphVertex)
  })
  for (let edgeIndex = 0; edgeIndex < sortedEdges.length; edgeIndex += 1) {
    const currentEdge = sortedEdges[edgeIndex]
    if (!disjointSet.inSameSet(currentEdge.startVertex, currentEdge.endVertex)) {
      disjointSet.union(currentEdge.startVertex, currentEdge.endVertex)
      minimumSpanningTree.addEdge(currentEdge)
    }
  }
  return minimumSpanningTree
}

```
