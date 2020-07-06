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
| 2 / 7  | "0.(285714)" |


# Implementation :
```java
class Solution {
    public String fractionToDecimal(int numerator, int denominator) {
    if (numerator == 0) 
        return "0";
    if (denominator == 0)  
        throw new IllegalArgumentException();
        
    StringBuilder fraction = new StringBuilder();
    // If either one is negative (not both)
    if ((numerator < 0 && denominator > 0) || (denominator < 0 && numerator > 0)) {
        fraction.append("-");
    }
    // Convert to Long or else abs(-2147483648) overflows
    long dividend = Math.abs((long) numerator);
    long divisor = Math.abs((long) denominator);
    fraction.append(dividend / divisor);
    long remainder = dividend % divisor;
    if (remainder == 0) {
        return fraction.toString();
    }
    fraction.append(".");
    Map<Long, Integer> map = new HashMap<>();
    while (remainder != 0) {
        if (map.containsKey(remainder)) {
            fraction.insert(map.get(remainder), "(");
            fraction.append(")");
            break;
        }
        map.put(remainder, fraction.length());
        remainder *= 10;
        fraction.append(remainder / divisor);
        remainder %= divisor;
    }
    return fraction.toString();
  }
}
```

# References :
1. https://www.youtube.com/watch?v=a-62yK1S1O4
2. https://leetcode.com/problems/fraction-to-recurring-decimal/solution
