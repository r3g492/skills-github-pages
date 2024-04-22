---
title: "nested-list-weight-sum"
date: 2024-04-22
layout: post
---

```java
class Solution {
    public int depthSum(List<NestedInteger> nestedList) {
        return depthSumRecursive(nestedList, 1);
    }

    private int depthSumRecursive(List<NestedInteger> nestedList, int depth) {
        int sum = 0;
        for (NestedInteger ni : nestedList) {
            if (ni.isInteger()) {
                sum += ni.getInteger() * depth;
            } else {
                sum += depthSumRecursive(ni.getList(), depth + 1);
            }
        }
        return sum;
    }
}
```
