---
title: 69. x 的平方根
created: 2026-04-29
updated: 2026-04-29
type: problem
tags: [binary-search, math]
sources: []
confidence: high
frequency: high
---

# 69. x 的平方根

## 题目描述
给定一个非负整数 x，计算并返回 x 的算术平方根的整数部分。

## 我的实现

```java
class Solution {
    public int mySqrt(int x) {
        long left = 1;
        long right = x;
        while (left <= right) {
            long mid = left + (right - left) / 2;
            if (mid * mid == x) {
                return (int) mid;
            } else if (mid * mid < x) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return (int) right;
    }
}
```

## 心得

- 平方根整数部分 = 向下取整
- `right` 是最后一个 `mid*mid <= x` 的位置，循环结束返回 `right`
- **防止溢出**：用 `long` 类型，否则 `mid*mid` 可能溢出 int

## 相关题目
- [[704-binary-search]] - 标准二分查找
- [[34-find-first-and-last-position]] - 找左右边界