# Insertion Sort

```
for i in 1 ..< input.count {
    let key = input[i]
    var j = i - 1
    
    while j >= 0 && input[j] > key {
        input[j + 1] = input[j]
        j -= 1
    }
    
    input[j + 1] = key
}
```

Insertion sort essentially copies all elements that are larger than the key element (which goes from 1...end) to the right and then inserts the key element at its position. For roughly sorted data, this might be very efficient, for reverse sorted data, this means that every element is essentially moved twice.

    [3, 5, 1, 10, 9, 4, 2, 7] <--- original
    [3, 5, 1, 10, 9, 4, 2, 7] after i=1
    [1, 3, 5, 10, 9, 4, 2, 7] after i=2
    [1, 3, 5, 10, 9, 4, 2, 7] after i=3
    [1, 3, 5, 9, 10, 4, 2, 7] after i=4
    [1, 3, 4, 5, 9, 10, 2, 7] after i=5
    [1, 2, 3, 4, 5, 9, 10, 7] after i=6
    [1, 2, 3, 4, 5, 7, 9, 10] after i=7
    [1, 2, 3, 4, 5, 7, 9, 10] <--- result

The whole algorithm makes only sense if new data (relative small) is inserted into a larger already sorted list of data.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/dCpgT9khD7A).

Back to [overview](../README.md).