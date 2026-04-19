# 时间复杂度

时间复杂度用于衡量算法运行时间随数据规模增长的变化趋势，是评价算法效率的重要指标。

---

## 为什么需要时间复杂度？

同样的问题，不同的算法效率可能天差地别：

| 算法 | n=10 | n=100 | n=1000 |
|------|------|-------|--------|
| O(n) | 10 | 100 | 1000 |
| O(n²) | 100 | 10,000 | 1,000,000 |
| O(2ⁿ) | 1024 | ≈10³⁰ | 天文数字 |

---

## 大 O 表示法

**定义**：T(n) = O(f(n)) 表示当 n 足够大时，T(n) 的增长速度不超过 f(n)。

**特点**：
- 只保留最高阶项
- 忽略常数系数
- 关注最坏情况

### 常见时间复杂度

```
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)
常数   对数      线性      线性对数      平方      立方      指数      阶乘
```

---

## 各类复杂度详解

### O(1) - 常数时间

```cpp
// 访问数组元素
int a[100];
int x = a[5];  // O(1)

// 数学计算
int sum = n * (n + 1) / 2;  // O(1)
```

### O(log n) - 对数时间

```cpp
// 二分查找
int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
// 每次循环范围减半，时间复杂度 O(log n)
```

### O(n) - 线性时间

```cpp
// 遍历数组
for (int i = 0; i < n; i++) {
    cout << a[i] << endl;
}
// 执行 n 次，O(n)
```

### O(n log n) - 线性对数时间

```cpp
// 快速排序、归并排序
// 分治思想，每次分成两半，每半 O(n)
```

### O(n²) - 平方时间

```cpp
// 双重循环
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // 操作
    }
}
// n × n = n²，O(n²)

// 冒泡排序
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n - i - 1; j++) {
        if (a[j] > a[j+1]) swap(a[j], a[j+1]);
    }
}
```

### O(2ⁿ) - 指数时间

```cpp
// 子集枚举
void dfs(int idx) {
    if (idx == n) {
        // 处理一个子集
        return;
    }
    // 选
    dfs(idx + 1);
    // 不选
    dfs(idx + 1);
}
// 每个元素选/不选，2ⁿ 个子集
```

---

## 复杂度分析技巧

### 1. 单层循环

```cpp
for (int i = 0; i < n; i++) { }  // O(n)
for (int i = 0; i < n; i += 2) { }  // O(n)，常数忽略
```

### 2. 嵌套循环

```cpp
// 独立循环
for (int i = 0; i < n; i++) { }      // O(n)
for (int j = 0; j < m; j++) { }      // O(m)
// 总复杂度：O(n + m)

// 嵌套循环
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) { }  // O(n × m)
}
```

### 3. 递归

```cpp
// 斐波那契（低效）
int fib(int n) {
    if (n <= 1) return n;
    return fib(n-1) + fib(n-2);
}
// 时间复杂度：O(2ⁿ)

// 斐波那契（高效）
int fib(int n) {
    if (n <= 1) return n;
    int a = 0, b = 1;
    for (int i = 2; i <= n; i++) {
        int c = a + b;
        a = b;
        b = c;
    }
    return b;
}
// 时间复杂度：O(n)
```

---

## 竞赛中的时间限制

| 时间限制 | 推荐复杂度 | 最大数据规模 |
|---------|-----------|-------------|
| 1 秒 | O(n) | n ≤ 10⁷ |
| 1 秒 | O(n log n) | n ≤ 10⁶ |
| 1 秒 | O(n²) | n ≤ 5000 |
| 1 秒 | O(n³) | n ≤ 500 |
| 1 秒 | O(2ⁿ) | n ≤ 25 |

**经验公式**：1 秒内大约能执行 10⁸ 次简单操作。

---

## 空间复杂度

类似时间复杂度，衡量内存使用量。

```cpp
int a[1000];        // O(1)，固定大小
int a[n];           // O(n)，与输入规模相关
int a[n][n];        // O(n²)，二维数组
vector<int> dp(n);  // O(n)，动态数组
```

**竞赛注意**：通常内存限制为 256MB 或 512MB。

---

## 练习题

1. 分析以下代码的时间复杂度：
```cpp
for (int i = 1; i <= n; i *= 2) {
    for (int j = 0; j < n; j++) {
        // 操作
    }
}
```
<details>
<summary>答案</summary>
外层循环 i 每次乘 2，执行 log n 次；内层循环执行 n 次。总复杂度 O(n log n)。
</details>

2. 分析以下代码的时间复杂度：
```cpp
for (int i = 0; i < n; i++) {
    for (int j = i; j < n; j++) {
        // 操作
    }
}
```
<details>
<summary>答案</summary>
内层循环执行次数：n + (n-1) + (n-2) + ... + 1 = n(n+1)/2，复杂度 O(n²)。
</details>

---

## 总结

- 时间复杂度衡量算法效率
- 大 O 表示法关注增长趋势
- 竞赛中要根据数据规模选择合适的算法
- 1 秒 ≈ 10⁸ 次操作
