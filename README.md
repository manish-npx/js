# JavaScript Algorithms & Data Structures -- Interview Preparation

## Data Structures (Array, Object, Set, Map)

### Array Utilities

-   Find duplicates\
-   Remove duplicates\
-   Map, filter, reduce examples

### Object Utilities

-   Deep clone\
-   Flatten object

### Set Utilities

-   Union\
-   Subset\
-   Intersection\
-   Symmetric difference

### Map Utilities

-   Merge maps\
-   Count occurrences\
-   Reverse map


## Math Algorithms

### Fibonacci Series

``` js
const fibNo = (n) => {
  const fib = [0, 1];
  for (var i = 2; i < n; i++) {
    fib[i] = fib[i - 1] + fib[i - 2];
  }
  return fib;
};
console.log("Fib seq is:-", fibNo(5));
console.log("Fib seq is:-", fibNo(7));
```

### Factorial

``` js
const factorial = (n) => {
  let element = 1;
  for (let i = 2; i <= n; i++) {
    element = element * i;
  }
  return element;
};
console.log("factorial is:-", factorial(5));
```

### Prime Number Check

``` js
const prime = (n) => {
  if (n < 2) return false;
  for (let index = 2; index < n; index++) {
    if (n % index === 0) return false;
  }
  return true;
};
console.log("is Prime?:-", prime(5));
console.log("is Prime?:-", prime(4));
```

Optimized:

``` js
const primeOptimal = (n) => {
  if (n < 2) return false;
  for (let index = 2; index <= Math.sqrt(n); index++) {
    if (n % index === 0) return false;
  }
  return true;
};
```

### Power of Two

``` js
const isPowerOfTwo = (n) => {
  if (n < 1) return false;
  while (n > 1) {
    if (n % 2 !== 0) return false;
    n = n / 2;
  }
  return true;
};
```

Bitwise method:

``` js
function isPowerOfTwoBitWise(n) {
  if (n < 1) return false;
  return (n & (n - 1)) == 0;
}
```

## Recursion

### Fibonacci (Recursive)

``` js
const fibonacci = (n) => {
  if (n < 2) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
};
```

### Factorial (Recursive)

``` js
const recursiveFactorial = (n) => {
  if (n === 0) return 1;
  return n * recursiveFactorial(n - 1);
};
```

## Search Algorithms

### Linear Search

``` js
const linearSearch2 = (arr, target) => {
  for (let index = 0; index < arr.length; index++) {
    if (arr[index] === target) return index;
  }
  return -1;
};
```

### Binary Search

``` js
const binarySearch = (arr, target) => {
  let start = 0;
  let end = arr.length - 1;
  while (start <= end) {
    let mid = Math.floor((start + end) / 2);
    if (arr[mid] == target) return mid;
    if (target > arr[mid]) start = mid + 1;
    else end = mid - 1;
  }
  return -1;
};
```

Recursive:

``` js
function search(arr, target, left, right) {
  if (left > right) return -1;
  let mid = Math.floor((left + right) / 2);
  if (target === arr[mid]) return mid;
  if (target < arr[mid]) return search(arr, target, left, mid - 1);
  return search(arr, target, mid + 1, right);
}
```

## Sorting Algorithms

### Bubble Sort

``` js
const bubbleShort = (arr) => {
  let swapped;
  do {
    swapped = false;
    for (let index = 0; index < arr.length - 1; index++) {
      if (arr[index] > arr[index + 1]) {
        let temp = arr[index];
        arr[index] = arr[index + 1];
        arr[index + 1] = temp;
        swapped = true;
      }
    }
  } while (swapped);
  return arr;
};
```

### Insertion Sort

``` js
const insertionSport = (array) => {
  for (let index = 1; index < array.length; index++) {
    let numberToInsert = array[index];
    let j = index - 1;
    while (j >= 0 && array[j] > numberToInsert) {
      array[j + 1] = array[j];
      j--;
    }
    array[j + 1] = numberToInsert;
  }
};
```

### Quick Sort

``` js
const quickSort = (arr) => {
  if (arr.length < 2) return arr;
  let pivot = arr[arr.length - 1];
  let left = [];
  let right = [];

  for (let i = 0; i < arr.length - 1; i++) {
    if (arr[i] < pivot) left.push(arr[i]);
    else right.push(arr[i]);
  }
  return [...quickSort(left), pivot, ...quickSort(right)];
};
```

### Merge Sort

``` js
const mergeSort = (arr) => {
  if (arr.length < 2) return arr;
  const mid = Math.floor(arr.length / 2);
  const leftArr = arr.slice(0, mid);
  const rightArr = arr.slice(mid);
  return merge(mergeSort(leftArr), mergeSort(rightArr));
};

function merge(leftArr, rightArr) {
  const sortedArr = [];
  while (leftArr.length && rightArr.length) {
    if (leftArr[0] <= rightArr[0]) sortedArr.push(leftArr.shift());
    else sortedArr.push(rightArr.shift());
  }
  return [...sortedArr, ...leftArr, ...rightArr];
}
```

------------------------------------------------------------------------

File automatically generated.
