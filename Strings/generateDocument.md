
# Generate Document

You're given a string of available characters and a string representing
a document that you need to generate. Write a function that
determines if you can generate the document using the available
characters. If you can generate the document, your function should
return true; otherwise, it should return false.




### Sample Input
```python
characters = "abcabc"
document = "aabbccc"
```

### Sample Output
```python
False
```
### My Solution/Thoughts
```python
#create an dict for one input and subtract
#the other one to compare
#Time O(m + n)/ Space O(c)
def generateDocument(characters, document):
    char_dict = {}

	for c in characters:
		if c not in char_dict:
			char_dict[c] = 0

		char_dict[c] += 1

	for d in document:
		if d not in char_dict or char_dict[d] == 0:
			return False

		char_dict[d] -= 1

	return True
```

### Solution 2
```python
#Compare two inputs and check whether there are
#enough characters to write the documents
#Time O(m * (m + n)) / Space O(1)
def generateDocument(characters, document):
	for char in document:
		characterFreq = countChar(char,characters)
		documentFreq = countChar(char,document)
		if documentFreq > characterFreq:
			return False

	return True

def countChar(char,target):
	freq = 0
	for character in target:
		if character == char:
			freq +=1

	return freq
```
### Solution 3
```python
#Compare two inputs and check whether there are
#enough characters to write the documents
#Time O(c*(m + n)) / Space O(c)
def generateDocument(characters, document):
    checked = set()
	for char in document:
		if char in checked:
			continue
		characterFreq = countChar(char,characters)
		documentFreq = countChar(char,document)
		if documentFreq > characterFreq:
			return False
	return True

def countChar(character,target):
	frequency = 0
	for char in target:
		if char == character:
			frequency += 1
	return frequency
```
