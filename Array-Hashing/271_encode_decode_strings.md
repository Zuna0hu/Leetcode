# Leetcode 271: Encode and Decode Strings

## Link
[Leetcode](https://leetcode.com/problems/encode-and-decode-strings/) (needs subscription)
[Linkcode](https://www.lintcode.com/problem/659/) (free)

# Problem
Design an algorithm to encode a list of strings to a string. The encoded string is then sent over the network and is decoded back to the original list of strings.

## Idea

### Idea 1: Use # to separate

#### Example Implementation:
- **Original List**: `["feet", "code"]`  
- **Encoded String**: `"feet#code"`  
- **Decoded Strings**: `"feet", "code"`

#### Issue:
This approach fails in cases where a string in the list contains the separator itself.

For example:  
- **Original List**: `["feet#code"]`  
- **Encoded String**: `"feet#code"`  
- **Decoded Strings**: `"feet", "code"` (Incorrect)  

The decoding process produces incorrect results because it cannot differentiate between the separator used for encoding and actual content in the original strings.

### Idea 2: Use Array of String Lengths

#### Example Implementation:
- **Original List**: `["feet", "code", "feet#code", "feet###code"]`  
- **Encoded String**: `"feetcodefeet#codefeet###code"`
- **Array**: [4, 4, 9, 11]  
- **Decoded Strings**: `"feet", "code", "feet#code", "feet###code"`

## Solution

### Solution 1 using Idea 1
```Python
class Solution:
    """
    @param: strs: a list of strings
    @return: encodes a list of strings to a single string.
    """
    # arr = []
    dic = {} # class level attribute
    def encode(self, strs):
        # write your code here
        encode = ""
        arr = []

        # if empty
        if not strs:
            return ""

        # count length and append
        for str in strs:
            arr.append(len(str))
            encode += str
        
        self.dic[encode] = arr

        return encode

    """
    @param: str: A string
    @return: decodes a single string to a list of strings
    """
    def decode(self, str):
        # write your code here
        arr = self.dic[str]

        i=0
        index = 0
        decode = []
        while i < len(str) and index < len(arr):

            j = i + arr[index]

            decode.append(str[i:j])
            i = j
            index += 1
            
        return decode
```
---
Because the testing process is easy for this problem, so if you use an array as instance-level variable, it is also correct. But it is better to use dictionary, in case that a single Solution instance handles multiple inputs, as it prevents `dic` from being overwritten or contaminated.

```Python
class Solution:
    """
    @param: strs: a list of strings
    @return: encodes a list of strings to a single string.
    """
    arr = []
    def encode(self, strs):
        # write your code here
        encode = ""

        # if empty
        if not strs:
            return ""

        # count length and append
        for str in strs:
            self.arr.append(len(str))
            encode += str
        
        #self.dic[encode] = arr

        return encode

    """
    @param: str: A string
    @return: decodes a single string to a list of strings
    """
    def decode(self, str):
        # write your code here

        i=0
        index = 0
        decode = []
        while i < len(str) and index < len(self.arr):

            j = i + self.arr[index]

            decode.append(str[i:j])
            i = j
            index += 1

        return decode
```
---

## Wrong Solutions

### Wrong Solution 1
```Python
class Solution:
    """
    @param: strs: a list of strings
    @return: encodes a list of strings to a single string.
    """
    # arr = []
    dic = {} # class level attribute
    def encode(self, strs):
        # write your code here
        encode = ""
        arr = []

        # if empty
        if not strs:
            return ""

        # count length and append
        for str in strs:
            arr.append(len(str))
            encode += str
        
        dic[encode] = arr

        return encode

    """
    @param: str: A string
    @return: decodes a single string to a list of strings
    """
    def decode(self, str):
        # write your code here
        arr = dic[str]

        i=0
        index = 0
        decode = []
        while i < len(str) and index < len(arr):

            j = i + arr[index]

            decode.append(str[i:j])
            i = j
            index += 1

        return decode
```
Reason: The `dic` dictionary is defined at the class level. Instead, we should use `self.dic` to define and access the dictionary at the instance level. `self.dic` will be initialized in the __init__ method, making it an instance-level variable.


### Wrong Solution 2

```Python
```