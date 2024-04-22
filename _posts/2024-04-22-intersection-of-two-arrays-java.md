---
title: "intersection-of-two-arrays"
date: 2024-04-22
layout: post
---

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Map<Integer, Boolean> a = new HashMap<>();
        Set<Integer> answer = new HashSet<>();
        for (Integer num : nums1) {
            a.put(num, true);
        }

        for (Integer num : nums2) {
            if (a.containsKey(num)) {
                answer.add(num);
            }
        }

        return answer.stream().mapToInt(Integer::intValue).toArray();
    }
}
```
