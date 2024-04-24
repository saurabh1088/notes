# Binary Search

## Definition
Binary search is an algorithm which can be defined as searching for a specific element in a sorted array or list by
repeatedly dividing the search interval into half.

## Pre-conditions
Array on which search is to be performed SHOULD BE sorted.

## What makes it efficient?
At every step, in binary search half of the elements in array are eliminated. So if one has a large dataset which is sorted
then instead of linear search, binary search will be more efficient.

## Complexity
O(Log n)
As discussed above, binary search algorith is efficient. So if the size of the data set gets increased, the time taken by
algorithm will grow logarithmically.
A logarithmical time complexity means that even if the input size increases significantly, the time taken by the
algorithm increases at a much slower rate.
