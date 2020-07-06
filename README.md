# Fraction to recurring decimal
## https://leetcode.com/problems/fraction-to-recurring-decimal

Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.

If the fractional part is repeating, enclose the repeating part in parentheses.
```
Example 1:

Input: numerator = 1, denominator = 2
Output: "0.5"

Example 2:

Input: numerator = 2, denominator = 1
Output: "2"

Example 3:

Input: numerator = 2, denominator = 3
Output: "0.(6)"
```

## Test Cases :

**Integer.MIN_VALUE = -2147483648  ,  Integer.MAX_VALUE = 2147483647 **


| Test case  | Explanation |
| ------------- | ------------- |
| 0 / 1  | Numerator is zero.  |
| 1 / 0  | Divisor is 0, should handle it by throwing an exception but here we ignore for simplicity sake.  |
| 20 / 4  | Answer is a whole integer, should not contain the fractional part.  |
| 1 / 2  | Answer is 0.5, no recurring decimal.  |
| -1 / 2 or 1 / -2  | One of the numerator or denominator is negative, fraction is negative.  |
| -1 / -2  | Both numerator and denominator are negative, should result in positive fraction.  |
| −2147483648 / -1  | Beware of overflow if you cast to positive.  |


# Implementation :
```java

```

# References :
1. https://www.youtube.com/watch?v=a-62yK1S1O4
2. https://leetcode.com/problems/fraction-to-recurring-decimal/solution
