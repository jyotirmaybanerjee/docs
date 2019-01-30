## Merge Sort

```javascript
var unsortedArr = [340, 1, 3, 3, 76, 23, 4, 12, 122, 7642, 646];

function merge(leftArr, rightArr) {
    var sortedArr = [];
    while (leftArr.length && rightArr.length) {
        if (leftArr[0] <= rightArr[0]) {
            sortedArr.push(leftArr[0]);
            leftArr = leftArr.slice(1)
        } else {
            sortedArr.push(rightArr[0]);
            rightArr = rightArr.slice(1)
        }
    }
    while (leftArr.length)
        sortedArr.push(leftArr.shift());
    while (rightArr.length)
        sortedArr.push(rightArr.shift());
    return sortedArr;
}

function mergesort(arr) {
  if (arr.length < 2) {
    return arr;
  }
  else {
    var midpoint = parseInt(arr.length / 2);
    var leftArr   = arr.slice(0, midpoint);
    var rightArr  = arr.slice(midpoint, arr.length);
    return merge(mergesort(leftArr), mergesort(rightArr));
  }
}

console.log('This should be the sorted array!');
console.log(mergesort(unsortedArr));
```


## Bubble Sort

![Bubble sort](images/bubble_sort.gif)
![Bubble sort](images/bubble_sort_2.png)

```javascript
function bubbleSort(items) {
  var length = items.length;
  for (var i = 0; i < length; i++) { //Number of passes
    for (var j = 0; j < (length - i - 1); j++) { //Notice that j < (length - i)
      //Compare the adjacent positions
      if (items[j] > items[j + 1]) {
        //Swap the numbers
        var tmp = items[j]; //Temporary variable to hold the current number
        items[j] = items[j + 1]; //Replace current number with adjacent number
        items[j + 1] = tmp; //Replace adjacent number with current number
      }
    }
  }
}

```


## Insertion Sort

![Insertion Sort](images/insertion_sort_amin.gif)
![Insertion Sort](images/insertion_sort_2.gif)
![Insertion Sort](images/insertion_sort_performance.png)

```javascript
function insertionSort(unsortedList) {
	var len = unsortedList.length;
	for (var i = 1; i < len; i++) {
		var tmp = unsortedList[i]; //Copy of the current element. 
		/*Check through the sorted part and compare with the number in tmp. If large, shift the number*/
		for (var j = i - 1; j >= 0 && (unsortedList[j] > tmp); j--) {
			//Shift the number
			unsortedList[j + 1] = unsortedList[j];
		}
		//Insert the copied number at the correct position
		//in sorted part. 
		unsortedList[j + 1] = tmp;
	}
}

var ul = [5, 3, 1, 2, 4];
insertionSort(ul);
console.log(ul);
```