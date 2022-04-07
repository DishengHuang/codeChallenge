
# Reserve Words In String

Write a function that takes in a string of words separated by
one or more whitespaces and returns a string that has
these words in reverse order. For example, given the string
"tim is great" , your function should return "great is tim".



## Sample Input

```python
string = "AlgoExpert is the best!"
```

## Sample Output

```python
"best! the is AlgoExpert"
```

## Solution 1
Split the word and space by the space. And then reverse
the order of the word list.

```python
# Time O(n)/ Space O(n) - where n is the length of the string
def reverseWordsInString(string):
    words = []
	startOfWord = 0
	for idx in range(len(string)):
        # if current character is space
        # then we add the word
		if string[idx] == " ":
			words.append(string[startOfWord:idx])
			startOfWord = idx
        # if the current start is space
        # then we add the space
		elif string[startOfWord] == " ":
			words.append(" ")
			startOfWord = idx
    # add the last word into the word list,
    # since we cannot triggle the condition that
    # current character is space
	words.append(string[startOfWord:])
    # reverse the word list
	reverseList(words)
	return "".join(words)

def reverseList(List):
	start , end = 0, len(List) - 1
	while start < end:
		List[start], List[end] = List[end], List[start]
		start += 1
		end -= 1
```

## Solution 2
Split the string and reverse all the character. And then reverse
back the word character.

```python
# Time O(n)/ Space O(n) - where n is the length of the string
def reverseWordsInString(string):
    #convert the string into the character list
	character_list = [char for char in string]
	#reverse all of them first
	reverseList(character_list, 0, len(character_list) - 1)
	#select the words and reverse them again
	startOfWord = 0
	while True:
		endOfWord = startOfWord
		#find the words
		while endOfWord < len(character_list) and character_list[endOfWord] != " ":
			endOfWord += 1
		#find the ending case for the while loop
		if endOfWord == len(character_list):
			#reverse the last word in the character list
			reverseList(character_list, startOfWord, endOfWord - 1)
			break

		reverseList(character_list, startOfWord, endOfWord - 1)
		startOfWord = endOfWord + 1

	return "".join(character_list)

def reverseList(List, start, end):
	while start < end:
		List[start], List[end] = List[end], List[start]
		start += 1
		end -= 1
```
