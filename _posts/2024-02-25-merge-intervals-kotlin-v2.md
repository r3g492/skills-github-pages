---
title: "merge-intervals"
date: 2024-02-25
layout: post
---

```kotlin
class Solution {
    fun merge(intervals: Array<IntArray>): Array<IntArray> {
        if (intervals.isEmpty()) {
            return arrayOf()
        }

        if (intervals.size == 1) {
            return intervals
        }

        intervals.sortBy { it[0] }

        if (intervals.size == 2) {
            if (isTwoArrayMergeable(intervals[0], intervals[1])) {
                return arrayOf(
                    mergeTwoIntArray(intervals[0], intervals[1])
                )
            }
            return intervals
        }

        val answer: MutableList<IntArray> = mutableListOf()

        var cur = intervals[0]
        var nextIndex = 1

        while (nextIndex < intervals.size) {
            if (isTwoArrayMergeable(cur, intervals[nextIndex])) {
                cur = mergeTwoIntArray(cur, intervals[nextIndex])
            } else {
                answer.add(cur)
                cur = intervals[nextIndex]
            }
            nextIndex++
        }
        answer.add(cur)

        return answer.toTypedArray()
    }

    private fun isTwoArrayMergeable(left: IntArray, right: IntArray): Boolean {
        return left[1] >= right[0] || left[0] >= right[1]
    }

    private fun mergeTwoIntArray(left: IntArray, right: IntArray): IntArray {
        return intArrayOf(
            min(left[0], right[0]),
            max(left[1], right[1])
        )
    }
}
```
