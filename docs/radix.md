# Radix Sort

```
let d = Int(ceil(log10(Double(input.max()!))))
for digitPos in 0 ..< d {
    let div = Int(pow(Double(10), Double(digitPos)))
    var counts = [Int](repeating: 0, count: 10)
    
    for v in input {
        let key = (v / div) % 10
        counts[key] += 1
    }
    
    var sum = 0
    for countIdx in 0...8 {
        sum += counts[countIdx]
        counts[countIdx] = sum
    }
    
    // shift counts to right. now each is a current index
    counts = Array([0] + counts[0 ..< counts.count - 1])

    var tempSpace = [Int](repeating: 0, count: input.count)
    for original in input {
        let key = (original / div) % 10
        let targetPosition = counts[key]
        counts[key] += 1
        tempSpace[targetPosition] = original
    }

    input = tempSpace
}
```

RadixSort is a variation of CountingSort.  Instead of considering the full range of all values (lo...hi), we only count a digit (lowest to highest) at a time. This is considered to be the key. For a base-10 number, this means that we only have 10 different key values and therefore 10 count buckets. The algorithm starts with the lowest digit (ones) and re-runs the CountingSort for the next higher digit (tens, then hundreds) until the maximum number of digits (d) is processed. 

    [52, 89, 150, 36, 633, 233] <--- original
    Sorted after 0-digit are: [150, 52, 633, 233, 36, 89]
    Sorted after 1-digit are: [633, 233, 36, 150, 52, 89]
    Sorted after 2-digit are: [36, 52, 89, 150, 233, 633]
    [36, 52, 89, 150, 233, 633] <--- result

The time complexity of this algorithm is O(d(n + b)) with b being a constant (here 10 but this could for example also be 255 for byte-comparison), this algorithm essentially scales very well for large n and small d (number of digits) in which case it can compete with the O(n log n) time complexity of QuickSort or MergeSort. The value of (b) is becoming a neglectable  constant and for small (d) the time complexity for large (n) essentially becomes O(n). As CountingSort is table, RadixSort is inherently stable as well.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/XiuSW_mEn7g).