---
title: 35. 搜索插入位置
created: 2026-04-29
updated: 2026-04-29
type: problem
tags: [binary-search, array]
sources: []
confidence: medium
frequency: high
---

# 35. 搜索插入位置

## 题目描述
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

## 我的实现

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else if (nums[mid] > target) {
                right = mid - 1;
            }
        }
        return left;
    }
}
```

## 心得

- 和704二分查找几乎一样，只是最后返回 `left` 而不是 `-1`
- 循环结束时 `left > right`，`left` 就是 target 应该插入的位置
- 为什么？因为最后一次更新：
  - 如果 `nums[mid] < target`，`left = mid + 1`，说明 target 应该在 mid 右边
  - 如果 `nums[mid] > target`，`right = mid - 1`，但 target 应该在 mid 左边，而 `left` 还在原位置

## 相关题目
- [[704-binary-search]] - 标准二分查找
- [[69-x的平方根]] - 二分答案