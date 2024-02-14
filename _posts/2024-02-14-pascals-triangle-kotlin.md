---
title: "pascals-triangle"
date: 2024-02-14
layout: post
---

```kotlin
class Solution {
    fun generate(numRows: Int): List<List<Int>> {
        val answer: MutableList<MutableList<Int>> = mutableListOf()
        var previousList: MutableList<Int> = mutableListOf(1)
        answer.add(previousList)

        for (i in 2..numRows) {
            val localList: MutableList<Int> = mutableListOf()

            for (j in 1..i) {
                if (j == 1 || j == i) {
                    localList.add(1)
                    continue
                }

                val a = previousList[j - 2]
                val b = previousList[j - 1]

                localList.add(a + b)
            }

            previousList = localList
            answer.add(localList)
        }
        return answer
    }
}
```
