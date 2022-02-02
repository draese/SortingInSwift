# Quick Sort

```
func quickSort(aroundSlice: inout ArraySlice<Int>) {
    if aroundSlice.count < 2 {
        return
    } else if aroundSlice.count == 2 {
        if aroundSlice.first! > aroundSlice.last! {
            aroundSlice.reverse()
        }
        
        return
    }

    let pivotIndex = aroundSlice.endIndex - 1    // last valid idx is endIdx-1
    let pivotElement = aroundSlice[pivotIndex]   // is the last element of the slice
    var frontIdx = aroundSlice.startIndex
    var endIdx = pivotIndex - 1                  // start one lower than the pivot element

    // partition data into smaller pivotElement (left) and greater pivotElement (right)
    while true {
        // get next swappable elements
        while aroundSlice[frontIdx] < pivotElement && frontIdx < endIdx { frontIdx += 1 }
        while aroundSlice[endIdx] > pivotElement && endIdx > frontIdx { endIdx -= 1 }
        
        if frontIdx < endIdx {
            swap(inSlice: &aroundSlice, firstIndex: frontIdx, secondIndex: endIdx)
        } else {
            break
        }
    }
    
    // swap the pivot point between the lower and the higher partitions
    swap(inSlice: &aroundSlice, firstIndex: frontIdx, secondIndex: pivotIndex)
    
    // recurse on each partition (left and right of the pivot element)
    quickSort(aroundSlice: &aroundSlice[aroundSlice.startIndex..<frontIdx])
    quickSort(aroundSlice: &aroundSlice[(frontIdx + 1)...])
    
    func swap(inSlice: inout ArraySlice<Int>, firstIndex: Int, secondIndex: Int) {
        let temp = inSlice[firstIndex]
        inSlice[firstIndex] = inSlice[secondIndex]
        inSlice[secondIndex] = temp
    }
}
```

    [3, 5, 1, 10, 9, 4, 2, 7] <--- original
    [3, 5, 1, 10, 9, 4, 2, 7] <- using pivotElement = 7
    [3, 5, 1, 2, 4]           <- using pivotElement = 4
    [3, 2, 1]                 <- using pivotElement = 1
    [2, 3]                    <- recursion on 2 element slice
    [9, 10]                   <- recursion on 2 element slice
    [1, 2, 3, 4, 5, 7, 9, 10] <--- result

QuickSort defines a pivot element (the above code just uses the last one in the slice) and then partitions the slice into elements that are smaller than the pivot and a partition where the elements are larger than the pivot. At the end of this, the pivot element is in its right, final position while the partitions to its left, containing smaller values and the partition to the right with the higher values are still unsorted. It performs a recursive call into each of these partitions and only stops if less than 3 elements are in the partition. This is a very efficient in-place sort.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/_Tf0DXpbRRE).

Back to [overview](../README.md).