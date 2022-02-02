# Bubble Sort

```
var swappedValues = true
var iterations = 0
while swappedValues {
    swappedValues = false
    iterations += 1
    
    for idx in 0..<(n-iterations) {  // move largest to right
        if input[idx] > input[idx + 1] {
            swap(idx, idx + 1)
            swappedValues = true
        }
    }
}
```

    [7, 2, 10, 5, 17, 3] <--- original
    [2, 7, 5, 10, 3, 17]
    [2, 5, 7, 3, 10, 17]
    [2, 5, 3, 7, 10, 17]
    [2, 3, 5, 7, 10, 17]
    [2, 3, 5, 7, 10, 17]

Iterates from the beginning of the input to the end (minus iterations) to swap out the elements at i and i + 1 if input[i] is greater than input[i + 1]. This way, each iteration bubbles the largest value in its 0...(end-iteration) range towards the end of the data.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/vSk8tejmNlI).

Back to [overview](../README.md).