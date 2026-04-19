# 基础模板

竞赛中最基础、最常用的代码模板。

---

## 1. 万能头文件模板

```cpp
#include <bits/stdc++.h>
using namespace std;

// 类型别名
typedef long long ll;
typedef unsigned long long ull;
typedef pair<int, int> pii;
typedef pair<ll, ll> pll;

// 常量定义
const int INF = 0x3f3f3f3f;
const ll LINF = 0x3f3f3f3f3f3f3f3f3f;
const int MOD = 1e9 + 7;
const double EPS = 1e-8;
const double PI = acos(-1.0);

// 快速 IO
inline void io() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);
}

int main() {
    io();
    
    // 多组数据
    int T = 1;
    cin >> T;
    while (T--) {
        // 解题代码
    }
    
    return 0;
}
```

---

## 2. 快速读入模板

### 整数读入

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

### 支持 long long

```cpp
inline ll read() {
    ll x = 0, f = 1;
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
```

---

## 3. 快速输出模板

```cpp
inline void write(int x) {
    if (x < 0) {
        putchar('-');
        x = -x;
    }
    if (x > 9) write(x / 10);
    putchar(x % 10 + '0');
}

inline void writeln(int x) {
    write(x);
    putchar('\n');
}

// 使用
write(ans);
putchar(' ');
writeln(ans);
```

---

## 4. 数组初始化模板

```cpp
// 一维数组初始化
memset(a, 0, sizeof(a));        // 置 0
memset(a, 0x3f, sizeof(a));     // 置 INF (约 1e9)
memset(a, -1, sizeof(a));       // 置 -1
fill(a, a + n, INF);            // 填充指定值

// 二维数组初始化
memset(dp, 0x3f, sizeof(dp));
```

---

## 5. 常用宏定义

```cpp
// 容器操作
#define pb push_back
#define mp make_pair
#define fi first
#define se second
#define all(x) (x).begin(), (x).end()
#define sz(x) (int)(x).size()

// 循环宏
#define rep(i, a, b) for (int i = (a); i < (b); ++i)
#define per(i, a, b) for (int i = (b) - 1; i >= (a); --i)
#define fore(i, x) for (auto &i : x)

// 调试宏
#ifdef LOCAL
#define debug(x) cout << #x << " = " << x << endl
#define debug2(x, y) cout << #x << " = " << x << ", " << #y << " = " << y << endl
#else
#define debug(x)
#define debug2(x, y)
#endif
```

---

## 6. 二分查找模板

### 查找第一个 ≥ target 的位置

```cpp
int lowerBound(vector<int>& nums, int target) {
    int left = 0, right = nums.size();
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    return left;
}
```

### 查找第一个 > target 的位置

```cpp
int upperBound(vector<int>& nums, int target) {
    int left = 0, right = nums.size();
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] <= target) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    return left;
}
```

---

## 7. 离散化模板

```cpp
vector<int> discrete(vector<int>& a) {
    vector<int> sorted = a;
    sort(all(sorted));
    sorted.erase(unique(all(sorted)), sorted.end());
    
    vector<int> res;
    for (int x : a) {
        res.pb(lower_bound(all(sorted), x) - sorted.begin() + 1);
    }
    return res;
}
```

---

## 8. 高精度模板（简化版）

```cpp
struct BigInt {
    vector<int> digits;  // 低位在前
    
    BigInt(string s = "0") {
        for (int i = s.size() - 1; i >= 0; i--) {
            digits.pb(s[i] - '0');
        }
        trim();
    }
    
    void trim() {
        while (digits.size() > 1 && digits.back() == 0) {
            digits.pop_back();
        }
    }
    
    BigInt operator+(const BigInt& other) const {
        BigInt res;
        res.digits.clear();
        int carry = 0;
        for (int i = 0; i < max(digits.size(), other.digits.size()) || carry; i++) {
            int sum = carry;
            if (i < digits.size()) sum += digits[i];
            if (i < other.digits.size()) sum += other.digits[i];
            res.digits.pb(sum % 10);
            carry = sum / 10;
        }
        return res;
    }
    
    string toString() const {
        string s;
        for (int i = digits.size() - 1; i >= 0; i--) {
            s += char(digits[i] + '0');
        }
        return s;
    }
};
```

---

## 9. 日期计算模板

```cpp
// 判断闰年
bool isLeap(int year) {
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}

// 每月天数
int daysInMonth[] = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

// 计算从公元 1 年 1 月 1 日到指定日期的天数
int dayCount(int year, int month, int day) {
    int res = 0;
    for (int y = 1; y < year; y++) {
        res += isLeap(y) ? 366 : 365;
    }
    for (int m = 1; m < month; m++) {
        res += daysInMonth[m];
        if (m == 2 && isLeap(year)) res++;
    }
    res += day;
    return res;
}

// 计算两个日期之间的天数
dateDiff(int y1, int m1, int d1, int y2, int m2, int d2) {
    return abs(dayCount(y2, m2, d2) - dayCount(y1, m1, d1));
}
```

---

## 10. 常用函数模板

```cpp
// 最大公约数
int gcd(int a, int b) {
    return b ? gcd(b, a % b) : a;
}

// 最小公倍数
int lcm(int a, int b) {
    return a / gcd(a, b) * b;
}

// 快速幂
ll qpow(ll a, ll b, ll mod) {
    ll res = 1;
    a %= mod;
    while (b) {
        if (b & 1) res = res * a % mod;
        a = a * a % mod;
        b >>= 1;
    }
    return res;
}

// 判断质数
bool isPrime(int n) {
    if (n < 2) return false;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) return false;
    }
    return true;
}
```

---

## 使用建议

1. **理解原理**：不要死记硬背
2. **熟练默写**：比赛时能快速写出
3. **个性化**：根据自己的习惯调整
4. **定期复习**：保持熟练度
