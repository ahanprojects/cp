The Jungle Book
```js
function minimumGroups(predators) {
    // Write your code here
    // Bismillah
    let minGroup = 0
    for (let i = 0; i < predators.length; i++) {
      
      let count = 1
      let node = i
      
      while (predators[node] > -1) {
        count++
        node = predators[node]
      }
      
      minGroup = Math.max(minGroup, count)
      
    }
    return minGroup
}
```