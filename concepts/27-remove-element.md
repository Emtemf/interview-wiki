---
title: 27. 移除元素
created: 2026-04-29
updated: 2026-04-29
type: problem
tags: [two-pointers, array]
sources: []
confidence: high
frequency: high
---

# 27. 移除元素

## 题目描述
给定一个数组 nums 和一个值 val，原地移除所有数值等于 val 的元素，返回移除后数组的新长度。

## 我的实现

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int index = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[index++] = nums[i];
            }
        }
        return index;
    }
}
```

## 心得

- **快慢指针**：`i` 是快指针遍历数组，`index` 是慢指针记录有效位置
- 遇到不等于 val 的元素，放到 `index` 位置，然后 `index++`
- 时间复杂度 O(n)，空间复杂度 O(1)

## 相关题目
- [[704-binary-search]] - 二分查找