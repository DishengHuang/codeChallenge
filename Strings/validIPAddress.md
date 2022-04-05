
# Valid IP Address

You're given a string of length 12 or smaller, containing only
digits. Write a function that returns all the possible IP addresses
that can be created by inserting three .s in the string.

An IP address is a sequence of four positive integers that are 
separated by .s, where each individual integer is within the range
0 - 255, inclusive. 

### Sample Input

```python
{
    string = "1921680"
}
```

### Sample Output

```python
{
    "1.9.216.80",
    "1.92.16.80",
    "1.92.168.0",
    "19.2.16.80",
    "19.2.168.0",
    "19.21.6.80",
    "19.21.68.0",
    "19.216.8.0",
    "192.1.6.80",
    "192.1.68.0",
    "192.16.8.0"
}
```

### Solution
Separate the strings into four parts and check them valid or not

```python
def validIPAddresses(string):
    ipFound = []
	for i in range(1, len(string)):
		currentIPPart = ["","","",""]
		currentIPPart[0] = string[:i]
		if not isValid(currentIPPart[0]):
			continue
		
		for j in range(i + 1, i + min(len(string) - i, 4)):
			currentIPPart[1] = string[i:j]
			if not isValid(currentIPPart[1]):
				continue
				
			for k in range(j + 1, j + min(len(string) - j, 4)):
				currentIPPart[2] = string[j:k]
				currentIPPart[3] = string[k:]
				if isValid(currentIPPart[2]) and isValid(currentIPPart[3]):
					ipFound.append(".".join(currentIPPart))
	return ipFound
			
		
def isValid(string):
	int_str = int(string)
	if int_str > 255:
		return False
	return len(string) == len(str(int_str))
	
```

