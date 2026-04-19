# C++ 基础

C++ 是信息学竞赛的主要编程语言，具有高效、灵活、功能强大的特点。

---

## 为什么选 C++？

| 特性 | 说明 |
|------|------|
| **执行效率高** | 编译型语言，运行速度接近底层 |
| **STL 丰富** | 标准模板库提供大量现成数据结构 |
| **竞赛标准** | NOI、NOIP、CSP 等官方指定语言 |
| **社区庞大** | 资料丰富，题解众多 |

---

## 本章节内容

1. [环境配置](environment.md) - 安装编译器和 IDE
2. [基础语法](basic-syntax.md) - 变量、运算符、表达式
3. [数据类型](data-types.md) - 整型、浮点、字符、布尔
4. [控制结构](control-flow.md) - 条件、循环、跳转
5. [函数](functions.md) - 定义、调用、参数、递归
6. [数组与字符串](arrays-strings.md) - 一维、多维数组
7. [指针与引用](pointers-references.md) - 内存地址操作
8. [结构体与类](struct-class.md) - 自定义数据类型
9. [STL 概述](stl-overview.md) - 标准模板库介绍
10. [STL Vector](stl-vector.md) - 动态数组
11. [STL String](stl-string.md) - 字符串处理
12. [STL Map/Set](stl-map-set.md) - 关联容器
13. [STL Queue/Stack](stl-queue-stack.md) - 队列和栈
14. [输入输出优化](io-optimization.md) - 加速 IO 技巧

---

## 快速开始

### Hello World

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, OI!" << endl;
    return 0;
}
```

### 基本框架

```cpp
#include <bits/stdc++.h>  // 万能头文件
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    
    // 你的代码
    
    return 0;
}
```

---

## 学习建议

1. **先掌握基础语法**，再学 STL
2. **多写代码**，不要只看
3. **理解内存模型**，特别是指针部分
4. **养成好习惯**：变量命名规范、代码缩进、注释

---

## 常见问题

**Q: 可以用 Python 参加信奥吗？**

A: CSP-J/S 入门组可以用 Python，但提高组只能用 C++。建议直接学 C++。

**Q: 需要学 C 语言吗？**

A: 不需要，直接学 C++。C++ 完全兼容 C，且功能更强大。

**Q: 多久能学会 C++ 基础？**

A: 每天 2 小时，1-2 个月可以掌握基础语法和 STL。
