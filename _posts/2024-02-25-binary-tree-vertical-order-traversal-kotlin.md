---
title: "binary-tree-vertical-order-traversal"
date: 2024-02-25
layout: post
---

```kotlin
class Solution {

    private val map: MutableMap<Int, MutableList<ColWithTreeNode>> = mutableMapOf()

    fun verticalOrder(root: TreeNode?): List<List<Int>> {
        recursiveLogic(root, 0, 0)
        val sorted = map.toSortedMap()
        return sorted.map {
            it.value
        }.map {
            it.sortedBy { colWithNode ->
                colWithNode.colNum
            }.map {
                it.treeNode.`val`
            }
        }
    }

    private fun recursiveLogic(node: TreeNode?, curRow: Int, curCol: Int) {
        if (node != null) {
            if (map[curRow] != null) {
                map[curRow]!!.add(
                    ColWithTreeNode(
                        treeNode = node,
                        colNum = curCol,
                    )
                )
            } else {
                map[curRow] = mutableListOf(
                    ColWithTreeNode(
                        treeNode = node,
                        colNum = curCol,
                    )
                )
            }
        } else {
            return
        }
        recursiveLogic(node.left, curRow - 1, curCol + 1)
        recursiveLogic(node.right, curRow + 1, curCol + 1)
    }

    class ColWithTreeNode(
        val treeNode: TreeNode,
        val colNum: Int,
    ) {
        override fun toString(): String {
            return "ColWithTreeNode(treeNode=$treeNode, colNum=$colNum)"
        }
    }
}
```
