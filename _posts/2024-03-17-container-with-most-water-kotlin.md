---
title: "container-with-most-water"
date: 2024-03-17
layout: post
---

```kotlin
class Solution {
    fun maxArea(height: IntArray): Int {
        var maxArea = 0
        var left = 0
        var right = height.size - 1
        while (left < right) {
            maxArea = maxOf(maxArea, min(height[left], height[right]) * (right - left))
            if (height[left] < height[right]) {
                left++
            } else {
                right--
            }
        }
        return maxArea
    }
}
```
