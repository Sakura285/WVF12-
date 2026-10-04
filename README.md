# WVF12

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%20x64-0078D4?style=for-the-badge&logo=windows&logoColor=white" alt="Windows" />
  <img src="https://img.shields.io/badge/Target-WX%20MiniProgram-07C160?style=for-the-badge" alt="WX" />
  <img src="https://img.shields.io/badge/DevTools-CDP-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white" alt="CDP" />
  <img src="https://img.shields.io/badge/MCP-Ready-7C3AED?style=for-the-badge" alt="MCP" />
</p>

<h1 align="center">WVF12</h1>

<p align="center">
  <b>PC 端 WX 小程序强开 F12</b><br/>
  将私有调试通道桥接到标准 Chrome DevTools Protocol，并支持 MCP 自动化分析
</p>

<p align="center">
  <a href="https://github.com/Sakura285/WVF12-/releases/latest"><img src="https://img.shields.io/github/v/release/Sakura285/WVF12-?style=flat-square&color=brightgreen" alt="release" /></a>
  <a href="https://github.com/Sakura285/WVF12-/releases/latest"><img src="https://img.shields.io/github/downloads/Sakura285/WVF12-/total?style=flat-square" alt="downloads" /></a>
  <img src="https://img.shields.io/badge/license-GPL--2.0-blue?style=flat-square" alt="license" />
</p>

---

## Features

| 能力 | 说明 |
|------|------|
| **强开调试** | 强制开启 PC 端 WX 小程序远程调试（F12） |
| **DevTools** | 用 Chrome / Edge 查看 Console / Sources / Network / Storage |
| **并行分析** | DevTools 手工分析与 MCP 自动分析可同时进行 |
| **MCP** | 对接 Claude / Cursor / Grok 等，执行 JS、导出脚本、抓网络 |
| **操作台** | 浏览器实时查看 MCP 调用日志 |

---

## Download

> 本仓库为**发行页**，不包含源码。请从 Releases 下载便携包。

<p align="center">
  <a href="https://github.com/Sakura285/WVF12-/releases/latest/download/WMPFDebugger-portable.zip">
    <img src="https://img.shields.io/badge/Download-WMPFDebugger--portable.zip-238636?style=for-the-badge" alt="Download ZIP" />
  </a>
</p>

- Latest release: https://github.com/Sakura285/WVF12-/releases/latest
- Asset: `WMPFDebugger-portable.zip` (~89MB)

---

## Quick Start

1. 解压 zip 到短路径，例如 `D:\\WVF12\\`.
2. 不要放在聊天文件等超长目录里直接运行。
3. 双击 **`WMPFDebugger.exe`**（或 `Start.bat`）。
4. 在 PC 端 **WX** 中打开目标小程序。
5. 用 **Chrome / Edge** 打开窗口打印的地址，例如：

```text
devtools://devtools/bundled/inspector.html?ws=127.0.0.1:62000
```

6. （可选）再打开 **`WMPF-MCP.exe`** 做自动化：
   - Console UI: http://127.0.0.1:17890/console
   - MCP: http://127.0.0.1:17890/mcp

> **必须保留解压后的 `app\\` 目录**，不要只拷贝 exe。

### Package layout

```text
WMPFDebugger-portable/
├── WMPFDebugger.exe      # main debugger
├── WMPF-MCP.exe          # MCP server
├── Start.bat / StartMCP.bat
├── app/                  # runtime (required)
└── README.txt
```

---

## MCP

| Mode | Endpoint |
|------|----------|
| Streamable HTTP | `http://127.0.0.1:17890/mcp` |
| SSE | `http://127.0.0.1:17890/sse` |
| Console UI | http://127.0.0.1:17890/console |

Useful tools: `evaluate` / `list_scripts` / `dump_scripts` / `network_enable` / `network_get` / `network_export` / `storage_get` ...

**Recommended parallel workflow**

1. Start `WMPFDebugger.exe` and open a mini program in WX
2. Open Chrome DevTools
3. Start `WMPF-MCP.exe`
4. Open the console UI for live MCP logs

---

## Requirements

- Windows 10 / 11 x64
- Logged-in PC WX client
- Antivirus may flag Frida — whitelist the extracted folder

---

## FAQ

| Issue | Fix |
|------|-----|
| AV quarantine | Whitelist folder and re-extract |
| Port 9421 in use | Another instance is running; close it |
| Bat garbled | Use the `.exe` or `Start.bat` |
| Empty network capture | `network_enable` → click around in app → `network_get` |
| DevTools vs MCP conflict | This build supports multi-client CDP |

---

## Disclaimer

For learning, authorized security research, and legitimate debugging only.  
You must have proper authorization for the target, and comply with applicable laws and platform terms. Abuse is at your own risk.

---

## License

[GPL-2.0](./LICENSE)
