---
title: "image-smoother"
date: 2024-02-17
layout: post
---

```kotlin
class Solution {
    fun imageSmoother(img: Array<IntArray>): Array<IntArray> {
        if (img.isEmpty()) {
            return listOf<IntArray>().toTypedArray()
        }
        val maxHeightIndex = img.size
        val maxLengthIndex = img[0].size

        val movementList: List<Int> = listOf(-1, 0, 1)

        val answerList: MutableList<IntArray> = mutableListOf()
        for(i in 0..<maxHeightIndex) {
            val intList: MutableList<Int> = mutableListOf()
            for (j in 0..<maxLengthIndex) {
                val localAverageList: MutableList<Int> = mutableListOf()
                movementList.forEach { yDiff ->
                    val localY = i + yDiff
                    movementList.forEach { xDiff ->
                        val localX = j + xDiff
                        if (localY in 0..<maxHeightIndex && localX in 0..<maxLengthIndex) {
                            localAverageList.add(img[localY][localX])
                        }
                    }
                }
                val av = localAverageList.average().toInt()
                intList.add(av)
            }
            answerList.add(intList.toIntArray())
        }

        return answerList.toTypedArray()
    }
}
```
