# Merge Sort

A sorting technique based on divide and conquer technique by dividing the array into equal halves and then combine them in a sorted manner.

How it works:
1. If it is only one element in the list it is already sorted.
2. Divide the array recursively into two halves until it can no longer be divided.
3. Merge the smaller arrays into a new array into sorted order.

Example usage of Merge Sort:
```javascript
function mergeSort(array) {
    if (array.length <= 1) { // Base case: If the array has 0 or 1 element, it is already sorted
        return array;
    }
    
    const middle = Math.floor(array.length / 2); // Find the middle index of the array

    // Divide the array into two halves
    const leftHalf = array.slice(0, middle);
    const rightHalf = array.slice(middle);

    // Recursively call mergeSort on the left and right halves
    const sortedLeftHalf = mergeSort(leftHalf);
    const sortedRightHalf = mergeSort(rightHalf);

    return merge(sortedLeftHalf, sortedRightHalf);// Merge the sorted halves
}

function merge(left, right) { // Helper function to merge two sorted arrays
    let result = [];
    let leftIndex = 0;
    let rightIndex = 0;

    while (leftIndex < left.length && rightIndex < right.length) { // Compare elements from left and right arrays and add the smaller element to the result
        if (left[leftIndex] < right[rightIndex]) {
        result.push(left[leftIndex]);
        leftIndex++;
        } else {
        result.push(right[rightIndex]);
        rightIndex++;
        }
    }

    while (leftIndex < left.length) { // Add any remaining elements from the left or right array
        result.push(left[leftIndex]);
        leftIndex++;
    }

    while (rightIndex < right.length) {
        result.push(right[rightIndex]);
        rightIndex++;
    }

    return result;
}

// Example usage
const unsortedArray = [7, 2, 1, 6, 8, 5, 3, 4];
const sortedArray = mergeSort(unsortedArray);
console.log(sortedArray); // [1, 2, 3, 4, 5, 6, 7, 8]
```

