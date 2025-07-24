# LeetCode Rust 练习题清单（简单题）

> 针对 Rust 语法练习的 LeetCode 简单题目推荐，重点在于熟悉标准库、所有权、迭代器等 Rust 特性

---

## 🔹 1. 数组与向量（Vec）【完成】

| 题号 | 题目 | 说明 |
|------|------|------|
| 1 | [两数之和](https://leetcode.cn/problems/two-sum/) | 使用 HashMap 存储值和索引 |
| 26 | [删除有序数组中的重复项](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/) | 向量去重、双指针思想 |
| 88 | [合并两个有序数组](https://leetcode.cn/problems/merge-sorted-array/) | 合并两个有序数组 |
| 121 | [买卖股票的最佳时机](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock/) | 最大差值问题 |
| 217 | [存在重复元素](https://leetcode.cn/problems/contains-duplicate/) | 使用 HashSet 判断重复 |

---

## 🔹 2. 字符串（String / &str）【完成】

| 题号 | 题目 | 说明 |
|------|------|------|
| 344 | [反转字符串](https://leetcode.cn/problems/reverse-string/) | 原地反转字符数组 |
| 387 | [字符串中的第一个唯一字符](https://leetcode.cn/problems/first-unique-character-in-a-string/) | 使用 HashMap 统计频率 |
| 13 | [罗马数字转整数](https://leetcode.cn/problems/roman-to-integer/) | 字符串解析、匹配映射 |
| 14 | [最长公共前缀](https://leetcode.cn/problems/longest-common-prefix/) | 多字符串比较 |
| 20 | [有效的括号](https://leetcode.cn/problems/valid-parentheses/) | 栈结构模拟（可用 Vec） |

---

## 🔹 3. 条件判断与控制流【完成】

| 题号 | 题目 | 说明 |
|------|------|------|
| 27 | [移除元素](https://leetcode.cn/problems/remove-element/) | 条件过滤、保留元素 |
| 66 | [加一](https://leetcode.cn/problems/plus-one/) | 数组进位操作 |
| 169 | [多数元素](https://leetcode.cn/problems/majority-element/) | HashMap 或 Boyer-Moore 投票算法 |
| 283 | [移动零](https://leetcode.cn/problems/move-zeroes/) | 双指针移动元素 |

---

## 🔹 4. 枚举、Option 和 Result【完成】

| 题号 | 题目 | 说明 |
|------|------|------|
| 70 | [爬楼梯](https://leetcode.cn/problems/climbing-stairs/) | 动态规划入门 |
| 191 | [位1的个数](https://leetcode.cn/problems/number-of-1-bits/) | 位运算 + 迭代计数 |
| 231 | [2的幂](https://leetcode.cn/problems/power-of-two/) | 位运算判断幂次 |
| 326 | [3的幂](https://leetcode.cn/problems/power-of-three/) | 循环或递归实现 |

---

## 🔹 5. 函数式编程风格（迭代器）【完成】

| 题号 | 题目 | 说明 |
|------|------|------|
| 1 | [两数之和](https://leetcode.cn/problems/two-sum/) | 可尝试用 `.enumerate()` + HashMap |
| 219 | [存在重复元素II](https://leetcode.cn/problems/contains-duplicate-ii/) | HashMap + 索引距离判断 |
| 118 | [杨辉三角](https://leetcode.cn/problems/pascals-triangle/) | 构造二维 Vec |
| 119 | [杨辉三角II](https://leetcode.cn/problems/pascals-triangle-ii/) | 优化空间版本 |

---

## 📌 练习建议

### 1. 优先使用迭代器风格
- 尽量避免手动 for 循环
- 多用 `.iter()`、`.map()`、`.filter()`、`.fold()`、`.collect()`

### 2. 善用 Option/Result
- 不要轻易 `.unwrap()`，尝试用 `match` 或 `if let`
- 学会使用 `?` 在函数中传播错误

### 3. 注意所有权转移
- 函数参数是否需要 `&Vec<T>` 而不是 `Vec<T>`
- 返回值是否可以借用而非克隆

### 4. 熟悉常见 trait
- `Debug`、`Clone`、`Copy`、`PartialEq` 等

### 5. 写测试
- 每道题都可以加上 `#[cfg(test)] mod tests` 来验证逻辑正确性

---

## 🧪 示例代码（两数之和）

```rust
use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut map = HashMap::new();
        for (i, &num) in nums.iter().enumerate() {
            let complement = target - num;
            if let Some(&j) = map.get(&complement) {
                return vec![j as i32, i as i32];
            }
            map.insert(num, i);
        }
        vec![] // unreachable in valid input
    }
}
```