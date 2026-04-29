---
title: 704. 二分查找
created: 2026-04-29
updated: 2026-04-29
type: problem
tags: [binary-search, array]
sources: []
confidence: medium
frequency: high
---

# 704. 二分查找

## 题目描述
给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。

## 我的实现

**左闭右闭 [left, right]**

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        // 闭区间
        while (left <= right) {
            // 闭区间防止溢出不需要+1
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else  {
                right = mid - 1;
            }
        }
        return -1;
    }
}
```

## 心得

- **只用全闭合区间**，避免混淆
- 闭区间：`left = 0, right = len - 1`，循环条件 `left <= right`
- 边界更新：`left = mid + 1`，`right = mid - 1`（都有 ±1，不会死循环）
- `mid = left + (right - left) / 2` 向下取整即可

## 相关题目
- [[35-搜索插入位置]] - 二分查找变形
- [[69-x的平方根]] - 二分答案
- [[367-有效的完全平方数]] - 二分答案

## 变体
- 查找第一个等于target的位置
- 查找最后一个等于target的位置
- 查找第一个大于target的位置
- 查找最后一个小于target的位置