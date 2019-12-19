#### KMP 算法

```js

const knuthMorrisPratt = (text, word) => {
  if (word.length === 0) {
    return 0
  }

  let textIndex = 0
  let wordIndex = 0

  const _buildPatternTable = word => {
    const patternTable = [0]
    let prefixIndex = 0
    let suffixIndex = 1

    while (suffixIndex < word.length) {
      if (word[prefixIndex] === word[suffixIndex]) {
        patternTable[suffixIndex] = prefixIndex + 1
        suffixIndex += 1
        prefixIndex += 1
      } else if (prefixIndex === 0) {
        patternTable[suffixIndex] = 0
        suffixIndex += 1
      } else {
        prefixIndex = patternTable[prefixIndex - 1]
      }
    }

    return patternTable
  }

  const patternTable = _buildPatternTable(word)

  while (textIndex < text.length) {
    if (text[textIndex] === word[wordIndex]) {
      if (wordIndex === word.length - 1) {
        return (textIndex - word.length) + 1
      }
      wordIndex += 1
      textIndex += 1
    } else if (wordIndex > 0) {
      wordIndex = patternTable[wordIndex - 1]
    } else {
      wordIndex = 0
      textIndex += 1
    }
  }
  return -1
}

```
