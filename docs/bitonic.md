# Bitonic Sort

```
func bitonicSort(aroundSlice: inout ArraySlice<Int>, isAscending: Bool) {
    // base case: stop at 1
    if aroundSlice.count > 1 {
        // divide/conquer (sort phase)
        let k = aroundSlice.count / 2
        bitonicSort(aroundSlice: &aroundSlice[aroundSlice.startIndex ..< aroundSlice.startIndex + k], isAscending: true)
        bitonicSort(aroundSlice: &aroundSlice[(aroundSlice.startIndex + k)...], isAscending: false)

        merge(slice: &aroundSlice)
    }

    func merge(slice: inout ArraySlice<Int>) {
        if slice.count > 1 {
            let k = slice.count / 2
            
            for idx in slice.startIndex ..< slice.startIndex + k {
                if (slice[idx] > slice[idx + k]) == isAscending {
                    swap(inSlice: &slice, firstIndex: idx, secondIndex: idx + k)
                }
            }
            
            merge(slice: &slice[slice.startIndex ..< slice.startIndex + k])
            merge(slice: &slice[(slice.startIndex + k)...])
        }
    }
    
    func swap(inSlice: inout ArraySlice<Int>, firstIndex: Int, secondIndex: Int) {
        let temp = inSlice[firstIndex]
        inSlice[firstIndex] = inSlice[secondIndex]
        inSlice[secondIndex] = temp
    }
}
```

    [3, 5, 1, 10, 9, 4, 2, 7] <--- original
    [3, 5]                         isAscending=true
    [10, 1]                        isAscending=false
    [1, 3, 5, 10]                  isAscending=true
    [4, 9]                         isAscending=true
    [7, 2]                         isAscending=false
    [9, 7, 4, 2]                   isAscending=false
    [1, 2, 3, 4, 5, 7, 9, 10]      isAscending=true
    [1, 2, 3, 4, 5, 7, 9, 10] <--- result

Bitonic definition is if given an index i, all elements below i are in ascending and all elements after i are descending. BitonicSort generates ascending/descending swapped sequences that are then merged back together to a larger sequence. Both, the splitting of the data as well as merging the sequences again are both (nested) recursive. The whole algorithm requires that the input dataset is having a 2^n size. BitonicSort is a primary candidate for parallel (SIMD or MP) processing on sequences of the data.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/uEfieI0MumY).

Back to [overview](../README.md).