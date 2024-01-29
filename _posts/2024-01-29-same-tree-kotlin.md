---
title: "same-tree"
date: 2024-01-29
layout: post
---

```kotlin
class Solution {
    fun isSameTree(p: TreeNode?, q: TreeNode?): Boolean {
        if (p == null && q == null) return true
        if (p == null || q == null) return false
        
        var pNext = p
        var qNext = q
        while (pNext != null && qNext != null) {
            if (pNext.`val` != qNext.`val`) return false
            pNext = pNextNode(pNext)
            qNext = qNextNode(qNext)
        }
        if (pNext != null || qNext != null) return false
        
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right)
    }
    
    private fun pNextNode(p: TreeNode?): TreeNode? {
        if (p == null) return null
        if (p.left != null) return p.left
        if (p.right != null) return p.right
        return null
    }
    
    private fun qNextNode(q: TreeNode?): TreeNode? {
        if (q == null) return null
        if (q.left != null) return q.left
        if (q.right != null) return q.right
        return null
    }
}
```
