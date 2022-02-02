# Counting Sort

```
// determine the value range
var lo = Int.max
var hi = Int.min
for v in input {
    lo = min(lo, v)
    hi = max(hi, v)
}

// populate count array
var counts = [Int](repeating: 0, count: hi - lo + 1)
for v in input {
    counts[v - lo] += 1
}

// convert counts into starting index array
var sum = 0
for countIdx in 0 ..< counts.count - 1{
    sum += counts[countIdx]
    counts[countIdx] = sum
}

// shift counts to right. now each is a current index
counts = Array([0] + counts[0 ..< counts.count - 1])

// populate new array with sorted (stable) values
var output = [Int](repeating: 0, count: input.count)
for original in input {
    let indexArrayPos = original - lo
    let targetPosition = counts[indexArrayPos]
    counts[indexArrayPos] += 1
    output[targetPosition] = original
}
```

    [3, 1, 1, 2, 0, 3, 0, 2, 3, 3, 1] <--- original
    -> Determined range from 0 to 3
    -> Counts by value (with base 0): [2, 3, 2, 4]
    -> Converted to starting positions [2, 5, 7, 4]
    -> Converted to starting positions shifted [0, 2, 5, 7]
    [0, 0, 1, 1, 1, 2, 2, 3, 3, 3, 3] <--- result

CountingSort is suitable for a small range of possible values. In the above example, we only have a range of 4 different values from zero to three.  In the first step, each occurrence of a particular value is counted. Then these counts are aggregated up to generate an array of starting indexes (if the original values were sorted). Lastly, the original content is copied over into a new array, where the starting indexes are now used as running index to determine the correct storage position for an entry when it is inserted into the output.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/OKd534EWcdk).

Back to [overview](../README.md).