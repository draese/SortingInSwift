# Merge Sort

```
func merge(_ list: [Int]) -> [Int] {
    print("merge called with input=\(list)")
    if list.count == 2 {
        // base case
        if list[0] < list[1] {
            return list
        } else {
            return list.reversed()
        }
    } else {
        // divide phase
        let middle = list.count / 2
        let leftSide = Array(list[0..<middle])
        let leftList = leftSide.count == 1 ? leftSide : merge(leftSide)
        let rightSide = Array(list[middle...])
        let rightList = rightSide.count == 1 ? rightSide : merge(rightSide)
        var leftIdx = 0
        var rightIdx = 0
        var ret = Array<Int>()
        
        // merge phase
        ret.reserveCapacity(leftList.count + rightList.count)
        while leftIdx < leftList.count && rightIdx < rightList.count {
            if leftList[leftIdx] < rightList[rightIdx] {
                ret.append(leftList[leftIdx])
                leftIdx += 1
            } else {
                ret.append(rightList[rightIdx])
                rightIdx += 1
            }
        }
        
        ret.append(contentsOf: leftList[leftIdx...])
        ret.append(contentsOf: rightList[rightIdx...])
        print("merge returning with left=\(leftList), right=\(rightList), merged=\(ret)")

        return ret
    }
}
```
	
    [7, 2, 22, 10, 5, 17, 3] <--- original
    merge called with input=[7, 2, 22, 10, 5, 17, 3]
    merge called with input=[7, 2, 22]
    merge called with input=[2, 22]
    merge returning with left=[7], right=[2, 22], merged=[2, 7, 22]
    merge called with input=[10, 5, 17, 3]
    merge called with input=[10, 5]
    merge called with input=[17, 3]
    merge returning with left=[5, 10], right=[3, 17], merged=[3, 5, 10, 17]
    merge returning with left=[2, 7, 22], right=[3, 5, 10, 17], merged=[2, 3, 5, 7, 10, 17, 22]

Of course, the divide phase here could have been performed with ArraySlices instead of copying arrays! Also, instead of generating a new output/return array, the result could be written to the input array again if a call-by-reference would be performed. Both parts have been ignored here to avoid derailing from the original algorithm demonstration. The above sample code actually has O(n log n) space complexity. Moving to writing output into the input array reduces this to O(n) space complexity.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/H16CCm3OOfo).

Back to [overview](../README.md).