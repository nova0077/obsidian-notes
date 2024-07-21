Problem Statement: Find the largest sequence which follows one of the below conditions
1. x1 < x2 > x3 < x4 > x5 ....
2. x1 > x2 < x3 > x4 < x5 ....

Approach:
1. Maintain two counters (`inc` and `dec`) representing the lengths of the increasing and decreasing sequences ending at the current element.
2. For each element, update the counters based on whether it contributes to an increasing or decreasing sequence. 
3. The final result is the maximum of the two counters, representing the longest alternating sequence.

```cpp
int alternativeMaxLength(vector<int>& arr){
	int inc=1, dec=1;
	for(int i=1;i<n;i++)
	{
		if(arr[i]>arr[i-1])
			inc = dec+1;
		if(arr[i]<arr[i-1])
			dec = inc+1;
	}
	return max(inc, dec);
}
```
