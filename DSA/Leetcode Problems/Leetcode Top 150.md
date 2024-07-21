#### 1. Next Permutation
Brute Approach => Generate all permutations and check the next 
`Time complexity => O(2^n)`
Optimal Approach => O(1)
**Note:** iterate from back

##### Intuition
1. In a permutation it is always observed that, it forms a peak, a set of increasing elements and then a set of decreasing elements.
2. to get the next permutation we need to modify the peak with the just greater element right to it.
3. after this we can just swap these elements and make the numbers after the 1st pivot in increasing order.
4. Ex: [ 1, 3 , 5, 4, 2]  => ind1 = 3, ind2 = 4,
	the next permutation is [ 1, 4, 5, 3, 2]
	
```cpp
void nextPermutation(vector<int> &nums){
	int n = nums.size();
	int i = n-1, j;
	for(i=n-2; i>=0; i--){
		if(nums[i] < nums[i+1]) // ind1
			break;
	}
	if(i<0){
		reverse(nums.begin(),nums.end());
		return;
	}
	for(j=n-1; j>i; j--){
		if(nums[j] > nums[i])
			break;
	}
	swap(nums[i], nums[j]);
	reverse(nums.begin()+i+1, nums.end());
}
```








#### 2. Maximum Subarray Sum
##### [[Kadane's Algorithm]]
1. Traverse in the array and include the curr value to the sum
2. if sum < 0 update the sum to 0
3. in every step after adding check for maximum ans with ans and sum

```cpp
int maxSubArray(vector<itn>& nums){
	int sum=0;
	int ans = INT_MIN;
	for(auto i:nums)
	{
		sum += i;
		ans = max(ans,sum);
		sum = max(sum, 0);
	}
	return sum
}
```


#### 3. Maximum Product Subarray
**Approach 1: (double iteration)**
1. check for whether 0 is present in the array or not, if it is present the ans will be `max(ans,0)`
2. iterate from left and take the max value of the left product, handle when 0 occurrs, set it to 1
3. similarly traverse from back and take the suffix max
4. ans will be the max of pref max and suff max and. 0(if 0 is present)
```cpp
int maxProductSubArray(vector<int>& nums) {
	int maxLeft = nums[0];
	int maxRight = nums[0];
	int prod = 1;
	bool zeroPresent =  false;
	for(auto i: nums) {
		prod *= i;
		if(i == 0) {
			zeroPresent = true;
			prod = 1;
			continue;
		}
		maxLeft = max(maxLeft, prod);
	}
	prod = 1;
	
	for(int j=nums.size()-1; j>=0; j--) {
		prod *= nums[j];
		if(nums[j] == 0) {
			zeroPresent = true;
			prod = 1;
			continue;
		}
		maxRight = max(maxRight,prod);
	}
	if(zeroPresent) 
		return max(max(maxLeft,maxRight),0);
	return max(maxLeft,maxRight);
}
```

**Approach 2: (single iteration)**
1. maintain 2 variables the max ans till now and the min ans till now
2. in each iteration multiply the variable with the cur value and update them
3. Take ans as the max of ans and the max till now.

```cpp
int maxProduct(vector<int>& nums) {
	int pr1 = nums[0], pr2 = nums[0];
	int ans = nums[0];
	for(int i=1;i<nums.size();i++)
	{
		int temp = max(nums[i], pr1*nums[i], pr2*nums[i]);
		pr2 = min(nums[i], pr1*nums[i], pr2*nums[i]);
		pr1 = temp;
		ans = max(ans, pr1);
	}
	return ans;
}
```

#### 4. Sort Array of 0, 1 and 2's
##### [[DUTCH NATIONAL FLAG PROBLEM]]
Approach:
1. Maintain 2 pointer L and R, such that
2. the values from 0 to L contains 0's
   the values from L to R contains 1's
   the values from R to n contains 2's

```cpp
void sortColors(vector<int>& nums){
	int l=0,r=nums.size()-1;
	for(int i=0; i<=r; i++){
		if(nums[i]==0) {
		   swap(nums[i], nums[l]);
		   l++;
		}
		else if(nums[i]==2) {
		   swap(nums[i], nums[r]);
		   r--;
		   i--;
		}
	}
}
```
#### 5. Find the Duplicate Number
Naive Approach: (Sorting)
Time complexity => O(nlogn)
1. Sort the array and check for the adjacent element to find duplicate

Better Approach: (Hashing)
Time complexity => O(N), Space => O(N)
1. Create a hash array of size n, as the elements are in the range of 1 to n,
2. Traverse in the array and mark visited for the position in the hash array for the current element.
3. if a pos is already marked visited, then it is the repeated number.
![[Pasted image 20230627002827.png]]
 ##### [[LINKED LIST CYCLE METHOD]]
Approach: 
1. Assume indexes are mapped with values of the array, 
2. Start iterating from the 0th index value and go to the position of `arr[0]` and so, on
3. A cycle gets formed if there is a duplicate number
4. To find this duplicate number we use [[Tortoise method]] using slow and fast pointers.
5. ![[Pasted image 20230627003514.png]]
```cpp
int findDuplicate(vector<int>& nums) {
	int slow = nums[0];
	int fast = nums[0];
	do{
		slow = nums[slow];
		fast = nums[nums[fast]];
	}while(slow != fast);
	fast = nums[0];
	while(slow != fast){
		fast = nums[fast];
		slow = nums[slow];
	}
	return slow;
}
```
