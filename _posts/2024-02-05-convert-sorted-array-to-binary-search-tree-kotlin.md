---
title: "symmetric-tree"
date: 2024-02-05
layout: post
---

```kotlin
class Solution {
    fun sortedArrayToBST(nums: IntArray): TreeNode? {
        return recursiveLogic(nums, 0, nums.lastIndex)
    }

    private fun recursiveLogic(nums: IntArray, startI: Int, endI: Int): TreeNode? {
        if (startI > endI) return null
        val midI = (startI + endI) / 2
        val newNode = TreeNode(nums[midI])
        newNode.left = recursiveLogic(nums, startI, midI - 1)
        newNode.right = recursiveLogic(nums, midI + 1, endI)
        return newNode
    }
}

```
