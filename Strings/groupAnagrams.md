
# Group Anagrams
Write a function that takes in an array of strings and groups anagrams together.
Anagrams are strings made up of exactly the same letters, where order doesn't matter.
For example,"cinema" and "iceman" are anagrams; similarly, "foo" and "ofo" are 
anagrams.
Your function should return a list of anagram groups in no particular order.


### Sample Input

```python
words = ["yo","act","flop","tac","foo","cat","oy","olfp"]
```
### Sample Output
```python
[["yo","oy"],["flop","olfp"],["act","tac","cat"],["foo"]]
```
### Solution and Thoughts
Sort the strings and bucket them. Most optimal solutions are using the hash
table.

```python
#Time O( w * n * log(n)) and Space O(w*n) 
def groupAnagrams(words):
    result = {}
	for w in words:
		res = "".join(sorted(w))
		if res in result:
			result[res].append(w)
		else:
			result[res] = [w]
	return list(result.values())
```
### Solution 2
Without using the hash table. 
```python
#Time O( w * n * log(n)) and Space O(w*n) 
def groupAnagrams(words):
	if len(words) == 0:
		return []
	# sort the words
    sortedWords = ["".join(sorted(w)) for w in words]
    # create the initial index of the words
	index = [i for i in range(len(words))]
	# sort by alphabetical order
	index.sort(key = lambda x: sortedWords[x])
	
	result = []
	currentAnagrams = sortedWords[index[0]]
	currentAnagramsArray = []
	for i in range(len(sortedWords)):
		if sortedWords[index[i]] == currentAnagrams:
			currentAnagramsArray.append(words[index[i]])
		else:
			result.append(currentAnagramsArray)
			currentAnagrams = sortedWords[index[i]]
			currentAnagramsArray = [words[index[i]]]
	result.append(currentAnagramsArray)
	return result
```