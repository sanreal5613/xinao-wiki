# 代码模板

竞赛中常用的代码模板，可以直接复制使用。

---

## 模板使用说明

1. **理解原理**：不要死记硬背，要理解每行代码的作用
2. **个性化修改**：根据自己的习惯调整变量名、注释等
3. **熟练默写**：比赛时能快速写出，不需要翻模板

---

## 模板分类

- [基础模板](basic-template.md) - 万能头文件、快速 IO
- [数据结构模板](data-structure-templates.md) - 并查集、线段树等
- [图论模板](graph-templates.md) - 最短路、最小生成树等
- [动态规划模板](dp-templates.md) - 背包、区间 DP 等
- [数学模板](math-templates.md) - 质数、GCD、快速幂等

---

## 万能头文件

```cpp
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
typedef pair<int, int> pii;
typedef pair<ll, ll> pll;

const int INF = 0x3f3f3f3f;
const ll LINF = 0x3f3f3f3f3f3f3f3f3f;
const int MOD = 1e9 + 7;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    
    // 你的代码
    
    return 0;
}
```

---

## 快速读入

```cpp
inline int read() {
    int x = 0, f = 1;
    char ch = getchar();
    while (ch < '0' || ch > '9') {
        if (ch == '-') f = -1;
        ch = getchar();
    }
    while (ch >= '0' && ch <= '9') {
        x = x * 10 + ch - '0';
        ch = getchar();
    }
    return x * f;
}

// 使用
int n = read();
```

---

## 快速输出

```cpp
inline void write(int x) {
    if (x < 0) {
        putchar('-');
        x = -x;
    }
    if (x > 9) write(x / 10);
    putchar(x % 10 + '0');
}

// 使用
write(ans);
putchar('\n');
```

---

## 常用宏定义

```cpp
#define pb push_back
#define mp make_pair
#define fi first
#define se second
#define all(x) (x).begin(), (x).end()
#define sz(x) (int)(x).size()
#define rep(i, a, b) for (int i = (a); i < (b); ++i)
#define per(i, a, b) for (int i = (b) - 1; i >= (a); --i)
```

---

## 调试技巧

```cpp
#ifdef LOCAL
#define debug(x) cout << #x << " = " << x << endl
#else
#define debug(x)
#endif

// 使用
debug(n);
debug(ans);
```

---

## 注意事项

1. **数组大小**：开够，但不要开太大（内存限制）
2. **数据类型**：注意 `int` 和 `long long` 的选择
3. **初始化**：数组、变量记得初始化
4. **边界条件**：特别注意 0、1、n 等边界
5. **取模**：负数取模要先加 MOD

---

## 比赛检查清单

- [ ] 头文件是否完整
- [ ] 数组大小是否足够
- [ ] 数据类型是否正确
- [ ] 是否开启快速 IO
- [ ] 多组数据是否清空数组
- [ ] 输出格式是否正确
- [ ] 是否考虑特殊情况
