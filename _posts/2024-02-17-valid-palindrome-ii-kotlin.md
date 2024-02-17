---
title: "valid-palindrome-ii"
date: 2024-02-17
layout: post
---

```kotlin
class Solution {
    fun validPalindrome(s: String): Boolean {
        val sLen = s.length
        for (i in 0..<(sLen / 2)) {
            if (s[i] != s[sLen - i - 1]) {
                val s1 = s.removeRange(i, i + 1)
                val s2 = s.removeRange(sLen - i - 1, sLen - i)
                return innerFunc(s1) || innerFunc(s2)
            }
        }
        return true
    }

    private fun innerFunc(s: String): Boolean {
        val sLen = s.length
        for (i in 0..<(sLen / 2)) {
            if (s[i] != s[sLen - i - 1]) {
                return false
            }
        }
        return true
    }
}
```
