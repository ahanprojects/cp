Ways to Sum
```js
function ways(total, k) {
  let map = Array(total + 1).fill(0)
  map[0] = 1
  
  for (let i = 1; i < k + 1; i++) {
    for (let j = 1; j < total + 1; j++) {
      if (i > j) continue
      map[j] = map[j] + map[j - i]
    }
  }
  return map[total]
}
```