---
title: Markdown 扩展使用
date: 2025-01-22
---

# Markdown 扩展使用

> Zensical 常用 Markdown 扩展示例

本站启用的扩展都在 `zensical.toml` 的 `[project.markdown_extensions]` 中配置，下面是一些常用写法。

## 警告框

```markdown
!!! note "提示"
    这是一个提示框。

!!! warning "注意"
    这是一个警告框。
```

!!! note "提示"
    这是一个提示框。

!!! warning "注意"
    这是一个警告框。

## 可折叠内容

```markdown
??? tip "点击展开"
    这里是被折叠的内容。
```

??? tip "点击展开"
    这里是被折叠的内容。

## 内容标签页

````markdown
=== "Python"

    ```python
    print("Hello, Zensical!")
    ```

=== "Rust"

    ```rust
    println!("Hello, Zensical!");
    ```
````

=== "Python"

    ```python
    print("Hello, Zensical!")
    ```

=== "Rust"

    ```rust
    println!("Hello, Zensical!");
    ```

## 代码高亮与行号

````markdown
```python hl_lines="2"
def greet(name):
    print(f"Hello, {name}!")
```
````

```python hl_lines="2"
def greet(name):
    print(f"Hello, {name}!")
```

## 任务列表

```markdown
- [x] 已完成
- [ ] 待完成
```

- [x] 已完成
- [ ] 待完成

## 脚注

```markdown
这里有一个脚注[^1]。

[^1]: 脚注内容。
```

这里有一个脚注[^1]。

[^1]: 脚注内容。

## 键盘按键

```markdown
按下 ++ctrl+c++ 复制。
```

按下 ++ctrl+c++ 复制。

## 其他常用语法

| 语法 | 效果 |
|------|------|
| `==高亮==` | ==高亮== |
| `H~2~O` | H~2~O |
| `x^2^` | x^2^ |
| `~~删除~~` | ~~删除~~ |
| `:material-rocket:` | :material-rocket: |

更多扩展说明请参考 [Zensical 官方文档](https://zensical.org/docs/)。
