# 环境配置

搭建 C++ 开发环境，包括编译器和代码编辑器。

---

## Windows 环境

### 方法一：Dev-C++（推荐初学者）

**优点**：一键安装，开箱即用

**下载**：
- 官网：https://sourceforge.net/projects/orwelldevcpp/
- 或搜索 "Dev-C++ 下载"

**安装步骤**：
1. 下载安装包
2. 双击安装，一路下一步
3. 打开 Dev-C++，新建源文件
4. 编写代码，按 F11 编译运行

### 方法二：VS Code + MinGW（推荐）

**优点**：功能强大，插件丰富

**步骤**：

1. **下载 MinGW**（编译器）
   - 官网：https://www.mingw-w64.org/
   - 或下载离线包

2. **配置环境变量**
   ```
   将 MinGW 的 bin 目录添加到系统 PATH
   例如：C:\mingw64\bin
   ```

3. **下载 VS Code**
   - 官网：https://code.visualstudio.com/

4. **安装插件**
   - C/C++（Microsoft 官方）
   - C/C++ Extension Pack

5. **验证安装**
   ```bash
   g++ --version
   ```

---

## Mac 环境

### 安装 Xcode Command Line Tools

```bash
xcode-select --install
```

### 安装 VS Code

1. 下载：https://code.visualstudio.com/
2. 安装 C/C++ 插件

---

## Linux 环境

### Ubuntu/Debian

```bash
sudo apt update
sudo apt install g++ gdb
```

### CentOS/RHEL

```bash
sudo yum install gcc-c++ gdb
```

---

## 验证安装

创建文件 `test.cpp`：

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "环境配置成功！" << endl;
    return 0;
}
```

编译运行：

```bash
g++ test.cpp -o test
./test
```

看到 "环境配置成功！" 即表示成功。

---

## 在线编译器（临时使用）

如果本地环境还没配好，可以先用在线编译器：

- [洛谷在线 IDE](https://www.luogu.com.cn/ide)
- [Programiz](https://www.programiz.com/cpp-programming/online-compiler/)
- [OnlineGDB](https://www.onlinegdb.com/online_c++_compiler)

---

## 推荐配置

| 场景 | 推荐工具 |
|------|---------|
| 初学者 | Dev-C++ |
| 日常练习 | VS Code + MinGW |
| 比赛模拟 | 与比赛环境一致 |
| 临时使用 | 在线编译器 |

---

## 常见问题

**Q: g++ 不是内部或外部命令？**

A: 环境变量没配置好，检查 PATH 是否包含 MinGW 的 bin 目录。

**Q: 中文输出乱码？**

A: 文件保存为 UTF-8 编码，或在代码开头添加：
```cpp
#include <windows.h>
SetConsoleOutputCP(CP_UTF8);
```

**Q: 编译报错 "undefined reference"？**

A: 检查是否使用了 C++11 及以上特性，编译时加上 `-std=c++11`：
```bash
g++ -std=c++11 test.cpp -o test
```
