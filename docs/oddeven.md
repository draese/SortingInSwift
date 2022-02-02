# Odd/Even Sort (variation of Bubble)

```
var swappedValues = true
while swappedValues {
    swappedValues = false
    
    // odd phase - only odd indexes
    for idx in stride(from: 1, to: n - 1, by: 2) {
        if input[idx] > input[idx + 1] {
            swap(idx, idx + 1)
            swappedValues = true
        }
    }
    
    // even pgase - only even indexes
    for idx in stride(from: 0, to: n - 1, by: 2) {
        if input[idx] > input[idx + 1] {
            swap(idx, idx + 1)
            swappedValues = true
        }
    }
}
```

    [7, 2, 10, 5, 17, 3] <--- original
    [2, 7, 5, 10, 3, 17]
    [2, 5, 3, 7, 10, 17]
    [2, 3, 5, 7, 10, 17]
    [2, 3, 5, 7, 10, 17]

This variation of BubbleSort fist performs a normal bubble sort on odd indexes, comparing for example elements at position 3 and 4 with each other and in a second loop the even index positions like 4 and 5.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/1UEWb_dgkq8).

Back to [overview](../README.md).