#LEETCODE_92

Reverse a Sublist from left position to right position in a lInkedList
Ex: 4 -> 8-> 15-> 16-> 23 -> 42 -> NULL  , left = 3, right = 5
sol: 4-> 8-> 23-> 16-> 15 -> 42 -> NULL

Approach:
1. We reverse the sublist same as a LinkedList reversal.
2. We maintain the pointer of left prev node, so that after reversal we can mark its next as the right node.

![[Pasted image 20230908025633.png]]