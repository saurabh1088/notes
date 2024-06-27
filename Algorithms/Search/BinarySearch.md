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

## What about linked list, can binary search be used for linked lists?
Binary search doesn't make sense for a linked list as it turns out to be highly inefficient if used. Following are the reasons
of inefficiency on a linked list:

- Binary search performs best on arrays stored in contiguous memory. Linked lists however have nodes which have references
to the next element, all the elements in a linked list may not be in a contiguos memory block. What this limitation lead to
is that random access to any element in a linked list means there is no escape from traversing the whole linked list. An
important aspect of a binary search algorith is to access the middle element of the array. For a linked list one would need
to traverse the whole list making each operation of finding the middle element having a linear time complexity.

For this limitation, when it comes to linked list, linear search is used.