---
title: "minimum-depth-of-binary-tree"
date: 2024-02-06
layout: post
---

```kotlin
class Solution {
    fun minDepth(root: TreeNode?): Int {
        minDepth = null
        recursiveLogic(1, root)

        val localMinDepth = minDepth ?: return 0
        return localMinDepth
    }

    private fun recursiveLogic(depth: Int, node: TreeNode?) {
        if (node == null) {
            return
        }
        if (isLeaf(node)) {
            val minDepthLocal = minDepth
            if (minDepthLocal == null) {
                minDepth = depth
            } else if (minDepthLocal > depth) {
                minDepth = depth
            }

            return
        }

        recursiveLogic(depth + 1, node.left)
        recursiveLogic(depth + 1, node.right)
    }

    private fun isLeaf(node: TreeNode): Boolean {
        return node.left == null && node.right == null
    }

    companion object {
        var minDepth: Int? = null
    }
}
```
