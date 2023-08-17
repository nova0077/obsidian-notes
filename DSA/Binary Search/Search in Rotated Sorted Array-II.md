Note: We may have duplicates
We cannot eliminate the half because we cant find the sorted half
Ex: `[3 1 2 3 3 3 3 ]`
In this case here, mid=l=r;
so we here move our l and r pointers closer towards mid

Add 1 case to the [[Search in Rotated Sorted Array - I]] problem
```cpp
if(nums[l]==nums[mid] and nums[mid]==nums[r])
	l++,r--;
```

WorstCase => O(N)