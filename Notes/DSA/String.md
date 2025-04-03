[8. String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/)

```java
class Solution {
    public int myAtoi(String s) {
        int i = 0, sign = 1, n = s.length();
        long num = 0;
        while (i < n && s.charAt(i) == ' ') {
            i++;
        }
        if (i >= n) return 0;
        if (s.charAt(i) == '+' || s.charAt(i) == '-') {
            sign = (s.charAt(i) == '-') ? -1 : 1;
            i++;
        }
        while (i < n && Character.isDigit(s.charAt(i))) {
            int digit = s.charAt(i) - '0';
            if (num > (Integer.MAX_VALUE - digit) / 10) {
                return (sign == 1) ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
            num = num * 10 + digit;
            i++;
        }
        return (int) (num * sign);
    }
}

```



