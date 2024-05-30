10/10
```js
/*
 * Complete the 'firstRepeatedWord' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING sentence as parameter.
 */

function firstRepeatedWord(sentence) {
    const words = sentence.split(/[ \t,;:\-.]+/)
    const seen = new Set()
    for (const word of words) {
      // if (word === '') continue
      if (seen.has(word)) return word
      seen.add(word)
    }
    return null
}
```