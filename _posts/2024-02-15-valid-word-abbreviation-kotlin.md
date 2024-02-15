---
title: "valid-word-abbreviation"
date: 2024-02-15
layout: post
---

```kotlin
class Solution {
    fun validWordAbbreviation(word: String, abbr: String): Boolean {
        var i = 0
        var j = 0

        while(j < abbr.length) {
            var isAtLead = true
            val k = j
            while(abbr[j].isDigit()) {
                if (isAtLead && (abbr[j] == '0')) {
                    return false
                }
                isAtLead = false
                j++
                if (j >= abbr.length) break
            }
            val number = abbr.substring(k, j).toIntOrNull()
            if (number != null) {
                i += number
            }
            if (i >= word.length || j >= abbr.length) {
                if (j < abbr.length) return false
                if (i < word.length) return false
                break
            }
            if (word[i] != abbr[j]) {
                return false
            }
            i++
            j++
        }
        return i == word.length
    }
}
```
