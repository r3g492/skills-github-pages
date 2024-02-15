---
title: "unique-number-of-occurrences"
date: 2024-02-15
layout: post
---

```kotlin
class Solution {
    fun uniqueOccurrences(arr: IntArray): Boolean {
        val occurrenceMap: MutableMap<Int, Int> = mutableMapOf()
        for (i in arr) {
            val existingOccurrence = occurrenceMap[i]
            if (existingOccurrence == null) {
                occurrenceMap[i] = 1
                continue
            }
            occurrenceMap[i] = existingOccurrence + 1
        }
        val duplicationMap: MutableMap<Int, Boolean> = mutableMapOf()
        for (i in occurrenceMap) {
            val existingDuplication = duplicationMap[i.value]
            if (existingDuplication == null) {
                duplicationMap[i.value] = true
                continue
            }
            return false
        }
        return true
    }
}
```
