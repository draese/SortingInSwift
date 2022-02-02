# Shell Sort

```
var gap = input.count / 2
while gap > 0 {
    for i in gap ..< input.count {
        let key = input[i]
        var j = i
        
        while j >= gap && input[j - gap] > key {
            input[j] = input[j - gap]
            j -= gap
        }

        input[j] = key
    }
    
    gap /= 2
}
```

ShellSort is a variation of InsertionSort. The main issue (O(n^2) time complexity) of insertion sort is that sometimes elements have to be all copied over to their right neighbor to move a key from right to left. This is addressed by ShellSort by splitting the input into sublists of equal "gap" size and to perform an InsertionSort in gap steps. The elements are essentially moved in multiples of gap rather than one position each time. The gap is narrowed down, until it is one and we essentially perform a standard insertion sort. 

    [3, 5, 1, 10, 9, 4, 2, 7] <--- original
    [3, 5, 1, 10, 9, 4, 2, 7] after i=4, gap=4
    [3, 4, 1, 10, 9, 5, 2, 7] after i=5, gap=4
    [3, 4, 1, 10, 9, 5, 2, 7] after i=6, gap=4
    [3, 4, 1, 7, 9, 5, 2, 10] after i=7, gap=4
    [1, 4, 3, 7, 9, 5, 2, 10] after i=2, gap=2
    [1, 4, 3, 7, 9, 5, 2, 10] after i=3, gap=2
    [1, 4, 3, 7, 9, 5, 2, 10] after i=4, gap=2
    [1, 4, 3, 5, 9, 7, 2, 10] after i=5, gap=2
    [1, 4, 2, 5, 3, 7, 9, 10] after i=6, gap=2
    [1, 4, 2, 5, 3, 7, 9, 10] after i=7, gap=2
    [1, 4, 2, 5, 3, 7, 9, 10] after i=1, gap=1
    [1, 2, 4, 5, 3, 7, 9, 10] after i=2, gap=1
    [1, 2, 4, 5, 3, 7, 9, 10] after i=3, gap=1
    [1, 2, 3, 4, 5, 7, 9, 10] after i=4, gap=1
    [1, 2, 3, 4, 5, 7, 9, 10] after i=5, gap=1
    [1, 2, 3, 4, 5, 7, 9, 10] after i=6, gap=1
    [1, 2, 3, 4, 5, 7, 9, 10] after i=7, gap=1
    [1, 2, 3, 4, 5, 7, 9, 10] <--- result

Depending on the input data, variations of the gap function (other than div 2 as used here) can improve the time complexity of ShellSort.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/nki-MWeE2kQ).

Back to [overview](../README.md).