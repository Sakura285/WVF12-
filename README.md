<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%20x64-0078D4?style=for-the-badge&logo=windows&logoColor=white" alt="Windows" />
  <img src="https://img.shields.io/badge/WeChat-MiniProgram-07C160?style=for-the-badge&logo=wechat&logoColor=white" alt="WeChat" />
  <img src="https://img.shields.io/badge/DevTools-CDP-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white" alt="CDP" />
  <img src="https://img.shields.io/badge/MCP-Ready-7C3AED?style=for-the-badge" alt="MCP" />
</p>

<h1 align="center">WVF12</h1>

<p align="center">
  <b>PC 微信小程序强开 F12</b><br/>
  把微信私有调试通道桥到标准 Chrome DevTools，并支持 MCP 自动化分析
</p>

<p align="center">
  <a href="https://github.com/Sakura285/WVF12-/releases/latest"><img src="https://img.shields.io/github/v/release/Sakura285/WVF12-?style=flat-square&color=brightgreen" alt="release" /></a>
  <a href="https://github.com/Sakura285/WVF12-/releases/latest"><img src="https://img.shields.io/github/downloads/Sakura285/WVF12-/total?style=flat-square" alt="downloads" /></a>
  <img src="https://img.shields.io/badge/license-GPL--2.0-blue?style=flat-square" alt="license" />
</p>

---

## ✨ 能做什么

| 能力 | 说明 |
|------|------|
| 🔓 **强开调试** | 强制开启 PC 微信小程序远程调试（F12） |
| 🧭 **DevTools** | 用 Chrome / Edge 看 Console / Sources / Network / Storage |
| 🤝 **人机并行** | DevTools 手工分析 + MCP 自动分析可同时进行 |
| 🤖 **MCP** | 对接 Claude / Cursor / Grok 等，执行 JS、拉脚本、抓网络 |
| 📊 **操作台** | 浏览器实时看 MCP 调用日志 |

---

## 📦 下载

> 本仓库为**发行页**，不包含源码。请从 Releases 下载便携包。

<p align="center">
  <a href="https://github.com/Sakura285/WVF12-/releases/latest/download/WMPFDebugger-portable.zip">
    <img src="https://img.shields.io/badge/⬇️%20下载%20WMPFDebugger--portable.zip-238636?style=for-the-badge" alt="Download ZIP" />
  </a>
</p>

- 最新 Release：https://github.com/Sakura285/WVF12-/releases/latest  
- 资源文件：`WMPFDebugger-portable.zip`（约 89MB）

---

## 🚀 使用步骤

1. **解压** zip 到短路径，例如 `D:\WVF12\`  
   - 不要放在微信聊天文件等超长目录里直接运行  
2. 双击 **`WMPFDebugger.exe`**（或 `Start.bat`）  
3. 在 **PC 微信**里打开要调试的小程序  
4. 用 **Chrome / Edge** 打开窗口打印的地址，例如：  
   ```text
   devtools://devtools/bundled/inspector.html?ws=127.0.0.1:62000
   ```
5. （可选）再开 **`WMPF-MCP.exe`** 做自动化  
   - 操作台：http://127.0.0.1:17890/console  
   - MCP：http://127.0.0.1:17890/mcp  

> ⚠️ **必须保留解压后的 `app\` 目录**，不要只拷贝 exe。

### 目录结构

```text
WMPFDebugger-portable\
├── WMPFDebugger.exe     # 强开主程序
├── WMPF-MCP.exe         # MCP 服务
├── Start.bat            # 命令行启动强开
├── StartMCP.bat         # 命令行启动 MCP
├── app\                 # 运行时（必带）
└── README.txt
```

---

## 🔌 MCP 说明

| 模式 | 地址 |
|------|------|
| Streamable HTTP | `http://127.0.0.1:17890/mcp` |
| SSE | `http://127.0.0.1:17890/sse` |
| 操作台 UI | http://127.0.0.1:17890/console |

常用能力：`evaluate`（逻辑层）、`list_scripts` / `dump_scripts`、`network_enable` / `network_get` / `network_export`、`storage_get` 等。

**推荐并行用法**

1. 先开 `WMPFDebugger.exe` + 小程序  
2. 再开 Chrome DevTools  
3. 再开 `WMPF-MCP.exe`  
4. 打开操作台看调用日志  

---

## 💻 环境要求

- Windows 10 / 11 **x64**  
- 已登录的 PC 微信  
- 杀软可能拦截 Frida：请将解压目录加入白名单  

---

## ❓ 常见问题

| 问题 | 处理 |
|------|------|
| 杀软删除 / 报毒 | 目录加白后重新解压 |
| 提示 9421 占用 | 已有实例在跑，关掉旧窗口 |
| bat 乱码 | 直接用 exe 或 `Start.bat` |
| MCP 网络为空 | 先 `network_enable`，在小程序里点页面，再 `network_get` |
| DevTools 与 MCP 抢连接 | 新版已支持多客户端并行；请使用本 Release 包 |

---

## ⚠️ 免声明

本工具仅供**学习、授权安全研究与合法调试**。  
请确保你对目标小程序拥有相应权限，并遵守法律法规与微信平台条款。滥用后果自负。

---

## 📄 License

[GPL-2.0](./LICENSE)