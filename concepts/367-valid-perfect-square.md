---
title: 367. 有效的完全平方数
created: 2026-04-29
updated: 2026-04-29
type: problem
tags: [binary-search, math]
sources: []
confidence: high
frequency: medium
---

# 367. 有效的完全平方数

## 题目描述
给定一个正整数 num，判断它是否是完全平方数。

## 我的实现

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        long left = 1;
        long right = num;
        while (left <= right) {
            long mid = left + (right - left) / 2;
            if (mid * mid == num) {
                return true;
            } else if (mid * mid < num) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return false;
    }
}
```

## 心得

- 和 [[69-sqrt]] 几乎一样，只是返回 boolean
- 找到 `mid*mid == num` 就返回 true，否则 false
- **用 long 防溢出**：int 相乘可能溢出

## 相关题目
- [[69-sqrt]] - x的平方根