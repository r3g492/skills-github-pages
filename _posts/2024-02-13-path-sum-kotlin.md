---
title: "path-sum"
date: 2024-02-13
layout: post
---

```kotlin
class Solution {
    fun hasPathSum(root: TreeNode?, targetSum: Int): Boolean {
        if (root == null) return false
        return recursiveLogic(root, targetSum, 0)
    }

    private fun recursiveLogic(node: TreeNode, targetSum: Int, curSum: Int): Boolean {
        if (node.right == null && node.left == null) {
            return targetSum == (curSum + node.`val`)
        }

        val leftNode = node.left
        if (leftNode != null) {
            if (recursiveLogic(leftNode, targetSum, curSum + node.`val`))
                return true
        }

        val rightNode = node.right
        if (rightNode != null) {
            if (recursiveLogic(rightNode, targetSum, curSum + node.`val`))
                return true
        }
        return false
    }
}
```
