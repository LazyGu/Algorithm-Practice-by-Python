# Reverse Interger
## Given a 32-bit signed integer, reverse digits of an integer.

### Examples
```
Input: 123
Output: 321
```
```
Input: -123
Output: -321
```
```
Input: 120
Output: 21
```
### Note
```
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. 
For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.
```

### Solutions
```
class Solution01:
    def reverse(self):
        y, res = abs(x), 0
        boundry = (1<<31)-1 if x>0 else 1<<31
        while y != 0:
            res = res*10 + y%10
            y //= 10
            if res > boundry:
                return 0
        return res if x>0 else -res
    print(reverse(x))
```
