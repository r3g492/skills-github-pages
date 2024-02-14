---
title: "merge-strings-alternately"
date: 2024-02-14
layout: post
---

```kotlin
class Solution {
    fun mergeAlternately(word1: String, word2: String): String {
        var answer = ""

        val word1Len = word1.length
        val word2Len = word2.length
        for (i in 0..max(word1Len, word2Len)) {
            if (i < word1Len) {
                answer += word1[i]
            }
            if (i < word2Len) {
                answer += word2[i]
            }
        }
        return answer
    }
}
```
