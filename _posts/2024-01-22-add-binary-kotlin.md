---
title: "add-binary"
date: 2024-01-22
layout: post
---

```kotlin
class Solution {
    fun addBinary(a: String, b: String): String {

        val longerString = if (a.length > b.length) a else b
        val shorterString = if (a.length > b.length) b else a

        var answer = ""
        var carry = 0

        var longCursor = longerString.length - 1
        var shortCursor = shorterString.length - 1
        var addum = 0
        while (longCursor >= 0) {
            val longValue = longerString[longCursor].digitToInt()
            val shortValue = if (shortCursor >= 0) {
                shorterString[shortCursor].digitToInt()
            } else {
                0
            }
            addum = addOneBinary(longValue, shortValue, carry)
            when (addum) {
                2 -> {
                    carry = 1
                    answer = "0$answer"
                }
                3 -> {
                    carry = 1
                    answer = "1$answer"
                }
                1 -> {
                    carry = 0
                    answer = "1$answer"
                }
                0 -> {
                    carry = 0
                    answer = "0$answer"
                }
            }
            longCursor--
            shortCursor--
        }

        when (addum) {
            2 -> {
                answer = "1$answer"
            }
            3 -> {
                answer = "1$answer"
            }
            else -> {

            }
        }

        return answer
    }

    private fun addOneBinary(a: Int, b: Int, carry: Int): Int {
        println(a + b + carry)
        return a + b + carry
    }
}
```
