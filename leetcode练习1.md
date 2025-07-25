# Rust语法练习向 LeetCode 简单题推荐
创建日期：2025年7月24日

本清单聚焦于Rust语法、数据结构、所有权、模式匹配、Option/Result、字符串和集合等常用语法点，适合初学者用来巩固Rust基础。

---

## 1. 字符串与切片【完成】
- [344. 反转字符串](https://leetcode.cn/problems/reverse-string/)  
  可变借用、切片、Vec与String的转换
- [557. 反转字符串中的单词 III](https://leetcode.cn/problems/reverse-words-in-a-string-iii/)  
  split、collect、String拼接

## 2. 数组与Vec【完成】
- [27. 移除元素](https://leetcode.cn/problems/remove-element/)  
  Vec遍历、可变操作
- [283. 移动零](https://leetcode.cn/problems/move-zeroes/)  
  Vec索引、swap、可变借用

## 3. HashMap 基础【完成】
- [1. 两数之和](https://leetcode.cn/problems/two-sum/)  
  HashMap插入、查找、所有权
- [242. 有效的字母异位词](https://leetcode.cn/problems/valid-anagram/)  
  HashMap计数、字符串遍历

## 4. Option/Result与模式匹配【完成】
- [704. 二分查找](https://leetcode.cn/problems/binary-search/)  
  Option返回、match用法
- [35. 搜索插入位置](https://leetcode.cn/problems/search-insert-position/)  
  Result/Option和match

## 5. 迭代器与collect【完成】
- [136. 只出现一次的数字](https://leetcode.cn/problems/single-number/)  
  for、iter、fold等迭代器用法
- [977. 有序数组的平方](https://leetcode.cn/problems/squares-of-a-sorted-array/)  
  map、collect、Vec操作

## 6. 字符处理【完成】
- [389. 找不同](https://leetcode.cn/problems/find-the-difference/)  
  char、String、iter
- [13. 罗马数字转整数](https://leetcode.cn/problems/roman-to-integer/)  
  match、模式匹配

## 7. 其它基础题【完成】
- [21. 合并两个有序链表](https://leetcode.cn/problems/merge-two-sorted-lists/)  
  Option、Box、所有权转移
- [206. 反转链表](https://leetcode.cn/problems/reverse-linked-list/)  
  Option、Box、所有权

---

### 练习建议
- 每道题建议用Rust标准库和惯用法（如iter、map、collect、match、Option/Result等）来实现。
- 尝试用不同方式（for循环、迭代器、模式匹配）多写几遍。
- 多查官方文档，遇到所有权、借用、生命周期相关报错时，认真体会编译器提示。 