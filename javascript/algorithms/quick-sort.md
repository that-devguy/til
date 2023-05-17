# Quick Sort

The key idea behind Quick Sort is to divide and conquer the sorting task by selecting a pivot, partitioning the data, and recursively sorting the smaller partitions.

How it works:
1. An element in the array is picked to be the "pivot".
2. The remaining elements are divided into two groups. One group contains elements that are smaller than the pivot, and the other contains elements that are larger. This is referred to as **partitioning**.
3. Each group is focused on separately. The proccess is repeated **recursively**: choose a pivot for each group and partition the remaining elements until each group is small enough to be considered sorted.
4. Combine the sorted groups back together to form the fully sorted array.

*Quick Sort is fast and can sort large arrays efficiently*

```javascript
function quickSort(array) {
    if (array.length <= 1) { // Base case: If the array has 0 or 1 element, it is already sorted
        return array;
    }

    const pivot = array[array.length - 1]; // Choose a pivot element (here, we select the last element)

    // Create two empty arrays for elements smaller and larger than the pivot
    const smaller = [];
    const larger = [];
    
    for (let i = 0; i < array.length - 1; i++) { // Iterate through the array, excluding the pivot element
        if (array[i] < pivot) {
        smaller.push(array[i]); // Element is smaller than the pivot, add it to the 'smaller' array
        } else {
        larger.push(array[i]); // Element is larger than or equal to the pivot, add it to the 'larger' array
        }
    }

    // Recursively call quickSort on the 'smaller' and 'larger' arrays
    // Concatenate the sorted 'smaller' array, the pivot, and the sorted 'larger' array
    return [...quickSort(smaller), pivot, ...quickSort(larger)];
}

// Example usage
const unsortedArray = [7, 2, 1, 6, 8, 5, 3, 4];
const sortedArray = quickSort(unsortedArray);
console.log(sortedArray); // [1, 2, 3, 4, 5, 6, 7, 8]
```


