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
![Bubble sort Performance](images/bubble_sort_2.png)


## Insertion Sort

![Insertion Sort](images/insertion_sort_amin.gif)
![Insertion Sort](images/insertion_sort_2.gif)

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
![Insertion Sort Performance](images/insertion_sort_performance.png)


## Selection Sort


```javascript
function selectionSort(items) {
	var length = items.length;
	for (var i = 0; i < length - 1; i++) {
		//Number of passes
		var min = i; //min holds the current minimum number position for each pass; i holds the Initial min number
		for (var j = i + 1; j < length; j++) { //Note that j = i + 1 as we only need to go through unsorted array
			if (items[j] < items[min]) { //Compare the numbers
				min = j; //Change the current min number position if a smaller num is found
			}
		}
		if (min != i) {
			//After each pass, if the current min num != initial min num, exchange the position.
			//Swap the numbers 
			var tmp = items[i];
			items[i] = items[min];
			items[min] = tmp;
		}
	}
}
```
![Selection Sort](images/selection_sort.png)

## Quick Sort
### (sometimes called partition-exchange sort)

![Quick Sort](images/Sorting_quicksort_anim.gif)

```javascript

function swap(items, firstIndex, secondIndex){
    let temp = items[firstIndex];
    items[firstIndex] = items[secondIndex];
    items[secondIndex] = temp;
}

function partition(items, left, right) {
    let pivot = items[Math.floor((right + left) / 2)];
    let i = left;
    let j = right;
    while (i <= j) {
        while (items[i] < pivot) {
            i++;
        }
        while (items[j] > pivot) {
            j--;
        }
        if (i <= j) {
            swap(items, i, j);
            i++;
            j--;
        }
    }
    return i;
}

function quickSort(items, left, right) {
    let index;
    if (items.length > 1) {
        index = partition(items, left, right);
        if (left < index - 1) {
            quickSort(items, left, index - 1);
        }
        if (index < right) {
            quickSort(items, index, right);
        }
    }
    return items;
}


// first call
console.log(quickSort(items, 0, items.length - 1));

```
![Quick Sort Performance](images/quick_sort_performance.png)
