```js
function slowestKey(keyTimes) {
    // Write your code here
    // Bismillah
    let t = -1
    let char = -1
    
    for (let i = 0; i < keyTimes.length; i++) {
      const subtract = (i == 0) ? 0 : keyTimes[i - 1][1]
      
      if (t < keyTimes[i][1] - subtract) {
        char = keyTimes[i][0]
        t = keyTimes[i][1] - subtract
      }
    }
    return String.fromCharCode(char + 97)
}
```