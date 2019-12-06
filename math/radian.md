### 弧度


| Radians | Degrees |
| :-----: | :-----: |
| 0       | 0°      |
| π/12    | 15°     |
| π/6     | 30°     |
| π/4     | 45°     |
| 1       | 57.3°   |
| π/3     | 60°     |
| π/2     | 90°     |
| π       | 180°    |
| 2π      | 360°    |

![radian](https://github.com/wangcongyi/learning-algorithm/blob/master/images/r.gif)


```js

const degreeToRadian = degree => {
  return degree * (Math.PI / 180)
}


const radianToDegree = radian => {
  return radian * (180 / Math.PI)
}

```
