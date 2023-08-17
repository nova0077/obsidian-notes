## Polynomial Rolling Hash

1. two different strings may also have same hash value, but getting this case has very less probability, and this can be minimised by some techniques.
![[Pasted image 20230627222824.png]]

2. It is suitable to keep p a prime number roughly equal to number of components.
   i.e, p = 31 for 26 chars
	     p = 53 for both lower and uppercases
3. **'m'** should be as large as possible, because the probability of collision is 1/m
4. Sometimes m = 2^64 is chosen as the integer overflows and work as modulus. But in practise we take m as 1e9+7 or 1e9+9 which is also a prime
5. while calculating hash value, we represent chars as numbers, so it is better to start with 1 rather than 0 (a=1, b=2 ..... z=26).
```cpp
long long compute_hash(stirng const& s){
	const int p = 31;
	const int m = 1e9+9;
	long long hash_val = 0;
	long long p_pow = 1;
	for(auto i:s)
	{
		hash_val = (hash_val + (i-'a'+1)*p_pow) % m;
		p_pow = (p_pow*p) % m;
	}
	return hash_val
}
```


### To find the hash value of a substring
![[Pasted image 20230627224457.png]]

1. We can perform the hash of a substring by knowing its prefix hash value, which can be done in O(1), by storing the prefix hash values and the [[modular inverse]] values for powers of i.
2. there is an easy way,
   - no need to calculate hash value of exact substring,
   - instead you can multiply by some power of p.
   - to achieve same power of p at last, we do this multiplication.
3. Ex: abc, def are 2 substrings of a string
   - then, hash value of `abc = a*p^2 + b*p^3 + c*p^4`
   - the hash value of `def =  d*p^5 + e*p^6 + f*p^7`
   - now to compare the hash values, we multiply the hash value of string abc with the p^3 (5-2 = 3)
   - because it starts with the small power of p value.

### Improve no-collision probability
1. the probability will be 1/m for 2 strings to get same hash value
2. what if we compare a single string with 1e6 other strings, the probability will now be 1e-3 (for m=1e9+9)
3. what if we compare 1e6 different strings with each other ?
   the probability will become 1
**Note:**
To avoid this collisions, we can compute 2 different hashes for each string with different p or m, and compare these pairs

Problems:
1. [[Count Unique Substrings]]