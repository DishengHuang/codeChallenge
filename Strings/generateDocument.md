
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
#create an dict for one input and substract
#the other one to compare
#Time O(m + n)/ Space O(c)
def generateDocument(characters, document):
    char_dict = {}
	for c in characters:
		if c in char_dict.keys():
			char_dict[c] += 1
		else:
			char_dict[c] = 1

	for d in document:
		if d in char_dict.keys():
			char_dict[d] -= 1
			if char_dict[d] < 0:
				return False
		else:
			return False
	return True
```
