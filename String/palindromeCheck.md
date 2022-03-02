
# Palindrome Check

Write a function that takes in a non-empty string and that returns a boolean
representing whether the string is a palindrome. A palindrome is defined
as a string that's written the same forward and backward. Note that single-character
strings are palindromes.


## Sample Input

```python
string = "abcdcba"
```
## Sample Output

```python
true // it's written the same forward and backward
```
## Solution 1
Create the array to store the reverse string and 
compare the reverse string with the original string
```python
# Time O(n)/ Space O(n)
def isPalindrome(string):
    reversedString = []
	for i in reversed(range(len(string))):
		reversedString.append(string[i])
	return string == "".join(reversedString)
```
## Solution 2
Recursive call
```python
# Time O(n)/ Space O(n)
def isPalindrome(string, i = 0):
	j = len(string) - 1 - i
	if i >= j:
		return True
	if string[i] != string[j]:
		return False
	return isPalindrome(string, i + 1)
```
## Solution 3
Optimal Solution
```python
# Time O(n)/ Space O(1)
def isPalindrome(string):
    leftIdx = 0
	rightIdx = len(string) - 1
	while leftIdx < rightIdx:
		if string[leftIdx] != string[rightIdx]:
			return False
		leftIdx += 1
		rightIdx -= 1
	return True
```