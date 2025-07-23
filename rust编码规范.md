# Rust 编码规范（2024）

## 1. 格式化（Formatting）
- 使用 4 个空格缩进。
- 每行建议不超过 100 个字符，必要时可适当放宽。
- 运算符、括号、花括号、冒号、逗号和关键字周围使用空格。
- 花括号采用 K&R 风格（左花括号与语句同行，右花括号单独一行）。
- 代码段落之间用一行空行分隔。
- 文档注释和参数列表建议对齐。
- 推荐使用 `rustfmt` 自动格式化代码：
  ```sh
  cargo fmt
  ```

## 2. 命名规范（Naming Conventions）
- 类型（struct、enum、trait）和枚举变体：`UpperCamelCase`（大驼峰）。
- 函数、方法、局部变量、字段、宏名：`snake_case`（小写加下划线）。
- 常量和静态变量：`SCREAMING_SNAKE_CASE`（全大写加下划线）。
- 包名：全小写，单词拼接，避免下划线。
- 避免缩写和不常见的简写，除非广泛认同（如 HTTP、XML）。
- 保持命名风格一致，优先表达清晰含义。

## 3. 注释与文档（Commenting & Documentation）
- 用注释解释代码的目的和复杂逻辑，避免重复代码本身的内容。
- 复杂算法、设计选择应有注释说明。
- 公共 API 使用文档注释（`///`），包含用途、参数、返回值、示例等。
- 示例：
  ```rust
  /// 计算一组山羊的平均体重（kg）。
  ///
  /// # 参数
  /// - `weights`: 山羊体重列表
  ///
  /// # 返回
  /// 平均体重
  pub fn average_goat_weight(weights: &[f32]) -> f32 {
      // 避免除以零
      if weights.is_empty() {
          panic!("Cannot calculate average weight for an empty herd!");
      }
      let total_weight = weights.iter().sum::<f32>();
      total_weight / weights.len() as f32
  }
  ```
- 注释风格保持一致，可用工具或 linter 检查。

## 4. 最佳实践与惯用法（Best Practices & Idioms）
### 所有权与借用
- 理解并善用所有权、借用和生命周期，避免不必要的 clone 和拷贝。
- 优先使用引用（`&`/`&mut`）传递数据。

### 模式匹配
- 善用 `match`、`if let`、`while let` 进行模式匹配，简化分支逻辑。

### 迭代器与函数式编程
- 使用迭代器链（`map`、`filter`、`fold` 等）处理集合，代码更简洁高效。

### 错误处理
- 使用 `Result` 和 `Option` 类型进行显式错误处理。
- 避免在生产代码中使用 `unwrap`、`expect`，优先用 `?` 运算符传播错误。
- 错误信息应有助于定位和调试。

### 泛型与 trait
- 利用泛型和 trait 提高代码复用性和灵活性。

### 智能指针
- 根据需要使用 `Rc`、`Arc`、`Box` 等智能指针管理复杂所有权关系。

## 5. 性能优化（Performance）
- 用引用和切片避免不必要的内存分配。
- 用迭代器代替 for 循环，减少中间集合。
- 用 `cargo-flamegraph`、`perf` 等工具分析性能瓶颈。
- 避免频繁 clone，必要时用智能指针。

## 6. 测试（Testing）
- 编写单元测试、集成测试和文档测试，保证代码正确性。
- 用 `cargo test` 运行测试。
- 示例：
  ```rust
  #[cfg(test)]
  mod tests {
      use super::*;
      #[test]
      fn test_add() {
          assert_eq!(add(2, 3), 5);
      }
  }
  ```

## 7. 工具推荐（Tools）
- `rustfmt`：官方代码格式化工具。
- `clippy`：官方静态分析和风格检查工具。
- `cargo test`：测试。
- `cargo audit`：依赖安全检查。
- `rust-analyzer`：主流 IDE 的 Rust 语言服务。
- `bacon`、`geiger` 等辅助工具。

## 8. 参考资料（References）
- [The Rust Programming Language](https://doc.rust-lang.org/book/)
- [Rust API Guidelines](https://rust-lang.github.io/api-guidelines/)
- [Rust Style Guide](https://github.com/rust-dev-tools/fmt-rfcs)
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/)
- [Clippy Lints](https://rust-lang.github.io/rust-clippy/)

---

本规范适用于团队协作和个人学习，建议结合实际项目灵活调整。 