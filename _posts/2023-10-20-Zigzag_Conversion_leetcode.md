---
title: "Zigzag_Conversion_leetcode_solution"
date: 2023-10-20
layout: post
---

```go
func convert(s string, numRows int) string {
	var answer string
	if numRows == 1 {
		return s
	}
	var leftJump int = 2*numRows - 2
	var rightJump int = 0
	var cnt int = 0
	for leftJump >= 0 {
		var i = cnt
		for i < len(s) {
			answer = answer + string(s[i])
			if leftJump != 0 && rightJump != 0 {
				i = i + leftJump
				if i < len(s) {
					answer = answer + string(s[i])
				}
				i = i + rightJump
			} else {
				i = i + leftJump + rightJump
			}
		}
		leftJump = leftJump - 2
		rightJump = rightJump + 2
		cnt++
	}
	return answer
}
```
