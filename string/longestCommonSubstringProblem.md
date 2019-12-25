#### 最长公共子串问题

```

最长公共子串是指 两个或者多个字符串找到最长相同的子字符串

比如 ABABC BABCA ABCBA 最长公共子串为 ABC 

ABABC
  |||
 BABCA
  |||
  ABCBA

```

```js

const longestCommonSubstring = (string1, string2) => {
  const s1 = [...string1]
  const s2 = [...string2]
  const substringMatrix = Array(s2.length + 1).fill(null).map(() => Array(s1.length + 1).fill(null))

  for (let columnIndex = 0; columnIndex <= s1.length; columnIndex += 1) {
    substringMatrix[0][columnIndex] = 0
  }

  for (let rowIndex = 0; rowIndex <= s2.length; rowIndex += 1) {
    substringMatrix[rowIndex][0] = 0
  }

  let longestSubstringLength = 0
  let longestSubstringColumn = 0
  let longestSubstringRow = 0

  for (let rowIndex = 1; rowIndex <= s2.length; rowIndex += 1) {
    for (let columnIndex = 1; columnIndex <= s1.length; columnIndex += 1) {
      if (s1[columnIndex - 1] === s2[rowIndex - 1]) {
        substringMatrix[rowIndex][columnIndex] = substringMatrix[rowIndex - 1][columnIndex - 1] + 1
      } else {
        substringMatrix[rowIndex][columnIndex] = 0
      }
      if (substringMatrix[rowIndex][columnIndex] > longestSubstringLength) {
        longestSubstringLength = substringMatrix[rowIndex][columnIndex]
        longestSubstringColumn = columnIndex
        longestSubstringRow = rowIndex
      }
    }
  }

  if (longestSubstringLength === 0) {
    return ''
  }

  let longestSubstring = ''

  while (substringMatrix[longestSubstringRow][longestSubstringColumn] > 0) {
    longestSubstring = s1[longestSubstringColumn - 1] + longestSubstring
    longestSubstringRow -= 1
    longestSubstringColumn -= 1
  }

  return longestSubstring
}

```
