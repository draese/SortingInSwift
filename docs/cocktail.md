# Cocktail Shaker Sort (variation of Bubble)

```
var swappedValues = true
var iterations = 0
while swappedValues {
    swappedValues = false
    iterations += 1
    
    for idx in 0..<(n-iterations) {  // move lagest to right
        if input[idx] > input[idx + 1] {
            swap(idx, idx + 1)
            swappedValues = true
        }
    }
    
    if swappedValues {
        for idx in stride(from: n - iterations, through: iterations, by: -1) { // move smallest to left
            if input[idx] < input[idx - 1] {
                swap(idx, idx - 1)
            }
        }
    }
}
```

    [7, 2, 10, 5, 17, 3] <--- original
    [2, 3, 7, 5, 10, 17]
    [2, 3, 5, 7, 10, 17]
    [2, 3, 5, 7, 10, 17]

This variation of BubbleSort flip-flops between bubbling the largest value to the right and the smallest value to the left, reducing the space to scan by (2 * iteration) each time.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/gUid9vrD5eQ).

Back to [overview](../README.md).
