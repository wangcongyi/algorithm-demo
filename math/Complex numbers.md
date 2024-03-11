#### Complex numbers
#### i² = -1

```javascript

class Complex {
  constructor(real, imaginary) {
    this.real = real;
    this.imaginary = imaginary;
  }

  // Add another complex number to this one
  add(other) {
    return new Complex(
      this.real + other.real,
      this.imaginary + other.imaginary
    );
  }

  // Multiply this complex number by another complex number
  multiply(other) {
    // (a + bi) * (c + di) = (ac - bd) + (ad + bc)i
    const realPart =
      this.real * other.real - this.imaginary * other.imaginary;
    const imaginaryPart =
      this.real * other.imaginary + this.imaginary * other.real;
    return new Complex(realPart, imaginaryPart);
  }

  // Display complex number in a readable format
  toString() {
    return `${this.real} + ${this.imaginary}i`;
  }
}

// Demonstrating i^2 = -1
const i = new Complex(0, 1); // Representing the imaginary unit i
const iSquared = i.multiply(i); // Calculating i^2

```
