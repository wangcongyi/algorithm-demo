### Big O

- O(n) 总执行次数随 n 增长
```js
function sun(n) {
  let total = 0
  for (let i = 1; i<=n; i++){
    total += i
  }
  return total
}
```
遍历一次数组
for / forEach / for...of 只跑一层，查找、统计、求和、打印  基本属于 O(n)
***

- O(1) 总执行次数随 n 不变
```js
function getFirst(arr) {
  return arr[0]
}
```
直接访问：arr[0] → O(1) Set / Map 的 get / has 没循环 基本属于 O(1)
***

- O(n²) 总执行次数随 n 递增
```js
function printPairs(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++) {
      console.log(arr[i], arr[j]);
    }
  }
}
```
嵌套循环， 对 n 个元素执行 n 个事情   基本属于 O(n²)
***

- O(n log n) 对 n 个元素整体处理一遍（O(n))，但在处理过程中，每个元素只需要分层/折半处理（log n）

经典示例 [归并排序](https://github.com/wangcongyi/algorithm-demo/blob/17cad92165d06f90e5a08bbcb9fe0b4c53920638/sort/mergeSort.md)
拆分阶段（log n）
```
n
↓
n/2 + n/2
↓
n/4 + n/4 + n/4 + n/4
```
合并阶段（O(n)）
```
每一层合并时 所有元素都会被处理一次 每一层是 O(n)
```
层数 log n × 每层 n
= O(n log n)


