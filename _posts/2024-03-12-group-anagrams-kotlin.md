---
title: "group-anagrams"
date: 2024-03-12
layout: post
---

```kotlin
class Solution {
    fun groupAnagrams(strs: Array<String>): List<List<String>> {
        val keyInputMap = mutableMapOf<String, MutableList<String>>()
        
        for (str in strs) {
            val key = generateAnagramKey(str)
            
            if (keyInputMap.containsKey(key)) {
                keyInputMap[key]!!.add(str)
            } else {
                keyInputMap[key] = mutableListOf(str)
            }
        }
        
        return keyInputMap.values.toList()
    }
    
    private fun generateAnagramKey(str: String): String {
        val alphabetMap = mutableMapOf<Char, Int>()
        
        for (char in str) {
            alphabetMap[char] = alphabetMap.getOrDefault(char, 0) + 1
        }
        
        val keyStringBuilder = StringBuilder()
        for (char in 'a'..'z') {
            if (!alphabetMap.containsKey(char)) {
                continue
            }
            keyStringBuilder.append("$char:${alphabetMap[char]}")
        }
        return keyStringBuilder.toString()
    }
}

```
