# Bubble Sort

A simple sorting algorithm that repeatedly steps through the list that's being sorted and compares each pair of adjacent items and swap them if they are in the wrong order. This is repeated until no more swaps are needed, indicating that the list is sorted.

How it works:
1. Starting from the first element in the list, compare it to the next element.
2. If the current element is greater, swap them.
3. If the current element is less, move on to the next.
4. Repeat, starting from step 1.

*Bubble Sort only considers one element at a time and is time consuming. Due to inefficiency it's almost never used in production code.*

Example of bubble sort:

```javascript
let bubbleSort = (inputArr) => {
    let len = inputArr.length; // Get the number of elements in the array.
    let checked;
    do {
        checked = false; // Assume no swaps are needed initially.
        for (let i = 0; i < len; i++) {
            if (inputArr[i] > inputArr[i + 1]) { // Compare adjacent numbers.
                let tmp = inputArr[i]; // Swap the numbers if they are in the wrong order.
                inputArr[i] = inputArr[i + 1];
                inputArr[i + 1] = tmp;
                checked = true; // Mark that a swap has occurred.
            }
        }
    } while (checked); // Repeat the process until no more swaps are needed.

    return inputArr; // Return the sorted array.
};
```

In this example, we start with the assumption that no number swaps are needed.

We repeat the following steps until we don't have to make any more swaps:
- Compare each number with the one next to it in the array.
- If a number is greater than the next one, we swap them to put them in the correct order.
- We mark that a swap has occurred.

We then repeat these steps until no more swaps are needed. Finally, we return the sorted array.