---
title: "atoi"
date: 2024-01-25
layout: post
---

```kotlin
class Solution {
    fun myAtoi(s: String): Int {
        val one = deleteLeadingWhiteSpaces(s)
        if (one == "") return 0
        val two = checkNextCharacter(one)
        val three = readUntilNonDigit(two.second)
        val four = convertDigitIntoInteger(three, two.first)
        return four
    }

    private fun deleteLeadingWhiteSpaces(s: String): String {
        var localI = 0
        for (i in s.indices) {
            if (s[i] == ' ') {
                localI = i + 1
            } else {
                break
            }
        }
        return s.substring(localI)
    }

    private fun checkNextCharacter(s: String): Pair<Char, String> {
        var sign: Char? = null
        if (s[0] == '+' || s[0] == '-') {
            sign = s[0]
        }
        if (sign == null) return Pair('+', s)
        return Pair(sign, s.substring(1))
    }

    private fun readUntilNonDigit(s: String): String {
        var localI = 0
        for (i in s.indices) {
            if (s[i].isDigit()) {
                localI = i + 1
            } else {
                break
            }
        }
        return s.substring(0, localI)
    }

    private fun convertDigitIntoInteger(s: String, sign: Char): Int {
        var localSum: Long = 0
        for (i in s.indices) {
            localSum *= 10
            localSum += s[i].digitToInt()

            if (sign == '+') {
                if (localSum >= Int.MAX_VALUE) {
                    return Int.MAX_VALUE
                }
            } else {
                if (localSum > Int.MAX_VALUE) {
                    return Int.MIN_VALUE
                }
            }
        }
        return if (sign == '+') {
            localSum.toInt()
        } else {
            -localSum.toInt()
        }
    }
}
```
