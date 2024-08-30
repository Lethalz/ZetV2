2408300957
	Status: #idea 
		Tags: 

# Base64 table conversion


## Base64 Conversion Table

Base64 encoding uses a set of 64 characters to represent binary data. Here's a table showing the mapping of 6-bit values to Base64 characters:

| Value | Char | Value | Char | Value | Char | Value | Char |
|-------|------|-------|------|-------|------|-------|------|
| 0     | A    | 16    | Q    | 32    | g    | 48    | w    |
| 1     | B    | 17    | R    | 33    | h    | 49    | x    |
| 2     | C    | 18    | S    | 34    | i    | 50    | y    |
| 3     | D    | 19    | T    | 35    | j    | 51    | z    |
| 4     | E    | 20    | U    | 36    | k    | 52    | 0    |
| 5     | F    | 21    | V    | 37    | l    | 53    | 1    |
| 6     | G    | 22    | W    | 38    | m    | 54    | 2    |
| 7     | H    | 23    | X    | 39    | n    | 55    | 3    |
| 8     | I    | 24    | Y    | 40    | o    | 56    | 4    |
| 9     | J    | 25    | Z    | 41    | p    | 57    | 5    |
| 10    | K    | 26    | a    | 42    | q    | 58    | 6    |
| 11    | L    | 27    | b    | 43    | r    | 59    | 7    |
| 12    | M    | 28    | c    | 44    | s    | 60    | 8    |
| 13    | N    | 29    | d    | 45    | t    | 61    | 9    |
| 14    | O    | 30    | e    | 46    | u    | 62    | +    |
| 15    | P    | 31    | f    | 47    | v    | 63    | /    |

```ad-info
title: Base64 Padding
collapse: closed
icon: equals

The '=' character is used for padding at the end of Base64 encoded data to ensure the length is a multiple of 4 characters. One '=' means the last group contained only 2 bytes of data, while '==' means it contained only 1 byte.
```

```ad-example
title: Base64 Encoding Process
collapse: closed
icon: cogs

1. Take 3 bytes of binary data (24 bits)
2. Split into 4 groups of 6 bits each
3. Convert each 6-bit group to its corresponding Base64 character
4. If the data doesn't divide evenly into 3-byte groups, add padding:
   - If 1 byte remains, encode it as 2 Base64 chars + '=='
   - If 2 bytes remain, encode them as 3 Base64 chars + '='
```

This table and the accompanying notes should help in understanding how Base64 encoding works, which is crucial for working with PEM and other Base64-encoded formats in cryptography.

---
# Reference