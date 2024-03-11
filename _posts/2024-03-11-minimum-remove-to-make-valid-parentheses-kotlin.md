---
title: "minimum-remove-to-make-valid-parentheses"
date: 2024-03-11
layout: post
---

```kotlin
class Solution {
    fun minRemoveToMakeValid(s: String): String {
        val stack = mutableListOf<Int>()
        val newS = StringBuilder(s)
        for (i in s.indices) {
            if (s[i] == '(') {
                stack.add(i)
                continue
            }
            if (s[i] == ')') {
                if (stack.isNotEmpty()) {
                    stack.removeAt(stack.size - 1)
                } else {
                    newS[i] = '*'
                }
            }
        }
        for (i in stack) {
            newS[i] = '*'
        }

        return newS.filter {
            it != '*'
        }.toString()
    }
}
```
