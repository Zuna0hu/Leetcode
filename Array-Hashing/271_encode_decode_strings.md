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


```Python

```