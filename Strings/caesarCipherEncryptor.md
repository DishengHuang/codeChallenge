
# Caesar Cipher Encryptor

Given a non-empty string of lowercase letters and non-negative integer
representing a key, write a function that returns a new string obtained
by shifting every letter in the input string by k positions in 
the alphabet, where k is the key.
Note that letters should "wrap" around the alphabet; in other words, the
letter z shifted by one returns the letter a.  


## Sample Input

```python
string = "xyz"
key = 2
```

## Sample Output

```python
"zab"
```

## Solution 1 (With ASII Code)

```python
def caesarCipherEncryptor(string, key):
	newLetters = []
    # what if the key is greater than 26?
	newKey = key % 26
	for l in string:
		newLetters.append(getLetter(l,newKey))
	return "".join(newLetters)

def getLetter(letter, key):
	newCode = ord(letter) + key
	return chr(newCode) if newCode <= 122 else chr(96 + newCode % 122)
```

## Solution 2 (Without ASII Code)

```python
def caesarCipherEncryptor(string, key):
    newLetters = []
    newKey = key % 26
    alphabet = list("abcdefghijklmnopqrstuvwxyz")
    for l in string:
        newLetters.append(getLetters(l, newKey, alphabet))
    return "".join(newLetters)

def getLetters(letter, key, array):
    newCode = array.index(letter) + key
    return array[newCode] if newCode < 26 else array[newCode % 26]

```