Leetcode [1717. Maximum Score From Removing Substrings](https://leetcode.com/problems/maximum-score-from-removing-substrings/)
Approach:
1. First process either "ab"/ "ba" entire the string. (which gives you more points)
2. How will you process this in O(N) TC (using stack), But in O(1) SC ?

To solve these kind of problems in O(1) auxiliary space & O(N) time complexity, 
1. We can maintain 2 pointers, read pointer & write pointer
2. Instead of removing the substring from the string we can simply copy the next character after the substring in the place of substring (over-writing) & at last we can erase the left over string.
3. Ex: "f a b c", 
   when "ab" is found, instead of removing it we will copy 'c' in the place of 'a',
   so our string becomes "f c b c", 
   we can remove the left over string "b c", so the string after removal of "ab" is "fc".

Implementation details
``` cpp
int func(string& s,string t, int x)
{
	int r=0, cnt=0;
	for(int l=0;l<s.size();l++)
	{
		s[r++] = s[l];
		if(r > 1 && s[r-2]==t[0] && s[r-1]==t[1])
		{
			r -= 2;
			cnt += x;
		}
	}
	s.erase(s.begin()+r, s.end());
	return cnt;
}
```

