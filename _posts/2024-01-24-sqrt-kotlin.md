---
title: "sqrt"
date: 2024-01-24
layout: post
---

```kotlin
class Solution {
    fun mySqrt(x: Int): Int {
        val xLong = x.toLong()
        var nearestHalf: Long = xLong
        while (nearestHalf * nearestHalf > xLong) {
            nearestHalf /= 2
        }

        while (nearestHalf * nearestHalf <= xLong) {
            if (nearestHalf * nearestHalf == xLong) {
                return nearestHalf.toInt()
            }
            nearestHalf += 1
        }

        return (nearestHalf - 1).toInt()
    }
}
```
