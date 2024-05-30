10/10
```js
/*
 * Complete the 'smallestString' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING_ARRAY substrings as parameter.
 */
function sort(a) {
  for (let i = 0; i < a.length; i++) {
    for (let j = i + 1; j < a.length; j++) {
      if ((a[i] + a[j]) > (a[j] + a[i])) {
        let temp = a[i]
        a[i] = a[j]
        a[j] = temp
      }
    }
  }
}

function smallestString(substrings) {
  sort(substrings)
  return substrings.join('')
}
```