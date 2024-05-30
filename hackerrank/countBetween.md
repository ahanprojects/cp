Kurang efisien (7/10)
Harusnya pake Binary search, jangan linear
`for (let n of arr) {
        if (n >= l && n <= h) count++
      }
`
```js
/*
 * Complete the 'countBetween' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts following parameters:
 *  1. INTEGER_ARRAY arr
 *  2. INTEGER_ARRAY low
 *  3. INTEGER_ARRAY high
 */

function countBetween(arr, low, high) {
    // Write your code here
    const ans = []
    for (let i = 0; i < low.length; i++) {
      let count = 0
      const l = low[i]
      const h = high[i]
      
      for (let n of arr) {
        if (n >= l && n <= h) count++
      }
      ans.push(count)
      
    }
    return ans
}
```