#### Newton's universal law of gravitation
#### ![image](https://github.com/wangcongyi/algorithm-demo/assets/13843979/b18b4522-b1c8-4552-badf-cba0a7913e18)

```javascript

const calculateGravitationalForce = (m1, m2, r) => {
  const G = 6.674e-11 // Gravitational constant in N(m^2)/(kg^2)
  return (G * (m1 * m2)) / (r * r)
}

```
