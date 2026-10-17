# Skip List Analysis

## 1. Structure
Explain the sentinel node and how forward pointers at multiple levels represent the skip list.
The sentinel is a head node containing pointers for all supported levels. It is a dummy node (doesn't hold real key) and each node keeps array of pointers for all the upper levels, one node / level represented in, the fact that some elements from lower levels are not brought up to higher levels allows traversal to "skip" values. "because some nodes appear on higher levels, searches can jump past lots of nodes". The nodes contain forward pointers for each level that they participate in (including 0).

## 2. Search
Explain the top-down search procedure and why it can skip many nodes.
Start at the head, while the target node is greater than the next node, keep moving forward, once the next node is greater than the key then you can move down the list and keep searching level by level and repeat, all the way until the level is 0. You can skip nodes because the higher levels only have a subset of the full linked list at level 0 so therefore you don't have to search through as many elements as you would if you search through level 0.

## 3. Randomization
Explain how the probability parameter affects node heights and the expected number of nodes at each level.
Given a certain probability p between 0 and 1, not inclusive of either, the probability will decide when a node gets promoted to the next level. Promotions are independent per level, so if you get promoted one node, it doesn't affect any other nodes. This results in a halving effect when p = 0.5. For example, with 100 elements, we expect 100 nodes at level 0, 50 at level 1, 25 at level 2, etc. Node heights are also decied by repeated promotion trials until a promotion fails or the maximum level is reached.

## 4. Complexity
Give expected and worst-case time complexity for search, insertion, deletion, and traversal. Explain why the worst case remains linear.
Search: Expected time complexity is O(log n) because assuming p = 0.5, the number of nodes are halved each level. The worst-case remains linear O(n) because if the promotions are not favorable (ie none were promoted), it would still be a linear search to find the element from level 0.
Insertion: Expected time complexity is O(log n) because there is first a search for the target key, and then the forward pointers are all updated accordingly. The worst-case remains linear O(n) because using the scenario described above, if the element to be inserted was at the end, it would still require linear traversal.
Deletion: Similar to insertion, the expected time complexity is O(log n) because there is a search for the target key, and then the previous pointers are updated to point to the next element instead. The worst-case remains linear O(n) because using the scenario described above, if the element to be deleted was at the end, it would still require linear traversal.
Traversal is O(n) for both expected and worst case as it visits all n nodes at level 0. Therefore, the randomized levels do not affect the time complexity.

## 5. Comparison
Compare a skip list with a balanced binary search tree in terms of expected performance, worst-case guarantees, memory overhead, implementation complexity, and practical use.

For the expected case, skip lists and BBST will both expect O(log n) time complexity. In the worst case, skip list becomes O(n) whereas BBST is still O(log n). In terms of space complexity, both data structures take O(n) total space. However, their memory overhead still differs. BBSTs usually contain two child pointers per node, and skip lists stores multiple forward pointers based on the highest level of each node.
BST can guarantee O(log n) for the search, insert, delete functions at the cost of a more complex implementation, whereas skip lists are easy to implement but may include a O(n) search if all values are promoted, creating multiple lists.
In terms of practical use, BBSTs can be useful when worst-case performance is important (such as for maps and sets), while skip lists offer simultaneous operations. For example, within servers, skip lists can perform concurrent operations and save the balancing rules used in BBSTs.

