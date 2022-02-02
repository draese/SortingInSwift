# Heap Sort

```
func heapSort(sortData: inout [Int]) {
    // step 1: heapify (maxheap) the array, starting with last parent node
    for i in stride(from: sortData.startIndex + (sortData.count / 2) - 1, through: 0, by: -1)   {
        heapify(parentNodeIndex: i)
    }

    // step 2: repeatedly push largest max-heap element (at zero) to position
    for i in 0 ..< sortData.count - 1 {
        swap(sortData.startIndex, sortData.endIndex - i - 1)
        heapify(parentNodeIndex: sortData.startIndex, numHeapElements: sortData.count - i - 1)
    }

    func heapify(parentNodeIndex: Int, numHeapElements: Int = sortData.count) {
        var largestIndex = parentNodeIndex
        let endPosition = sortData.startIndex + numHeapElements
        let leftChild = (largestIndex * 2) + 1
        let rightChild = leftChild + 1
        
        if leftChild < endPosition && sortData[largestIndex] < sortData[leftChild] {
            largestIndex = leftChild
        }
        
        if rightChild < endPosition && sortData[largestIndex] < sortData[rightChild] {
            largestIndex = rightChild
        }
        
        if largestIndex > parentNodeIndex {
            swap(largestIndex, parentNodeIndex)
            heapify(parentNodeIndex: largestIndex, numHeapElements: numHeapElements)
        }
    }

    func swap(_ firstIdx: Int, _ secondIdx: Int) {
        let temp = sortData[firstIdx]
        sortData[firstIdx] = sortData[secondIdx]
        sortData[secondIdx] = temp
    }
}
```

In the first phase, the input data is heapified. This starts with the last parent node (middle of the array) towards the root (beginning of the array), doing recursive swap down if the parent is smaller than the largest child. The result is a max-heap. The second phase pushes the root (largest element) to the end of the array and reduces the heap size by one (essentially removing the largest element and storing it at the new, free position towards the end of the array. The last heap element was swapped into the root location for the removal process and it needs to be heapified (pushed down) to its position. Note that the above sample code could also work on an array slice as it uses startIndex and endIndex instead of zero and count-1.

    [3, 5, 1, 10, 9, 4, 2, 7] <--- original
    [10, 9, 4, 7, 3, 1, 2, 5] <--- after initial heapify
    [9, 7, 4, 5, 3, 1, 2, 10] after sort iteration with i=0
    [7, 5, 4, 2, 3, 1, 9, 10] after sort iteration with i=1
    [5, 3, 4, 2, 1, 7, 9, 10] after sort iteration with i=2
    [4, 3, 1, 2, 5, 7, 9, 10] after sort iteration with i=3
    [3, 2, 1, 4, 5, 7, 9, 10] after sort iteration with i=4
    [2, 1, 3, 4, 5, 7, 9, 10] after sort iteration with i=5
    [1, 2, 3, 4, 5, 7, 9, 10] after sort iteration with i=6
    [1, 2, 3, 4, 5, 7, 9, 10] <--- result

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/1Rn10hHmp5I).

Back to [overview](../README.md).