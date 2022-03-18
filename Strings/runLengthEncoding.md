
# Run-Length Encoding

Write a function that takes in a non-empty string and returns its
run-length encoding. 


### Sample Input
```python
string = "AAAAAAAAAAABBCCCCDD"
```
### Sample Output
```python
9A4A2B4C2D
```
The reason why we need to encode 13A to 9A4A is that we 9 is the maximum single
number we could use and if we have one 3 as an input, it may messy up the algorithm.  

### Solution 1
```python
### Time O(n) and Space O(n)
def runLengthEncoding(string):
    char_list = []
	currentLength = 1
	
	for index in range(1,len(string)):
		if string[index] != string[index - 1] or currentLength == 9:
			char_list.append(str(currentLength))
			char_list.append(string[index - 1])
			currentLength = 0
		currentLength += 1
	
	char_list.append(str(currentLength))
	char_list.append(string[len(string) - 1])
	
	return "".join(char_list)
```
