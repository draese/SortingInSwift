# Cycle Sort

```
var currentElement: Int = 0
var targetElementPosition: Int = 0

for outerIndex in 0 ..< (input.count - 1) {
    currentElement = input[outerIndex]
    findPositionForCurrentElement(startingAt: outerIndex)
        
    // stop here if the cycle is completed
    while targetElementPosition != outerIndex {
        swapWithCurrentElement()
        findPositionForCurrentElement(startingAt: outerIndex)
    }
    
    swapWithCurrentElement()
}

func findPositionForCurrentElement(startingAt: Int)  {
    targetElementPosition = startingAt
    for scanIndex in startingAt + 1 ..< input.count {
        if currentElement >= input[scanIndex] {
            targetElementPosition += 1
        }
    }
}

func swapWithCurrentElement() {
    let temp = input[targetElementPosition]
    input[targetElementPosition] = currentElement
    currentElement = temp
}
```

    [3, 5, 1, 10, 9, 4, 2, 7] <--- original
    After outerIndexIteration 0: [1, 5, 3, 10, 9, 4, 2, 7] with compositionGroup=[1, 3]
    After outerIndexIteration 1: [1, 2, 3, 10, 5, 4, 9, 7] with compositionGroup=[9, 2, 5]
    After outerIndexIteration 2: [1, 2, 3, 10, 5, 4, 9, 7] 
    After outerIndexIteration 3: [1, 2, 3, 4, 5, 7, 9, 10] with compositionGroup=[7, 4, 10]
    After outerIndexIteration 4: [1, 2, 3, 4, 5, 7, 9, 10] 
    After outerIndexIteration 5: [1, 2, 3, 4, 5, 7, 9, 10] 
    After outerIndexIteration 6: [1, 2, 3, 4, 5, 7, 9, 10] 

The Cycle sort determines the right position for each element and swaps it into that position. The element that is replaced (in that position) is becoming the new element for which to find the right position. This is going on, until a cycle is completed. For the above example, we determine that the right position for value 3 is actually at index 2 and swap it in. Then we make the original value at index 2 (1) the new currentElement and find it's position, which happens to be zero. At that moment, a cycle is closed and we iterate on the next outer loop.  The algorithm could of course be optimized by memorizing if an element was already swapped into its right position, allowing us to skip over it in the outer loop. But this would require additional space, while the original algorithm has a space complexity of O(1) and is optimized for a minimum number of writes.

CycleSort is optimized for the minimum of writes. An element is written to a new position either 1 or 0 times.  So, it is ideal if the storage location is slow.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/hX8seJh1cT0).

Back to [overview](../README.md).