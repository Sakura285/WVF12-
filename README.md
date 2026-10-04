# WMPFDebugger（便携版）

PC 微信小程序 **强开 F12** 工具的**已打包发行版**（Windows x64）。

本仓库**仅提供可执行包**，不含源码。

> 仅用于你有权调试的小程序与授权安全研究。请遵守法律法规与微信平台条款。  
> 含 Frida 注入引擎，杀软可能误报，请将解压目录加入白名单。

## 下载

- **推荐**：[`WMPFDebugger-portable.zip`](./WMPFDebugger-portable.zip)  
- 可选单文件：[`WMPFDebugger-onefile.exe`](./WMPFDebugger-onefile.exe)（首次运行会自解压到 `%LOCALAPPDATA%\WMPFDebugger-onefile\`）

## 使用（便携包）

1. 下载并解压 `WMPFDebugger-portable.zip` 到**短路径**（例如 `D:\WMPF\`）  
   - 不要放在微信聊天文件等超长目录里直接跑  
2. 双击 **`WMPFDebugger.exe`**（或 `Start.bat`）  
3. 在 PC 微信中打开要调试的小程序  
4. 用 Chrome / Edge 打开窗口里打印的地址，例如：  
   `devtools://devtools/bundled/inspector.html?ws=127.0.0.1:62000`  
5. （可选）再开 **`WMPF-MCP.exe`** 做 MCP 自动化  
   - 操作台：http://127.0.0.1:17890/console  
   - MCP：http://127.0.0.1:17890/mcp  

**必须保留 `app\` 目录**，不要只拷贝 exe。

## 目录说明

```text
WMPFDebugger-portable\
  WMPFDebugger.exe    # 强开主程序
  WMPF-MCP.exe        # MCP 服务
  Start.bat / StartMCP.bat
  app\                # 运行时（必带）
  README.txt
```

## 能力摘要

- 强制开启小程序远程调试（F12）  
- Chrome DevTools 看 Console / Sources / Network  
- DevTools 与 MCP **可同时连接**  
- MCP：执行逻辑层 JS、列/导出脚本、双通道网络抓取等  

## 环境

- Windows 10 / 11 x64  
- 已登录的 PC 微信  

## 常见问题

| 现象 | 处理 |
|------|------|
| 杀软拦截 | 解压目录加白名单后重试 |
| 端口 9421 占用 | 已有实例在跑，关掉旧窗口 |
| bat 乱码 | 直接用 exe 或 `Start.bat` |
| MCP 网络为空 | 先开 MCP，在小程序里点页面，再抓包 |

## 免责声明

使用者须确保对目标具备合法授权，自行承担使用风险与后果。