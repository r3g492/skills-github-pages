---
title: "kth-largest-element-in-an-array"
date: 2024-03-12
layout: post
---

```kotlin
class Solution {
    fun findKthLargest(nums: IntArray, k: Int): Int {
        val list: MutableList<Int> = mutableListOf()

        for (i in nums.indices) {
            list.add(nums[i])
        }

        return quickSelect(list, k)
    }

    private fun quickSelect(nums: MutableList<Int>, k: Int): Int {
        val pivot = nums[nums.size / 2]
        val left = nums.filter { it < pivot }
        val right = nums.filter { it > pivot }
        val mid = nums.filter { it == pivot }

        return when {
            k <= right.size -> quickSelect(right.toMutableList(), k)
            k > right.size + mid.size -> quickSelect(left.toMutableList(), k - right.size - mid.size)
            else -> pivot
        }
    }
}
```
