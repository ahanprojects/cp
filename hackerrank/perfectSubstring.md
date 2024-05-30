Masih kurang efisien (7/10)
```js
/*
 * Complete the 'perfectSubstring' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. STRING s
 *  2. INTEGER k
 */
function perfectSubstring(s, k) {
  // BRUTE FORCE, sorry not enough time :)
  const allSubstring = []
  
  for (let i = 0; i < s.length; i++) {
    for (let j = i + k - 1; j < s.length; j += k) {
      allSubstring.push(s.substring(i, j + 1))
    }
  }  
  
  // Check each substring
  let perfectCount = 0
  for (let str of allSubstring) {
    let charCount = {}
    
    for (let c of str) {
      charCount[c] = (charCount[c] ?? 0) + 1
    }
    
    if (Object.values(charCount).every(count => count == k)) {
      perfectCount += 1
    }
  }
  return perfectCount

}
```