# Selection Sort

```
for head in 0 ..< n {
    var smallest  = head
    for scan in head + 1 ..< n {
        if input[scan] < input[smallest] { // find smaller
            smallest = scan
        }
    }
    
    swap(smallest, head)
}
```

     [7, 2, 10, 5, 17, 3]  <--- original
     [2, 7, 10, 5, 17, 3]
     [2, 3, 10, 5, 17, 7]
     [2, 3, 5, 10, 17, 7]
     [2, 3, 5, 7, 17, 10]
     [2, 3, 5, 7, 10, 17]
     [2, 3, 5, 7, 10, 17]

Simply scans through the input from head to tail, finds the smallest element at swaps it to the front.

---
Description of the algorithm can be found [here on Youtube](https://youtu.be/i4hoyD4hUcg).

Back to [overview](../README.md).