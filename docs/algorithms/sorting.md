# 快速排序

快速排序（Quick Sort）是一种高效的排序算法，平均时间复杂度为 O(n log n)。

---

## 算法思想

**分治策略**：
1. 选择一个基准元素（pivot）
2. 将数组分成两部分：小于 pivot 和大于 pivot
3. 递归排序两部分

---

## 算法步骤

```
原始数组：[3, 6, 8, 10, 1, 2, 1]

第 1 轮（pivot=3）：
  小于 3：[1, 2, 1]
  等于 3：[3]
  大于 3：[6, 8, 10]
  
第 2 轮：
  对 [1, 2, 1] 排序 → [1, 1, 2]
  对 [6, 8, 10] 排序 → [6, 8, 10]
  
结果：[1, 1, 2, 3, 6, 8, 10]
```

---

## 代码实现

### 标准写法

```cpp
#include <bits/stdc++.h>
using namespace std;

void quickSort(int arr[], int left, int right) {
    if (left >= right) return;
    
    // 选择基准（这里选中间元素）
    int pivot = arr[(left + right) / 2];
    int i = left, j = right;
    
    while (i <= j) {
        // 找到左边大于等于 pivot 的元素
        while (arr[i] < pivot) i++;
        // 找到右边小于等于 pivot 的元素
        while (arr[j] > pivot) j--;
        
        if (i <= j) {
            swap(arr[i], arr[j]);
            i++;
            j--;
        }
    }
    
    // 递归排序左右两部分
    quickSort(arr, left, j);
    quickSort(arr, i, right);
}

int main() {
    int arr[] = {3, 6, 8, 10, 1, 2, 1};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    quickSort(arr, 0, n - 1);
    
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    // 输出：1 1 2 3 6 8 10
    
    return 0;
}
```

### STL 写法（竞赛推荐）

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> a(n);
    
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    
    // 使用 STL sort（内部用快速排序优化）
    sort(a.begin(), a.end());
    
    for (int x : a) {
        cout << x << " ";
    }
    
    return 0;
}
```

### 降序排序

```cpp
// 方法 1：使用 greater
sort(a.begin(), a.end(), greater<int>());

// 方法 2：自定义比较函数
sort(a.begin(), a.end(), [](int a, int b) {
    return a > b;
});
```

### 结构体排序

```cpp
struct Student {
    string name;
    int score;
};

// 按分数降序，分数相同按名字升序
bool cmp(const Student& a, const Student& b) {
    if (a.score != b.score) return a.score > b.score;
    return a.name < b.name;
}

vector<Student> students;
sort(students.begin(), students.end(), cmp);
```

---

## 时间复杂度分析

| 情况 | 时间复杂度 | 说明 |
|------|-----------|------|
| 最好 | O(n log n) | 每次 pivot 正好在中间 |
| 平均 | O(n log n) | 随机数据 |
| 最坏 | O(n²) | 数组已有序，pivot 选最值 |

**空间复杂度**：O(log n)（递归栈空间）

---

## 优化技巧

### 1. 随机选择 pivot

```cpp
#include <random>

void quickSort(int arr[], int left, int right) {
    if (left >= right) return;
    
    // 随机选择 pivot
    int randomIndex = left + rand() % (right - left + 1);
    swap(arr[randomIndex], arr[(left + right) / 2]);
    
    int pivot = arr[(left + right) / 2];
    // ...
}
```

### 2. 三数取中

```cpp
int medianOfThree(int arr[], int left, int right) {
    int mid = (left + right) / 2;
    if (arr[left] > arr[mid]) swap(arr[left], arr[mid]);
    if (arr[left] > arr[right]) swap(arr[left], arr[right]);
    if (arr[mid] > arr[right]) swap(arr[mid], arr[right]);
    return arr[mid];
}
```

### 3. 小数组用插入排序

```cpp
void quickSort(int arr[], int left, int right) {
    // 小数组用插入排序
    if (right - left <= 10) {
        insertionSort(arr, left, right);
        return;
    }
    // ...
}
```

---

## 相关题目

| 题目 | 来源 | 难度 |
|------|------|------|
| P1177 【模板】快速排序 | 洛谷 | 入门 |
| P1923 【深基9.例4】求第 k 小的数 | 洛谷 | 普及- |
| P1093 [NOIP2007 普及组] 奖学金 | 洛谷 | 普及- |

---

## 总结

- 快速排序是竞赛中最常用的排序算法
- 实际比赛中直接用 `sort()` 即可
- 理解原理有助于解决第 k 大/小等问题
- 最坏情况 O(n²)，可以通过随机化避免
