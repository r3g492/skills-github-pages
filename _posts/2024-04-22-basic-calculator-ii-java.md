---
title: "basic-calculator-ii"
date: 2024-04-22
layout: post
---

```java
class Solution {
    public int calculate(String s) {
        if (s == null) {
            return 0;
        }

        s = s.replaceAll(" ", "");

        int len = s.length();
        if (len == 0) {
            return 0;
        }

        List<Integer> stack = new ArrayList<>();

        int num = 0;
        char sign = '+';

        for (int i = 0; i < len; i++) {
            char c = s.charAt(i);

            if (Character.isDigit(c)) {
                num = num * 10 + c - '0';
            }

            if (!Character.isDigit(c) || i == len - 1) {
                if (sign == '+') {
                    stack.add(num);
                } else if (sign == '-') {
                    stack.add(-num);
                } else if (sign == '*') {
                    stack.add(stack.remove(stack.size() - 1) * num);
                } else if (sign == '/') {
                    stack.add(stack.remove(stack.size() - 1) / num);
                }

                sign = c;
                num = 0;
            }
        }

        int result = 0;
        for (int n : stack) {
            result += n;
        }

        return result;
    }
}
```
