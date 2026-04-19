# 信奥知识库

信息学奥赛学习平台 - MkDocs 项目

## 项目结构

```
xinao-wiki/
├── docs/                   # 文档内容
│   ├── index.md           # 首页
│   ├── cpp/               # C++基础
│   │   ├── index.md
│   │   ├── environment.md
│   │   └── ...
│   ├── algorithms/        # 算法入门
│   │   ├── index.md
│   │   ├── complexity.md
│   │   └── sorting.md
│   ├── data-structures/   # 数据结构
│   │   └── index.md
│   ├── graph/             # 图论
│   │   └── index.md
│   ├── dp/                # 动态规划
│   │   └── index.md
│   ├── math/              # 数学基础
│   │   └── index.md
│   ├── templates/         # 代码模板
│   │   ├── index.md
│   │   └── basic-template.md
│   └── contests/          # 比赛指南
│       └── index.md
├── mkdocs.yml             # MkDocs 配置文件
├── requirements.txt       # Python 依赖
└── README.md              # 项目说明
```

## 本地预览

### 1. 安装依赖

```bash
pip install -r requirements.txt
```

### 2. 启动本地服务器

```bash
mkdocs serve
```

### 3. 访问

打开浏览器访问：`http://127.0.0.1:8000`

## 部署到 Vercel

### 1. 构建静态文件

```bash
mkdocs build
```

### 2. 部署到 Vercel

1. 将项目推送到 GitHub
2. 在 Vercel 导入项目
3. 设置构建命令：`mkdocs build`
4. 设置输出目录：`site`
5. 部署

### 3. 设置密码保护

在 Vercel 控制台 → Project Settings → Password Protection 设置访问密码

## 功能特性

- ✅ 左侧树形导航（类似菜鸟教程）
- ✅ 顶部搜索功能
- ✅ 代码高亮
- ✅ 深色/浅色模式切换
- ✅ 移动端适配
- ✅ 快速导航

## 技术栈

- [MkDocs](https://www.mkdocs.org/) - 静态网站生成器
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) - 主题
- Python 3.8+

## 目录结构说明

| 目录 | 内容 |
|------|------|
| C++基础 | 语法、STL、输入输出优化 |
| 算法入门 | 复杂度、排序、搜索、贪心 |
| 数据结构 | 线性结构、树、堆、并查集 |
| 图论 | 存储、遍历、最短路、生成树 |
| 动态规划 | 背包、区间 DP、树形 DP |
| 数学基础 | 质数、GCD、快速幂、组合 |
| 代码模板 | 常用代码片段 |
| 比赛指南 | CSP/NOIP 介绍、策略 |

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License
