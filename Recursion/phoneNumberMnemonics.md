
# Phone Number Mnemonics


### Sample Input
```python
phoneNumber = "1905"
```
### Sample Output
```python
[
    "1w0j",
    "1w0k",
    "1w0l",
    "1x0j",
    "1x0k",
    "1x0l",
    "1y0j",
    "1y0k",
    "1y0l",
    "1z0j",
    "1z0k",
    "1z0l",
]
```

```python
def phoneNumberMnemonics(phoneNumber):
	mnemonicsFound = []
	currentMnemonics = ["0"] * len(phoneNumber)
	
	phoneNumberMnemonicsHelper(0, phoneNumber, currentMnemonics, mnemonicsFound)
	
	return mnemonicsFound

def phoneNumberMnemonicsHelper(idx, phoneNumber, currentMnemonics, mnemonicsFound):
	if idx == len(phoneNumber):
		mnemonic = "".join(currentMnemonics)
		mnemonicsFound.append(mnemonic)
	else:
		digit = phoneNumber[idx]
		letters = DIGIT_LETTERS[digit]
		for letter in letters:
			currentMnemonics[idx] = letter
			phoneNumberMnemonicsHelper(idx + 1, phoneNumber, currentMnemonics, mnemonicsFound)

DIGIT_LETTERS = {
	"0": ["0"],
	"1": ["1"],
	"2": ["a","b","c"],
	"3": ["d","e","f"],
	"4": ["g","h","i"],
	"5": ["j","k","l"],
	"6": ["m","n","o"],
	"7": ["p","q","r","s"],
	"8": ["t","u","v"],
	"9": ["w","x","y","z"],
}
```

