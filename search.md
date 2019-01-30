## Binary Search

```javascript
function binarySearch(searchArray, searchElement) {
  let minIndex = 0;
  let maxIndex = searchArray.length;
  let currentIndex;
  let currentElement;
  while (minIndex <= maxIndex) {
    currentIndex = Math.floor((maxIndex + minIndex) / 2);
    currentElement = searchArray[currentIndex];
    if (searchElement < currentElement) {
      maxIndex = currentIndex - 1;
    } else if (searchElement > currentElement) {
      minIndex = currentIndex + 1;
    } else {
      return currentIndex;
    }
  }
  return -1;
}

console.log(binarySearch([1,2,3,4,5,6,7,8], 8));
```