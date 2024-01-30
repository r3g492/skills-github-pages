---
title: "symmetric-tree"
date: 2024-01-30
layout: post
---

```kotlin
class Solution {
    fun isSymmetric(root: TreeNode?): Boolean {
        if (root?.left?.`val` != root?.right?.`val`) return false
        return symmetricNodeCheckRecursive(root?.left, root?.right)
    }

    private fun symmetricNodeCheckRecursive(left: TreeNode?, right: TreeNode?): Boolean {
        if (left?.`val` != right?.`val`) return false
        if (left != null) {
            if(!symmetricNodeCheckRecursive(left.left, right?.right)) {
                return false
            }
        }
        if (left != null) {
            if(!symmetricNodeCheckRecursive(left.right, right?.left)) {
                return false
            }
        }

        return true
    }
}

```
