#### The Fourier transform
#### ![image](https://github.com/wangcongyi/algorithm-demo/assets/13843979/540b0bcb-8e51-48f9-88b1-ee2b575f725c)

```javascript

const discreteFourierTransform = (signal) => {
    const N = signal.length
    let X = new Array(N)

    for (let k = 0; k < N; k++) {
      let sumReal = 0
      let sumImag = 0

      for (let n = 0; n < N; n++) {
        const phi = (2 * Math.PI * k * n) / N
        sumReal += signal[n] * Math.cos(phi)
        sumImag -= signal[n] * Math.sin(phi)
      }

      X[k] = { real: sumReal, imag: sumImag }
    }
    return X
  }

  // Example usage:
  const signal = [0, 1, 2, 3, 4, 5, 6, 7] // An example signal
  const DFT = discreteFourierTransform(signal)
  console.log(DFT)

```
