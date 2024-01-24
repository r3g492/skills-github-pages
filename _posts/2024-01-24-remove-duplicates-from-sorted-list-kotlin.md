---
title: "remove-duplicates-from-sorted-list"
date: 2024-01-24
layout: post
---

```kotlin
class Solution {
    fun deleteDuplicates(head: ListNode?): ListNode? {
        var cur = head
        while(cur != null) {
            var next = cur.next
            while(cur.`val` == next?.`val`) {
                cur.next = next.next
                next = cur.next
            }

            cur = cur.next
        }
    
        return head
    }
}
```
