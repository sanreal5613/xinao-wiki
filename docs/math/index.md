# 数学基础

数学是信息学竞赛的重要基础，涉及数论、组合数学、线性代数等多个领域。

---

## 为什么学数学？

很多算法问题本质上都是数学问题：

- **数论**：密码学、哈希算法
- **组合数学**：计数问题、概率问题
- **线性代数**：矩阵快速幂、高斯消元
- **计算几何**：图形处理、碰撞检测

---

## 本章节内容

1. [质数与筛法](prime.md) - 质数判断、埃氏筛、欧拉筛
2. [GCD 与 LCM](gcd-lcm.md) - 最大公约数、最小公倍数
3. [模运算](modular.md) - 取模运算、逆元
4. [组合数学](combinatorics.md) - 排列组合、卡特兰数
5. [快速幂](fast-power.md) - 快速幂、矩阵快速幂

---

## 常用数学公式

### 数论公式

| 公式 | 说明 |
|------|------|
| gcd(a, b) × lcm(a, b) = a × b | 最大公约数与最小公倍数关系 |
| φ(n) = n × ∏(1 - 1/p) | 欧拉函数 |
| a^φ(n) ≡ 1 (mod n) | 欧拉定理 |
| a^(p-1) ≡ 1 (mod p) | 费马小定理（p 为质数） |

### 组合数学公式

| 公式 | 说明 |
|------|------|
| C(n, k) = n! / (k!(n-k)!) | 组合数 |
| C(n, k) = C(n-1, k) + C(n-1, k-1) | 组合数递推 |
| ∑C(n, k) = 2^n | 二项式定理 |
| Catalan(n) = C(2n, n) / (n+1) | 卡特兰数 |

---

## 常用算法

### 质数相关

```cpp
// 判断质数
bool isPrime(int n) {
    if (n < 2) return false;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) return false;
    }
    return true;
}

// 埃氏筛
const int MAXN = 1e6 + 5;
bool isPrime[MAXN];
vector<int> primes;

void sieve(int n) {
    memset(isPrime, true, sizeof(isPrime));
    isPrime[0] = isPrime[1] = false;
    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) {
            primes.push_back(i);
            for (int j = i * 2; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }
}
```

### GCD 与 LCM

```cpp
// 最大公约数（辗转相除法）
int gcd(int a, int b) {
    return b ? gcd(b, a % b) : a;
}

// 最小公倍数
int lcm(int a, int b) {
    return a / gcd(a, b) * b;  // 先除后乘防溢出
}
```

### 快速幂

```cpp
// 快速幂（求 a^b mod p）
long long qpow(long long a, long long b, long long p) {
    long long res = 1;
    a %= p;
    while (b) {
        if (b & 1) res = res * a % p;
        a = a * a % p;
        b >>= 1;
    }
    return res;
}
```

### 组合数计算

```cpp
const int MAXN = 1005;
const int MOD = 1e9 + 7;

long long C[MAXN][MAXN];

void initComb() {
    for (int i = 0; i < MAXN; i++) {
        C[i][0] = C[i][i] = 1;
        for (int j = 1; j < i; j++) {
            C[i][j] = (C[i-1][j] + C[i-1][j-1]) % MOD;
        }
    }
}
```

---

## 学习路线

```
基础阶段
├── 质数与筛法
├── GCD 与 LCM
└── 快速幂

进阶阶段
├── 模运算与逆元
├── 组合数学
└── 欧拉函数

高级阶段
├── 扩展欧几里得
├── 中国剩余定理
├── 矩阵快速幂
└── 高斯消元
```

---

## 经典问题

| 问题 | 算法 | 难度 |
|------|------|------|
| 质数判断 | 试除法 | ⭐ |
| 筛质数 | 埃氏筛/欧拉筛 | ⭐ |
| GCD | 辗转相除 | ⭐ |
| 快速幂 | 二进制分解 | ⭐⭐ |
| 组合数 | 递推/逆元 | ⭐⭐ |
| 逆元 | 扩展欧几里得/费马小定理 | ⭐⭐⭐ |
| 中国剩余定理 | 扩展欧几里得 | ⭐⭐⭐ |
| 矩阵快速幂 | 矩阵乘法 | ⭐⭐⭐ |

---

## 学习建议

1. **掌握基础**：质数、GCD、快速幂必须熟练
2. **理解原理**：不要只记公式，要理解推导过程
3. **注意取模**：大数运算记得取模防溢出
4. **多做练习**：数学题目需要大量练习才能掌握
5. **总结套路**：归纳常见数学问题的解法

---

## 推荐练习

| 题目 | 来源 | 类型 |
|------|------|------|
| P5736 【深基7.例2】质数筛 | 洛谷 | 质数筛 |
| P1082 [NOIP2012 提高组]同余方程 | 洛谷 | 扩展欧几里得 |
| P1226 【模板】快速幂 | 洛谷 | 快速幂 |
| P1313 [NOIP2011 计算系数] | 洛谷 | 组合数 |
| P3811 【模板】乘法逆元 | 洛谷 | 逆元 |
| P1495 【模板】中国剩余定理 | 洛谷 | CRT |

---

## 下一步

掌握基础数学后，继续学习：
- [动态规划](../dp/index.md) - 结合数学的优化
- [图论](../graph/index.md) - 网络流、匹配

数学是竞赛的基础，也是最难的部分之一。需要系统学习和大量练习！📐
