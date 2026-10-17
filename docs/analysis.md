# Skip List Analysis

## 1. Structure
Explain the sentinel node and how forward pointers at multiple levels represent the skip list.
sentinel is dummy, doesn't hold real key, each node keeps array of pointers for all the upper levels, one node / level represented in, the fact that some elements from lower levels are not brought up to higher levels allows traversal to "skip" values. "because some nodes appear on higher levels, searches can jump past lots of nodes"

## 2. Search
Explain the top-down search procedure and why it can skip many nodes.
Start at the head, while the node/key you're searching for is less than the next, keep moving forward, once the next node is greater than the key then you can move down the list and keep traversing level by level and repeat, all the way until the level is 0. 
you can skip nodes because the higher levels only have a subset of the full linked list at level 0 so therefore you don't have to traverse through as many elements as you would if you traverse through level 0.

## 3. Randomization
Explain how the probability parameter affects node heights and the expected number of nodes at each level.
Given a certain probability p between 0 and 1, not inclusive of either, the probability will decide when a node gets promoted to the next level. Promotions are independent per level, (if you get promoted one node it doesn't affect the other node), results in halving effect.

## 4. Complexity
Give expected and worst-case time complexity for search, insertion, deletion, and traversal. Explain why the worst case remains linear.
Traversal is O(n), worst case is because 
Search: Since the function, in the worst case, traverses through the whole level, the time complexity would be O(n). Being multiplied by the total number of levels, the more accurate time complexity would be O(levels*n), but because we ignore constants when talking about time complexity, the overall is still O(n).

## 5. Comparison
Compare a skip list with a balanced binary search tree in terms of expected performance, worst-case guarantees, memory overhead, implementation complexity, and practical use.
Expected: Skip lists and BBST will both expect O(log n), worst case skip list O(n), BBST O(log n)
BBST: O(n) total space, skip list O(n) total space
BST are for guaranteed worst-case search for the tradeoff of more nuanced code, whereas skip lists are easy to implement but may include a O(n) search if all values are promoted, creating multiple lists.
Practical USE:
skip lists for simple and fast
balanced bst for edge cases bad and worst-case guarantee
