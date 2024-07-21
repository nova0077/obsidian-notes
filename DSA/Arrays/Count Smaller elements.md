Problem: For each element `arr[i]` in `arr` return the number of elements smaller than `arr[i]` to its right.

Code:
```cpp
vector<int> countSmaller(vector<int>& nums) {
	int n=nums.size();
	vector<int>v = nums;
	vector<int>ans;
	sort(v.begin(),v.end());
	for(int i=0;i<n;i++)
	{
		int x = lower_bound(v.begin(),v.end(),nums[i])-v.begin();
		ans.push_back(x);
		v.erase(v.begin()+x);
	}
	return ans;
}
```
Time Complexity: Actual  O(nlogn), Expected O(n^2)

### Using Merge Sort
counting no. of inversions

```cpp
void merge(int l, int mid, int r, vector<pair<int,int>>& vp, vector<int>& cnt){
	int i=l, j=mid+1, k=0;
	vector<pair<int,int>>tmp(r-l+1);
	while(i<=mid && j<=r)
	{
		if(vp[i].first <= vp[j].first)
			tmp[k++] = vp[j++];
		else
		{
			cnt[vp[i].second] += r-j+1;
			tmp[k++] = vp[i++];
		}
	}
	while(i<=mid)
		tmp[k++] = vp[i++];
	while(j<=r)
		tmp[k++] = vp[j++];
	for(i=l;i<=r;i++)
		vp[i] = tmp[i-l];
}
void mergeSort(int l, int r, vector<pair<int,int>>& vp, vector<int>& cnt){
	if(l>=r)
		return;
	int mid = (l+r)/2;
	mergeSort(l,mid,vp,cnt);
	mergeSort(mid+1,r,vp,cnt);
	merge(l,mid,r,vp,cnt);
}
vector<int> countSmaller(vector<int>& nums) {
	int n=nums.size();
	vector<pair<int,int>>vp;
	vector<int>cnt(n,0);
	for(int i=0;i<n;i++)
		vp.push_back({nums[i],i});
	mergeSort(0,n-1,vp,cnt);
	return cnt;
}
```
TC: O(nlogn)

### Using Fenwick Tree
1. Array Compression
2. Iterate from back side & mark them as visited to get prefix
```cpp
vector<int>bit;
void update(int i, int p)
{
	for(;i<1000001;i+=(i&-i))
		bit[i] += p;
}
int get(int i)
{
	int ans=0;
	for(;i>0;i-=(i&-i))
		ans+=bit[i];
	return ans;
}
vector<int> constructLowerArray(vector<int> &arr) {
	// code here
	int n = arr.size();
	vector<pair<int,int>>vp;
	for(int i=0;i<n;i++)
		vp.push_back({arr[i],i});
	sort(vp.begin(),vp.end());
	int ind=1;
	unordered_map<int,int>mp;
	for(int i=0;i<n;i++)
	{
		if(mp.find(vp[i].first) == mp.end())
			mp[vp[i].first]=ind++;
	}
	for(int i=0;i<n;i++)
		arr[i] = mp[arr[i]];
	bit = vector<int>(1000001,0);
	vector<int>ans(n);
	for(int i=n-1;i>=0;i--)
	{
		ans[i] = get(arr[i]-1);
		update(arr[i],1);
	}
	return ans;
}
```
