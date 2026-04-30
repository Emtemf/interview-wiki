---
title: 34. 在排序数组中查找元素的第一个和最后一个位置
created: 2026-04-29
updated: 2026-04-29
type: problem
tags: [binary-search, array]
sources: []
confidence: high
frequency: high
---

# 34. 在排序数组中查找元素的第一个和最后一个位置

## 题目描述
给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。如果数组中不存在目标值，返回 `[-1, -1]`。

## 我的实现

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return new int[]{-1, -1};
        }
        return new int[]{findResLeft(nums, target), findResRight(nums, target)};
    }

    // 找左边界：往左边缩，right一直减
    // 循环结束后 left 会停在第一个 >= target 的位置
    // 如果 left 出数组了或 nums[left] != target，说明不存在
    private int findResLeft(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < target) {
                left = mid + 1;
            } else {
                // nums[mid] >= target，往左缩
                right = mid - 1;
            }
        }
        // 出数组了，不存在这个值
        if (left >= nums.length || nums[left] != target) {
            return -1;
        }
        return left;
    }

    // 找右边界：往右边缩，left一直加
    // 循环结束后 right 会停在最后一个 <= target 的位置
    // 如果 right 出数组了（< 0）或 nums[right] != target，说明不存在
    private int findResRight(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] <= target) {
                left = mid + 1;
            } else {
                // nums[mid] > target，往左缩
                right = mid - 1;
            }
        }
        // 出数组了，不存在这个值
        if (right < 0 || nums[right] != target) {
            return -1;
        }
        return right;
    }
}
```

## 核心理解

| 找什么 | 条件 | 最后停在哪 | 返回谁 |
|--------|------|------------|--------|
| 左边界 | `>= target` 往左缩 | left 停在第一个 >= target | `left` |
| 右边界 | `<= target` 往右缩 | right 停在最后一个 <= target | `right` |

**关键点**：
- 找左边界：`right` 一直减，最后 `left` 出来了
- 找右边界：`left` 一直加，最后 `right` 出来了
- 先检查越界，再访问数组

## 相关题目
- [[704-binary-search]] - 标准二分查找
- [[35-search-insert-position]] - 搜索插入位置