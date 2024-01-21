---
title: "search-insert-position"
date: 2024-01-21
layout: post
---

```kotlin
class Solution {
    fun searchInsert(nums: IntArray, target: Int): Int {
        if (nums.isEmpty()) return 0
        return loopMethod(nums, 0, nums.size - 1, target)
    }

    private fun loopMethod(nums: IntArray, start: Int, end: Int, target: Int): Int {
        if (start > end) return start
        val mid = (start + end) / 2
        if (nums[mid] == target) return mid
        if (nums[mid] > target) {
            return loopMethod(nums, start, mid - 1, target)
        }
        return loopMethod(nums, mid + 1, end, target)
    }
}
```
