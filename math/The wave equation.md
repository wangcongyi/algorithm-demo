#### The wave equation
#### ![image](https://github.com/wangcongyi/algorithm-demo/assets/13843979/038e077b-88f6-425a-b49f-b09f7ff3a8cd)

```javascript

const simulateWaveEquation = (c, length, duration, dx, dt) => {
    // c: wave speed
    // length: length of the medium
    // duration: total time of simulation
    // dx: space step
    // dt: time step

    // Calculate the number of points in space and time
    const nx = Math.floor(length / dx) + 1
    const nt = Math.floor(duration / dt) + 1

    // Stability condition (Courant condition)
    const courantCondition = ((c * dt) / dx) ** 2
    if (courantCondition > 1) {
      throw new Error(
        'Simulation may be unstable. Try adjusting dt or dx.',
      )
    }

    // Initialize wave at t=0 and t=1 (assuming initial condition and first time derivative)
    let u = new Array(nx).fill(0) // Initial displacement
    let uPrev = [...u] // Copy of the initial displacement
    let uNext = new Array(nx).fill(0) // Next time step

    // Example: A simple initial condition (e.g., a peak in the middle)
    u[Math.floor(nx / 2)] = 1

    for (let i = 1; i < nt; i++) {
      for (let j = 1; j < nx - 1; j++) {
        // Implementing the finite difference method for the wave equation
        uNext[j] =
          2 * u[j] -
          uPrev[j] +
          courantCondition * (u[j - 1] - 2 * u[j] + u[j + 1])
      }

      // Update the previous and current solutions
      uPrev = [...u]
      u = [...uNext]
    }

    // Return the final state (for the sake of demonstration)
    return u
  }

  // Example parameters
  const c = 1 // Wave speed
  const length = 10 // Length of the medium
  const duration = 2 // Total time of simulation
  const dx = 0.1 // Space step
  const dt = 0.01 // Time step

  const finalWaveState = simulateWaveEquation(
    c,
    length,
    duration,
    dx,
    dt,
  )
  console.log(finalWaveState)

```
