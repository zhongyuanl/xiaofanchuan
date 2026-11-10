<div align="center">

<img src="docs/images/app-logo.png" alt="小帆船 Little Sailboat" width="112" height="112" />

# 小帆船 · Little Sailboat

Claude 与 Claude Code 的网络环境管理和启动控制台

[![macOS](https://img.shields.io/badge/macOS-v2.0.3-007AFF?style=flat-square&logo=apple)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v2.0.3)
[![Windows](https://img.shields.io/badge/Windows-v1.3.23-0078D6?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.23)

[简体中文](README.md) · [English](README.en.md) · [使用指南](docs/使用指南.md) · [反馈问题](https://github.com/zhongyuanl/xiaofanchuan/issues)

</div>

## v2.0.3 更新

本次更新面向 macOS。Windows 当前公开版本为 v1.3.23，两个平台按各自版本下载。

- **系统代理一键修复**。外部 VPN 开关已打开、小帆船仍提示系统代理未开启时，可直接点击“修复系统代理”。按当前联网服务识别 Wi-Fi、网线或 USB 网卡，使用已保存的本地端口，写入后读回设置并测试连接。
- **外部客户端适配**。系统代理状态依据 macOS 当前生效设置读取，“打开客户端”遵循已选择的应用。
- **原生界面更新**。通行页集中呈现代理环境、安全护航和三端启动入口，环境页管理订阅源、节点与连接方式，设置页提供设置助理。

## 下载

| 平台 | 版本 | 安装包 | 要求 |
| --- | --- | --- | --- |
| macOS | **v2.0.3** | [DMG 安装包](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.dmg) · [ZIP 压缩包](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.zip) | Apple Silicon，macOS 13 或更高版本 |
| Windows | v1.3.23 | [EXE](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.exe) · [ZIP](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.zip) | Windows 10/11 x64 |

macOS 打开 DMG 后，将“小帆船”拖入 Applications。升级前先退出旧版并保存正在运行的任务。安装包采用 ad-hoc 签名，尚未进行 Apple 公证。下载后可用发布页的 SHA-256 清单核对文件。[校验清单](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/SHA256SUMS.txt)

## 界面预览

下图使用新版界面截图，订阅源、节点、账号及出口地址已经过图像脱敏编辑，展示为示例数据。

### 通行

查看当前出口和运行状态，从同一页面进入 Claude 桌面端、专用浏览器或命令行终端。

![通行页，账号、节点和出口地址已脱敏](docs/images/passage.png?v=2.0.3)

### 代理环境

管理多个订阅源，选择节点和内置或外部代理。图中的“示例订阅 A/B/C”为脱敏名称。

![代理环境，订阅源已替换为中性示例名](docs/images/environment-proxy.png?v=2.0.3)

### 设置

调整外观、语言、开机自启动，并通过设置助理重新配置必要选项。

![设置页，账号信息已脱敏](docs/images/settings.png?v=2.0.3)

## 外部 VPN 的系统代理怎么修复

1. 在所用 VPN 客户端中连接节点，确认其本地 **HTTP 或混合代理端口**。
2. 在小帆船的“环境 → 代理环境 → 外部代理”中选择客户端，填写并保存端口。
3. 如果“系统代理配置”显示未开启，点击 **修复系统代理**，按 macOS 提示授权。
4. 查看修复结果。权限不足、端口不通、网络切换或设置被其他应用覆盖时，界面会说明下一步操作。

修复会更新当前联网服务的 HTTP/HTTPS 代理；同端口通过 SOCKS 测试时也会配置 SOCKS。原有绕过列表保留，当前服务的 PAC 与自动代理发现会关闭。修复结果通过设置读回和连接探针核对。

## 使用范围与验证情况

小帆船提供内置代理、外部客户端接入、出口观测、地区环境设置及受控启动入口。使用订阅源时，请自行准备有权使用的服务。网络检查、风险评分和界面状态应结合实际连接情况判断。

v2.0.3 已通过 Swift 6 编译、防回退和修复流程检查，本机只读 HTTP/SOCKS 连接测试通过。新增按钮的实际授权写入、跨电脑兼容性及端到端防泄漏仍待进一步实机验证。账号是否可用还受服务方政策和账号状态影响。

操作可能修改系统代理、语言、时区、IPv6、浏览器资料或 Claude Code 配置。执行配置或清理前查看影响范围，并保存必要备份。[使用指南](docs/使用指南.md) · [注意事项与隐私](docs/注意事项与隐私说明.md)

## 项目与许可

此仓库提供安装包、文档和第三方来源说明。完整应用的许可范围见仓库说明。截图中的示例名称用于展示界面。[许可范围](LICENSE.md)

感谢 CCBaga、Mihomo、Clash Verge Rev 及相关依赖项目。各项目的使用范围和许可分别列在来源说明中。[参考项目与许可](docs/参考项目与许可.md) · [第三方通知](THIRD_PARTY_NOTICES.txt)
