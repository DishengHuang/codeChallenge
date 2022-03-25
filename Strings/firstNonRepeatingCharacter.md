
# First Non-Repeating Character

Write a function that takes in a string of lowercase English-alphabet
letters and returns the index of the string's first non-Repeating character.
The first non-repeating character is the first character in a string that occurs
only once. if the input string doesn't have any non-repeating character, your 
function should return -1
### Sample Input

```python
string = "abcdcaf"
```

### Sample Output

```python
1 // The first non-repeating character is "b" and is found at index 1.
```

### Solution 1 (Brute Force Search)

```python
# Time O(n^2) and Space O(1)
def firstNonRepeatingCharacter(string):
    for i in range(len(string)):
		depulicate = False
		for j in range(len(string)):
			if i != j and string[i] == string[j]:
				depulicate = True
		if not depulicate:
			return i
	return -1
```

### Solution 2

```python
# Time O(n) and Space O(1)
def firstNonRepeatingCharacter(string):
    #count the character frequency
	char_freq = {}
	for s in string:
		char_freq[s] = char_freq.get(s,0) + 1

	#check the count of the string
	for idx in range(len(string)):
		if char_freq[string[idx]] == 1:
			return idx
	return -1
```


