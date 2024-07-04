# QnA

## Compare a dictionary and array type data structure.

||Dictionary|Array|
|---|---|---|
|Definition|A collection of key-value pairs|A collection of elements|
|Requisite|Each key should be unique|Element should be identified by index|
|Access time complexity|O(1)|O(1)|
|Insertion time complexity|O(1)|O(n)|
|Deletion time complexity|O(1)|O(n)|
|Order|Elements are usually unordered, there are some exceptions like Python 3.7+|Ordered|
|Usage|Mapping with unique key|Ordered elements|

Dictionary makes sense when one need to access some data based on unique key. It make senese as the insertion, deletion
and access all have time complexity of O(1). Arrays makes sense when one needs to access data based on index and order is
important.
