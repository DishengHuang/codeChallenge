
# Minimum Characters For Words

Write a function that takes in an array of words and returns the
smallest array of characters needed to form all of words. The characters
don't need to be in any particular order.

### Sample Input

```python
words = ["this", "that", "did", "deed", "them!", "a"]
```

### Sample Output

```python
["t","t","h","i","s","a","d","d","e","e","m","!"]
```

### Solution 1
We will first count the number of frequency of each character in 
each word. Then, compare those frequency with the main hash table and
update the hash table. Either add the new key or update the max number 
of the frequency. Lastly, convert the hash table into the string
list
```python
# Time O(l * n) / Space O(C)
def minimumCharactersForWords(words):
    max_freq = {}
	for word in words:
		word_freq = countWordFreq(word)
		updateMaxFreq(word_freq, max_freq)
	return convertMaxFreq(max_freq)

		
def countWordFreq(string):
	char_dict = {}
	for char in string:
		if char not in char_dict:
			char_dict[char] = 0
		char_dict[char] += 1
	return char_dict

def updateMaxFreq(currentFreq, max_Freq):
	for char in currentFreq:
		if char not in max_Freq or currentFreq[char] > max_Freq[char]:
			max_Freq[char] = currentFreq[char]
			
def convertMaxFreq(max_Freq):
	char_list = []
	for k in max_Freq:
		for _ in range(max_Freq[k]):
			char_list.append(k)
	return char_list
```

