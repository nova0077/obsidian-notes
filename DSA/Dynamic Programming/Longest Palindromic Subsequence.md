**Problem Statement**: Find the longest palindromic subsequence from a given string.

**Dp State**: `dp[i][j] => length of longest palindromic subsequence of s[i....j]`.

**Transition**: 
1. if `i == j` return 1
2. if `s[i] == s[j`] 
	if `i+1 == j`
		return 2
	else
		return `2+dp[i+1][j-1]`
3. else
	return `max of dp[i+1][j] and dp[i][j-1]`

```cpp
class Solution {
public:
	vector<vector<int>>dp;
	int func(int i, int j, string &s){
		if(i==j)
			return 1;
		if(dp[i][j] != -1)
			return dp[i][j];
		if(s[i]==s[j])
		{
			if(i+1 == j)
				return dp[i][j]=2;
			else
				return dp[i][j]=2+func(i+1,j-1,s);
		}
		else
			return dp[i][j]=max(func(i+1,j,s), func(i,j-1,s));
	}
	int longestPalindromeSubseq(string s) {
		int n=s.length();
		dp = vector<vector<int>>(n+1, vector<int>(n+1,-1));
		return func(0,n-1,s);
	}
};
```

**Time Complexity:** O(N^2)