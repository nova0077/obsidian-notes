Take 3 extra pointers, prev, nxt and curr.
curr represents the current value,
prev represents the previous value,
nxt represents the next node of curr

Our basic idea is just changing the links or pointers or next reference between nodes.
ex: 1 -> 2 -> 3-> 4
after reversal, it looks like 1 <- 2 <- 3 <- 4

and we return our last node reference as head of reversed linkedlist which will be prev here as current will be NULL.

```cpp
ListNode* prev = NULL;
ListNode* curr = head;
ListNode* nxt = NULL;
while(curr != NULL)
{
	nxt = curr->next;
	curr->next = prev;
	prev = curr;
	curr = nxt;
}
```

Explanation:
1. We first keep a track of next node after curr
2. we point our cur->next to prev (reversing step)
3. we maintain our prev and curr pointers for next reversal operation.
