---
title: "balanced-binary-tree"
date: 2024-02-05
layout: post
---

```kotlin
class Solution {
    fun isBalanced(root: TreeNode?): Boolean {
        if (root == null) return true

        if (abs(height(root.left) - height(root.right)) > 1) {
            return false
        } else {
            return isBalanced(root.left) && isBalanced(root.right)
        }
    }

    private fun height(node: TreeNode?): Int {
        if (node == null) {
            return -1
        }
        return 1 + max(height(node.left), height(node.right))
    }
}
```
