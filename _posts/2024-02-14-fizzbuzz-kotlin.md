---
title: "fizzbuzz"
date: 2024-02-14
layout: post
---

```kotlin
class Solution {
    fun fizzBuzz(n: Int): List<String> {
        val listOfString: MutableList<String> = mutableListOf()
        for (i in 1..n) {
            val threeLeftOvers = i % 3
            val fiveLeftOvers = i % 5

            if (threeLeftOvers == 0 && fiveLeftOvers == 0) {
                listOfString.add("FizzBuzz")
                continue
            }
            
            if (threeLeftOvers == 0) {
                listOfString.add("Fizz")
                continue
            }

            if (fiveLeftOvers == 0) {
                listOfString.add("Buzz")
                continue
            }

            listOfString.add(i.toString())
        }
        return listOfString
    }
}
```
