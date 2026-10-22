# ⛵ 小帆船 Little Sailboat

![Version](https://img.shields.io/badge/version-1.3.19-blue) ![macOS](https://img.shields.io/badge/macOS-13%2B-lightgrey) ![Architecture](https://img.shields.io/badge/Apple_Silicon-arm64-blue)

[下载最新版](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.19) · [使用指南](docs/使用指南.md) · [问题反馈](https://github.com/zhongyuanl/xiaofanchuan/issues) · [更新记录](CHANGELOG.md) · [参考与许可](docs/参考项目与许可.md)

面向 macOS 的本地网络状态检查与 Claude 启动辅助工具。通过原生界面查看代理、出口 IP、地区和环境设置，并为经本程序启动、配置为使用本地代理的客户端提供通断控制。

**当前发布：v1.3.19 · Build 149 · Apple Silicon（arm64）。** 应用声明最低 macOS 13.0；没有完成全部 macOS 版本或干净系统的兼容性验收。Intel Mac、Windows 和 Linux 不在本次发行范围内。

本项目与 Anthropic、Apple、Microsoft、Google 及下列参考项目没有官方隶属或背书关系。**不承诺防封、解封、匿名、改变服务使用资格或覆盖整机全部网络流量。** 请遵守所在地法律及各服务的使用条款；地区选择不会改变用户的实际位置或服务资格。

## 界面展示

下图为本地保存的 **v1.3.16 界面演示图**，使用固定演示数据，只展示布局；v1.3.19 的细节以实际应用为准。图中的“物理阻断”“DNS 锁定”和绿色状态不是当前网络的验收证据。

![通行界面演示](docs/images/passage.png)

<details>
<summary>查看设置界面</summary>

![设置界面演示](docs/images/settings.png)

</details>

## 下载与安装

在本仓库 **Releases → v1.3.19 → Assets** 下载。三种格式包含同一个应用，任选一种即可：

| 文件 | 适合场景 | 如何安装 |
|---|---|---|
| `小帆船-v1.3.19-macOS.dmg` | 常规安装，推荐 | 打开镜像，把 APP 拖入“应用程序”，然后推出镜像 |
| `小帆船-v1.3.19-macOS.zip` | 使用系统解压工具 | 解压后把 `.app` 拖入“应用程序” |
| `小帆船-v1.3.19-app.tar.gz` | 保存或传输原始 APP 目录 | 解压后把 `.app` 拖入“应用程序” |

macOS 的 `.app` 实际是文件夹，GitHub Release 不能把它作为一个可直接下载的裸文件上传，因此第三种用 tar.gz 保留 APP 目录结构。GitHub 自动显示的 **Source code (zip/tar.gz)** 是此发布仓库的文档快照，不是安装包或完整工程源码。

同时下载 `THIRD_PARTY_NOTICES.txt`，保留随发行提供的第三方许可。可用 `SHA256SUMS.txt` 对照安装包的 SHA-256。校验值证明下载内容与本次上传文件一致，不等于 Apple 公证或安全认证。

当前应用使用 **ad-hoc 本地签名，没有 Developer ID 和 Apple 公证**。首次打开可能被系统拦截；仅在确认来源和校验值后，依据 macOS“隐私与安全性”中的提示处理。不要关闭 Gatekeeper、SIP 或整机安全检查。系统明确提示恶意软件、损坏或签名问题时，请停止安装并反馈。

## 开始使用

1. **准备外部代理客户端。** 建议先自行从官方仓库安装 Clash Verge Rev，导入你合法持有的代理配置，确认可以正常联网。小帆船不提供节点、订阅、账号或付费服务。
2. **在 Clash 中手动设置。** 按应用提示检查 TUN、全局模式和系统代理，确认本地 HTTP/mixed 端口。程序常用上游端口为 `7897`，以你的实际配置为准；`17897` 是小帆船本地水闸端口，不能填成上游端口。
3. **打开小帆船，先检查再配置。** 在“环境”查看网络、浏览器和电脑环境，填写实际代理端口，选择需要核对的目标地区。选择地区不会替你购买或切换到相应节点。
4. **按需调整环境。** 先看下方“会修改哪些内容”。时区、语言等会影响系统及其他软件，建议先记录原值；不需要的操作不要点击。
5. **确认通行状态。** 回到“通行”，等待出口数据与状态更新，处理阻断原因后开启安全护航。未知、超时、数据矛盾时不要把状态理解为已验证安全。
6. **通过应用中的入口启动。** 可按实际安装情况启动 Claude 桌面端、Claude Code 相关入口、独立资料浏览器或命令行。安全浏览器需要已安装的 Microsoft Edge 或 Google Chrome；首次 OAuth 登录按官方流程完成。
7. **结束工作。** 先保存任务。关闭护航用于切断受控代理连接；退出小帆船可能关闭 Claude、独立浏览器和相关终端进程。已有请求可能失败，需要客户端重新连接。

详细步骤、常见问题及卸载：[使用指南](docs/使用指南.md)。修改范围、联网服务及限制：[注意事项与隐私说明](docs/注意事项与隐私说明.md)。

## 功能与边界

- 网络与代理状态、出口 IP / ASN / 地区及第三方 IP 属性信息展示。
- 本地 `127.0.0.1:17897` 代理水闸及应用内护航开关。
- 独立浏览器资料、启动参数和 Claude Code 配置辅助。
- 地区、系统语言、时区和 IPv6 等环境检查与可选配置。
- 本地日志、设置快照和帮助说明。

**水闸只影响实际经过它的连接。** TUN 显示开启或 IP 查询成功，都不能单独证明 DNS、IPv6、WebRTC、已运行软件、直接启动的客户端或全部协议已被隔离。状态有探测周期和缓存，不能承诺零时间窗口。住宅属性、风险分及地区数据库可能出错，也不能推断账号状态。

## 系统与配套要求

| 项目 | 要求或说明 |
|---|---|
| 处理器 | Apple Silicon / arm64，非 Intel |
| 操作系统 | APP 声明 macOS 13.0 起，兼容性测试范围有限 |
| 代理客户端 | 用户自行安装，当前代码主要适配 Clash 系工具 |
| 浏览器 | 按需安装 Edge 或 Chrome，用于独立资料入口 |
| Claude / Claude Code | 用户按官方流程自行取得和配置 |
| 管理员权限 | 某些系统设置或安装动作会请求；日常状态展示与全局修改应区别对待 |
| 开发者签名 | 本地 ad-hoc 签名，未公证 |

## 会修改哪些内容

可选操作可能写入 `~/.claude/settings.json`、生成启动脚本、创建独立浏览器资料、修改系统语言/地区/时区、停用 IPv6，以及安装外部软件。时区快捷配置代码还包含写入 `/private/etc/sudoers.d/claudeguard` 的逻辑，会建立持久的免密执行规则；这不是普通界面偏好修改，使用前应理解权限影响。

v1.3.19 在修改 Claude Code 设置前创建带时间戳快照，保留最近 5 份；解析既有 JSON 失败时停止写入。快照不是完整系统备份。涉及凭据、浏览器重建或“封号善后”的清理操作可能不可逆，**不是常规安装步骤**，不要用来解决一般网络故障。

## 参考项目与致谢

来源关系在 [参考项目与许可](docs/参考项目与许可.md) 中逐项说明。

| 项目 | 在小帆船中的关系 |
|---|---|
| [CCBaga](https://github.com/liseami/CCBaga) | **实际代码复用**：Rust 地区目录与匹配逻辑，固定提交 `aff6122719c479effd4d53c7d875bcc3c04edcc8`；MIT 完整条款随发行保留 |
| [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev) / [Mihomo](https://github.com/MetaCubeX/mihomo) | 外部代理客户端及内核的配套、控制接口与网络文档参考；本次 APP 未内置这两个项目的二进制 |
| [Magic UI](https://github.com/magicuidesign/magicui) | 界面与动效方向参考；本次原生 SwiftUI 包没有 React/Magic UI 运行时依赖 |
| [Impeccable](https://github.com/pbakaus/impeccable) | 设计审查与细节打磨方法参考 |
| [Emil Kowalski skills](https://github.com/emilkowalski/skills) | Apple 风格交互与连续动效指导参考 |
| [Fingerprint Chromium](https://github.com/adryfish/fingerprint-chromium) | 早期浏览器候选调研；**本次未集成、未分发**，当前安全浏览器使用用户安装的 Edge/Chrome |
| serde / serde_json 等 Rust crates | 配套 guard-agent 的依赖，包含传递与构建期清单，详见 [依赖清单](third-party/RUST-DEPENDENCIES.md) |

完整许可文本：[THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt)。上游许可只覆盖对应上游部分；本仓库未为完整小帆船工程授予新的开源许可证。此仓库用于分发安装包与使用文档，不等于全部开发工程已开源。

## 更新与反馈

v1.3.19 重点：Claude Code 设置写入前快照、无效 JSON 保护、`sk-ant-` 前缀凭据保留逻辑、安全浏览器启动门禁及代理设置入口调整。详见 [本次发布说明](docs/发布说明-v1.3.19.md)。前缀判断无法验证凭据有效性或官方身份。

请使用**本仓库 Issues** 提交复现步骤、macOS 版本、芯片类型、应用版本及脱敏后的错误。安装包中的反馈按钮仍为旧地址，暂请通过仓库页面反馈。“检查更新”目前展示内置版本信息，不是联网自动更新服务；新版本请以 Releases 为准。

## 常见问题

- **这是三个平台版本吗？** 不是，三种格式均为同一个 arm64 macOS 应用。
- **需要全部下载吗？** 不需要，通常选择 DMG；APP 本体以 tar.gz 封装提供。
- **包含代理节点和账号吗？** 不包含，请自行准备合法配置与服务账号。
- **能保证账号安全或零泄漏吗？** 不能；状态检测、代理连接和账号使用资格是不同问题。
- **删除 APP 会还原系统吗？** 不会，参照[恢复与卸载](docs/使用指南.md)处理设置和权限。

更多排查见[完整使用指南](docs/使用指南.md)。

## 项目状态与后续改进

当前发布可下载的用户确认版本，仍有签名公证、干净系统验收、反馈地址、在线更新及细粒度退出清理等限制。上述事项记录为后续改进方向，不代表已实现或承诺交付日期。

## 参与贡献

欢迎提交可复现的问题、文档修正、兼容性信息及来源/许可更正。请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md)；涉及凭据或未公开漏洞时，不要在公开 Issues 上传敏感信息，见 [SECURITY.md](SECURITY.md)。目前仓库为发行与文档仓库，未提供完整应用源码构建入口；不把这里的资料声明为完整开源工程。

## 许可证说明

本仓库没有为完整应用新增 MIT、GPL 等开源授权。第三方对应部分按各自许可处理，尤其须保留 CCBaga 的 MIT 声明与随包提供的 Rust 依赖许可；详情见 [LICENSE.md](LICENSE.md) 和 [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt)。
