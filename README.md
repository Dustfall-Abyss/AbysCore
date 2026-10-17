#AbysCore
# 🛠️ Dust's CTF Toolkit (多功能极客终端)

![Python](https://img.shields.io/badge/Python-3.7%2B-blue?logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20Windows%20%7C%20Linux-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![GitHub](https://img.shields.io/badge/GitHub-Dust%20fall%20abyss-black?logo=github)

这是一个基于 Python 编写的轻量级命令行终端工具，专为 CTF 比赛、网络安全日常测试以及极客开发设计。支持在手机端（如 Pydroid 3）和 PC 端流畅运行，集成了文件分析、编码转换、密码学、网络下载等常用功能。

## ✨ 核心特性

*   **🎨 极客视觉**：全终端颜色高亮（错误红、警告黄、成功绿、目录蓝），原生 Linux 风格交互。
*   **🧠 智能指纹分析**：直接粘贴无指令密文，自动识别并尝试解码（Base64/Hex/URL/摩斯密码等）。
*   **📦 文件深度解剖**：支持文件头（Magic Number）真实类型识别，以及 ZIP 压缩包的伪加密检测、尾部隐写检测、敏感文件审查。
*   **⚡ 多线程高速下载**：内置 8 线程分段下载器，支持断点级别的高速拉取网络文件。
*   **📁 原生目录操作**：内置 `ls` 和 `cd` 命令，支持动态终端提示符。
*   **📝 自动日志系统**：错误和异常自动记录至 `Log/` 目录。

---

## 🚀 快速开始

### 1. 环境依赖
请确保你的 Python 版本在 **3.7+**。本项目依赖以下第三方库：

```bash
pip install colorama
pip install requests
```

(注：requests 仅用于多线程下载功能，如果你不需要下载功能，可以不安装)

2. 运行程序

将代码保存为 tool.py，在终端中运行：

```bash
python tool.py
```

---

📖 指令手册

在启动后，输入 help 可以随时查看指令菜单。当前文件夹的名字会作为左侧的提示符（如 Log > ）。

📁 基础与文件系统

指令 功能说明
ls [路径] 列出目录内容（蓝色为文件夹，黄色为隐藏文件）
cd <路径> 切换当前工作目录（支持 cd .. 返回上级）
file <路径> 识别文件的真实类型（防修改后缀）
zip <路径> ZIP 深度分析（伪加密标志位检测 / 尾部隐写检测 / 敏感文件内查）
download <URL> [文件名] 多线程高速下载网络文件
exit / quit 退出程序

🔐 哈希计算 (Hash)

指令 功能说明
hash <算法> <内容> 计算文本哈希 (支持 md5, sha1, sha256, sha512)
hash file <算法> <路径> 计算文件哈希（大文件分块读取防溢出）

🧬 编码与解码 (Codec)

指令 功能说明
encode <类型> <内容> 进行编码转换
decode <类型> <内容> 进行解码转换

支持类型：base64, url, hex, rot13, atbash, morse

🔑 古典密码 (Classic Cipher)

指令 功能说明
encode caesar <数字> <内容> 凯撒密码加密（数字为位移量）
decode caesar <数字> <内容> 凯撒密码解密
encode fence <数字> <内容> 栅栏密码加密（数字为栏数）
decode fence <数字> <内容> 栅栏密码解密

---

🧠 智能指纹分析 (Smart Analyze)

如果你遇到一段不明的密文，无需输入任何指令，直接将其粘贴进终端并回车。

示例：
输入 666c61677b746573747d 
程序会自动判断为 Hex 编码，并输出尝试解码的结果。

限制：长度在 1~4 个字符的输入会被直接判定为无效指令。

---

📂 日志管理

所有系统级别的异常和强制中断都会被捕获，并自动在当前目录下生成一份日志：

```text
Log/
 └── 20261017_142530/
      └── latest.log
```

---

👨‍💻 作者

Dust fall abyss (aka Dust)

RHVzdCBpbiB0aGUgY29kZSwgZXllcyBvbiB0aGUgYWJ5c3Mu

```
