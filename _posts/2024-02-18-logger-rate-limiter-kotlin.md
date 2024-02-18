---
title: "logger-rate-limiter"
date: 2024-02-18
layout: post
---

```kotlin
class Logger {

    fun shouldPrintMessage(timestamp: Int, message: String): Boolean {
        val prevMessageTimeStamp = hashMap[message]
        if (prevMessageTimeStamp == null) {
            hashMap[message] = timestamp
            return true
        }

        if (prevMessageTimeStamp + 10 > timestamp) {
            return false
        }

        hashMap[message] = timestamp
        return true
    }

    init {
        hashMap = mutableMapOf()
    }

    companion object {
        var hashMap: MutableMap<String, Int> = mutableMapOf()
    }
}
```
