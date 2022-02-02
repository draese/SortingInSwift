# Sorting In Swift
Collection of sorting algorithms and their complexity categories with sample code in Swift

Sorting algorithms are classified as Best/Average/Worst case scenario in regards to time-complexity (BigO) and worst case scenario for space complexity where the space is only additional space. Therefore, in-place sorting algorithms do not have any additional space complexity. Therefore, while there is no sorting algorithm with an O(1) time complexity, there are some with an O(1) space complexity.

| Sort Algorithm | Remarks | Time Complexity Best | Time Complexity Avg | Time Complexity Worst | Space Complexity (Worst) |
| -------------- | ------- | -------------------- | ------------------- | ----------------------| ------------------------ |
| [Selection](docs/selection.md) | InPlace, comparison based unstable (1) | O(n^2) | O(n^2) | O(n^2) | O(1) |
| [Bubble](docs/bubble.md) | InPlace, comparison based, stable | O(n) (if presorted) | O(n^2) | O(n^2) | O(1) |
| [Cocktail Shaker](docs/cocktail.md) | Variation of Bubble, InPlace, comparison based, stable | O(n) (if sorted) | O(n^2) | O(n^2) | O(1) |
| [Odd/Even](docs/oddeven.md) | Variation of Bubble, InPlace, comparison based, stable | O(n) (if sorted) | O(n^2) | O(n^2) | O(1) |
| [Merge](docs/merge.md) | stable, comparison based, recursive divide & conquer | O(n log n) | O(n log n) | O(n log n) | O(n) (Requires one extra temp copy if output is written into input array |
| [Cycle](docs/cycle.md) | unstable, comparison based, InPlace | O(n^2) | O(n^2) | O(n^2) | O(1) |
| [Quick](docs/quick.md) | unstable, comparison based, InPlace, divide & conquer | O(n log n) | O(n log n) | O(n^2) | O(log n) Space is not required for actual data elements (InPlace) but for recursion |
| [Bitonic](docs/bitonic.md) | unstable, comparison based, InPlace, divide & conquer , optimized for parallelism | O(log n) | O(log n) | O(log n) | O(n log n) due to the nested recursion |
| [Heap](docs/heap.md) | unstable, comparison based, inPlace | O(n log n) | O(n log n) | O(n log n) | O(1) |
| [Insertion](docs/insertion.md) | stable, comparison based, inPlace | O(n) (if sorted) | O(n^2) | O(n^2) | O(1) |
| [Shell](docs/shell.md) | unstable, comparison based, inPlace | O(n log n) | O(n log n) | O(n^2) | O(1) |
| [Counting](docs/counting.md) | stable, comparison based, usable for very small value ranges (k) | O(n + k) w/ k being the range between lowest and highest element value | O(n + k) w/ k being the range between lowest and highest element value | O(n + k) w/ k being the range between lowest and highest element value | O(n + k) k = array for each element in range lo..hi |
| [Radix](docs/radix.md) | stable, comparison based, used for large elements (n) with lower number of key-digits (d) | O(d(n + b)) with d = max number digits and b=base | O(d(n + b)) with d = max number digits and b=base | O(d(n + b)) with d = max number digits and b=base | O(n + b) |
