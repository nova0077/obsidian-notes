Step-1: Identify the sorted half, (left or right)
Step-2: Check in the sorted half, and if target is present move your pointers normally as binary search algorithm
Step-3: If it is not present in the sorted array, eliminate it and move to the other half.
```cpp
int search(vector<int>& nums, int target) {
	int l=0;
	int r=nums.size()-1;
	while(l<=r)
	{
		int mid = r-(r-l)/2;
		if(nums[mid] == target)
			return mid;
		// if left half is sorted
		else if(nums[l]<=nums[mid])
		{
			if(nums[l]<=target and target<=nums[mid])
				r = mid-1;
			else
				l = mid+1;
		}
		// right sorted half
		else
		{
			if(nums[mid]<=target and nums[r]>=target)
				l=mid+1;
			else
				r=mid-1;
		}
	}
	return -1;
}
```