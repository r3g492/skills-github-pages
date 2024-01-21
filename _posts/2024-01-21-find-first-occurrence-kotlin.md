---
title: "find-the-index-of-the-first-occurrence-in-a-string"
date: 2024-01-21
layout: post
---

```kotlin
class Solution {
    fun strStr(haystack: String, needle: String): Int {
        if (haystack == needle) return 0
        
        for (i in 0..haystack.length - needle.length) {
            if (haystack.substring(i, i + needle.length) == needle) return i
        }
        return -1
    }
}
```
