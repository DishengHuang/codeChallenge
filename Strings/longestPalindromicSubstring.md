
# Longest Palindromic Substring

Write a function that, given a string, returns its longest palindromic
substring. 
A palindrome is defined as a string that's written the same forward
and backward. Note that single-character strings are palindromes. You can
assume that there will only be one longest palindromic substring.

### Sample Input

```python
string = "abaxyzzyxf"
```
### Sample Output
```python
"xyzzyx"
```
### Solution and Thoughts
Here are some thoughts about the solution. We may need to define a
helper function to check whether the substring is palindromic or not.
And then to check whether the substring we found is the longest or not.

```python
#Time O(N^2) and Space O(N)
def longestPalindromicSubstring(string):
    currentLongestString = [0,1]
    # 0 is not necessary
	for i in range(1,len(string)):
		odds = getPalindromicFrom(string, i-1, i+1)
		even = getPalindromicFrom(string, i-1, i)
		currentLongestString = max(odds, even, currentLongestString, key = lambda x: x[1] - x[0])
	return string[currentLongestString[0]:currentLongestString[1]]

def getPalindromicFrom(string, leftIdx, rightIdx):
	while leftIdx >= 0 and rightIdx < len(string):
		if string[leftIdx] != string[rightIdx]:
			break
		leftIdx -= 1
		rightIdx += 1
	return [leftIdx + 1, rightIdx]
```