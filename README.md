# ⛵ 小帆船 · Little Sailboat

**[简体中文](README.md) | [English](README.en.md)**

让 Claude 的使用环境看得清、启动更方便。

小帆船是一款 macOS 原生的 Claude 使用环境管理工具。你可以在一个窗口中查看代理出口和连接状态，检查地区、语言与时区设置，并启动 Claude 客户端、独立浏览器或命令行。

![Version](https://img.shields.io/badge/version-1.3.19-blue) ![macOS](https://img.shields.io/badge/macOS-13%2B-lightgrey) ![Architecture](https://img.shields.io/badge/Apple_Silicon-arm64-blue)

**[下载 v1.3.19](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.19)** · [使用指南](docs/使用指南.md) · [常见问题](docs/使用指南.md#7-常见问题) · [反馈问题](https://github.com/zhongyuanl/xiaofanchuan/issues)

## 主要功能

- **查看网络状态**：集中显示代理连接、出口 IP、地区和第三方 IP 质量信息。
- **控制受控连接**：通过本地代理开关暂停或恢复经过小帆船的连接。
- **统一启动入口**：按安装情况启动 Claude、Claude Code、独立浏览器和命令行。
- **检查使用环境**：查看并按需调整地区、语言、时区和 IPv6 等设置。
- **保留设置快照**：修改 Claude Code 设置前保存副本，方便核对与恢复。

小帆船不提供代理节点、订阅或账号，也不承诺防封、解封或覆盖整台电脑的全部网络流量。请遵守所在地法律和所用服务的条款。

## 界面预览

以下为 **v1.3.16 的界面演示图**，使用固定示例数据；v1.3.19 的细节以实际应用为准。图片用于展示布局，其中的状态和分数不代表实际网络检查结果。

![通行界面演示](docs/images/passage.png)

<details>
<summary>查看设置界面</summary>

![设置界面演示](docs/images/settings.png)

</details>

## 运行在哪里？

**可以直接在 Mac 主系统上使用，也可以在 macOS 虚拟机中使用，推荐虚拟机。**

| 方式 | 怎么部署 | 适合情况 |
|---|---|---|
| macOS 虚拟机（推荐） | 将小帆船、代理客户端、浏览器和需要使用的 Claude 工具安装在同一台虚拟机内 | 希望把这套使用环境与日常系统分开，减少语言、时区和网络设置对日常工作的影响 |
| Mac 主系统（宿主机） | 直接在日常使用的 Mac 上安装，相关代理和客户端也在该系统内运行 | 希望直接使用现有桌面环境，并愿意自行管理系统设置变化 |

使用虚拟机时，请在虚拟机内设置、检查代理和网络。**宿主机代理已开启，不代表虚拟机内的代理、TUN 或系统代理已配置完成。** 虚拟机是环境分开的方式，不会自动带来匿名、账号资格或完整的网络隔离保证。

本次两种方式均要求 **Apple Silicon / arm64 macOS 环境**；Windows、Linux 虚拟机及 Intel Mac 不适用此安装包。具体虚拟化软件与系统版本组合仍需自行验证。

## 系统要求

| 项目 | 要求 |
|---|---|
| Mac | Apple 芯片（Apple Silicon / arm64），本次不提供 Intel 版 |
| 系统 | 应用声明最低 macOS 13.0；尚未完成全部系统版本的兼容性测试 |
| 代理 | 自行安装并配置代理客户端，当前主要适配 Clash 系工具 |
| 浏览器 | 使用独立浏览器功能需安装 Microsoft Edge 或 Google Chrome |
| Claude / Claude Code | 按需从官方渠道安装，不随小帆船提供 |

## 下载与安装

进入 [Releases 下载页](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.19)，展开 **Assets**。三种格式包含同一个应用，**任选一种即可，推荐 DMG**。

| 下载文件 | 安装方法 |
|---|---|
| `小帆船-v1.3.19-macOS.dmg` | 打开镜像，将 APP 拖入“应用程序”，然后推出镜像 |
| `小帆船-v1.3.19-macOS.zip` | 解压后，将 APP 拖入“应用程序” |
| `小帆船-v1.3.19-app.tar.gz` | 解压获得完整 APP 文件夹，再拖入“应用程序” |

macOS 的 `.app` 本质上是文件夹，第三种因此以 tar.gz 封装。GitHub 自动提供的 **Source code** 文件是本仓库的文档快照，不是安装包，也不是完整应用源码。

附件还包括使用说明与许可、`THIRD_PARTY_NOTICES.txt` 和 `SHA256SUMS.txt`。请保留第三方许可；需要时可用校验清单核对下载文件。

**首次打开提示：** 本版仅有本地临时签名，尚未通过 Apple 公证，系统可能拦截。请先确认下载来源和校验值，再按系统“隐私与安全性”的正常提示处理。不要关闭 Gatekeeper、SIP 等安全保护；遇到恶意软件、损坏或签名异常提示时，先停止安装并反馈。

## 快速开始

1. **准备代理。** 在自己的代理客户端导入合法配置，确认能正常联网。
2. **检查代理设置。** 在 Clash 中手动确认 TUN、全局模式和系统代理，记下实际 HTTP/mixed 端口。
3. **填写端口、选择地区。** 在小帆船“环境”中填写实际端口。常见上游端口为 `7897`；`17897` 是小帆船自己的本地代理端口，不能作为上游填写。选择目标地区用于核对，不会替你切换节点。
4. **查看检查结果。** 等待出口和连接状态更新，按提示处理阻断原因。未知、超时或来源矛盾时，先排查再使用。
5. **开启护航并启动。** 确认状态后，通过小帆船中的入口启动目标客户端。首次登录仍需完成官方授权流程。
6. **结束前保存工作。** 关闭护航会中断受控连接；退出小帆船可能结束相关客户端和终端，请先保存任务。

更多操作、恢复和卸载步骤见[完整使用指南](docs/使用指南.md)。

## 使用前请留意

- **系统设置会受到影响。** “一键配置”等可选操作可能更改语言、时区、IPv6 和 Claude Code 设置。时区快捷配置还可能建立持续有效的管理员免密规则，使用前应了解权限影响。
- **清理操作可能丢失数据。** 浏览器重建和“封号善后”可能删除登录凭据、会话或本地资料，不是普通网络排障步骤。
- **保护范围有限。** 只有实际经过小帆船本地代理的连接才受该开关控制。代理已开启或 IP 检查通过，不代表所有软件、DNS、IPv6 和 WebRTC 均已隔离。
- **IP 分数仅供参考。** 第三方数据可能不准确，不能判断账号资格或代替官方政策。网络检查会访问第三方服务，部分原始出口查询可能直连或使用明文 HTTP。

修改范围、权限、联网服务与隐私影响详见[注意事项与隐私说明](docs/注意事项与隐私说明.md)。

## 已知限制与更新

当前版本为 **v1.3.19 / Build 149**，仅适用于 Apple 芯片。尚未完成干净系统安装、卸载及全部网络协议的完整验收。

应用内的反馈按钮仍使用旧地址，请通过[本仓库 Issues](https://github.com/zhongyuanl/xiaofanchuan/issues)反馈。“检查更新”目前显示内置版本信息，下载新版本请以 Releases 为准。

本版重点改进设置快照、无效 JSON 写入保护、凭据处理及浏览器启动检查。详情见[更新记录](CHANGELOG.md)和[发布说明](docs/发布说明-v1.3.19.md)。签名公证、在线更新及更细致的退出清理是后续改进方向，尚无交付日期。

## 参考项目与致谢

感谢以下项目提供的代码、配套能力或设计思路。**实际代码复用与设计参考分别列出，不代表上游参与或认可本项目。**

| 项目 | 使用关系 |
|---|---|
| [CCBaga](https://github.com/liseami/CCBaga) | 实际复用 Rust 地区目录与匹配逻辑，保留 MIT 许可和作者声明 |
| [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev) / [Mihomo](https://github.com/MetaCubeX/mihomo) | 外部代理配套及接口、文档参考；本次 APP 未内置其二进制 |
| [Magic UI](https://github.com/magicuidesign/magicui) | 界面与动效方向参考，未引入其 React 运行时 |
| [Impeccable](https://github.com/pbakaus/impeccable) | 设计审查与细节打磨方法参考 |
| [Emil Kowalski skills](https://github.com/emilkowalski/skills) | Apple 风格交互与连续动效方法参考 |
| [Fingerprint Chromium](https://github.com/adryfish/fingerprint-chromium) | 早期浏览器候选调研，本次未集成、未分发 |
| serde / serde_json 等 | Rust 配套程序依赖，见[依赖清单](third-party/RUST-DEPENDENCIES.md) |

固定版本、复用文件、修改范围及许可证链接见[参考项目与许可](docs/参考项目与许可.md)。完整许可文本见 [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt)。

## 反馈与贡献

欢迎报告问题、提出建议或修正文档。提交前请阅读 [贡献指南](CONTRIBUTING.md)，删除日志中的密钥、账号、订阅链接和真实 IP。安全问题见 [SECURITY.md](SECURITY.md)。

此仓库用于发布应用和文档，尚未提供完整工程源码及构建入口。未为完整应用新增开源许可证；第三方部分按各自许可处理，见 [LICENSE.md](LICENSE.md)。

小帆船与 Anthropic、Apple、Microsoft、Google 及参考项目均无官方隶属或背书关系。
