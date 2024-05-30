```js
/*
 * Complete the 'countSentences' function below.
 *
 * The function is expected to return a LONG_INTEGER_ARRAY.
 * The function accepts following parameters:
 *  1. STRING_ARRAY wordSet
 *  2. STRING_ARRAY sentences
 *  0 => 1
 *  1 => 2
 */
function countSentence(splitted, anagramMap) {
  let anagramCount = 1
  for (const w of splitted) {
    const key = w.split('').sort().join('')
    if (anagramMap[key] > 1) {
      anagramCount *= anagramMap[key]
    }
  }
  return anagramCount
}

function countSentences(wordSet, sentences) {
  const anagramMap = {}
  
  for (const w of wordSet) {
    const key = w.split('').sort().join('')
    anagramMap[key] = (anagramMap[key] ?? 0) + 1
  }
  
  const result = []
  for (let sentence of sentences) {
    const splitted = sentence.split(' ')
    const count = countSentence(splitted, anagramMap)
    result.push(count)
  }
  return result
}
```