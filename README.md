<div align="center">

<img src="docs/images/app-logo.png" alt="小帆船 Little Sailboat" width="112" height="112" />

# 小帆船（Little Sailboat）
### Claude 与 Claude Code 运行环境安全控制台

面向 macOS 与 Windows 平台的桌面端安全护航与运行环境编排系统

[![macOS](https://img.shields.io/badge/macOS-v2.0.3-007AFF?style=flat-square&logo=apple)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v2.0.3)
[![Windows](https://img.shields.io/badge/Windows-v1.3.23-0078D6?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.23)
[![Platform](https://img.shields.io/badge/Architecture-Native_Swift_6_%7C_Rust-FA7343?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan)
[![Release](https://img.shields.io/badge/Release-Stable-brightgreen?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan/releases)

[简体中文](README.md) · [English](README.en.md) · [使用指南](docs/使用指南.md) · [注意事项与隐私说明](docs/注意事项与隐私说明.md) · [问题反馈](https://github.com/zhongyuanl/xiaofanchuan/issues)

</div>

---

## 1. 问题背景与风险分析

在开发和使用 Claude 官方桌面应用、Web 终端及 Claude Code（CLI 命令行）过程中，客户端运行环境与底层网络传输常面临若干结构性安全隐患，极易导致账号受限或会话阻断：

- 静默降级与真实 IP 暴露：当上游代理节点偶发网络抖动或中断时，宿主操作系统的默认网络调度倾向于静默回落至本地网络，导致境内物理出口 IP 直接暴露于目标服务方，触发安全风控。
- 命令行子进程旁路直连：Claude Code 在执行编译构建、代码分析与多工具调用时，后台触发的 npx、uvx、git、curl 及各类 MCP（Model Context Protocol）命令行子进程通常脱离上层环境代理规则，直接通过底层物理链路发送请求。
- 系统指纹与特征矛盾：网络出口已处于海外合规区域，但宿主系统的时区设置、本地 DNS 解析行为以及 WebRTC 协议探测依然对外广播真实的地理与物理网络特征，造成环境前后矛盾。
- 会话污染与出口漂移：通用浏览器混合用于日常访问与生产环境，导致账号 Cookie 与缓存数据交叉污染；出口 IP 在短时间内跨越不同物理国家与地理坐标，易被安全审计系统判定为异常异地登录。

小帆船针对上述隐患构建了完整的控制层，通过本地断流控制、双底座流量接管、系统环境对齐与受控沙盒调度，提供一致、透明且受控的客户端运行环境。

---

## 2. 核心系统架构与设计亮点

### 2.1 本地断流控制机制（Fail-Closed Gatekeeper）
系统在本地建立专属安全控制网关（127.0.0.1:17897），对经由小帆船调度发起的所有请求实施强制校验与放行控制：
- 故障断流控制：当上游代理通道失效、节点连通性中断或网络特征未达合规基准时，水闸执行硬性阻断，彻底阻断流量降级直连的可能，杜绝真实 IP 暴露。
- 全要素环境核验：集成公网出口探测算法，核验 IP 纯净度（数据中心/住宅网络标识）、官方合规国家与地区范围（涵盖 185 个官方支持区域）以及宿主系统时区一致性，同时支持中文语言豁免。
- 隧道活性保活：采用毫秒级探针评估底层隧道连通性，当通道健康且出口拓扑未漂移时，过滤偶发接口超时，保障会话持续稳定。

### 2.2 双底座网络接管架构（系统代理 + TUN 虚拟网卡）
传统单一代理方案通常无法覆盖非标准协议应用与命令行终端。小帆船在底层实施强制双底座接管机制：
- 复合网络接管：同时启用系统级 HTTP/SOCKS 代理与底层 TUN 虚拟网卡驱动。桌面应用与浏览器通过标准代理通道调度，所有终端命令、MCP 工具子进程、UDP 报文及 DNS 查询则由内核级虚拟网卡完整捕获。
- 零泄漏安全边界：内置远端加密 DoH（DNS over HTTPS）解析服务，阻断 STUN 协议与 WebRTC 旁路传输，保障本地 DNS 与物理网络不发生旁路泄漏。

### 2.3 双引擎协同调度与分流模式
- 内置独立内核：集成独立专有代理内核，支持直接导入订阅源，具备单节点独立探测与多节点并发异步测速能力。
- 外部客户端协同与一键修复：兼容既有第三方外部代理客户端；提供「系统代理一键修复」功能，自动按当前联网物理接口（Wi-Fi、以太网或 USB 适配器）纠正代理设置，降低网络迁移与换机调试成本。
- 双重路由策略：
  - 智能分流模式：境内域名、局域网段及办公应用自动走本地物理网卡直连，Claude 服务与海外流量路由至受控隧道；支持直接粘贴网址生成直连规则。
  - 全量出海模式：全机流量统一经由受控安全通道路由，适用于严格隔离的跨境开发任务。

### 2.4 三端受控沙盒调度体系
系统提供集成启动控制台，统一管理三类典型运行终端：
- 官方桌面应用：在受控网络策略与 MCP 依赖环境下拉起 Claude Desktop。
- 专用沙盒浏览器：创建独立会话存储沙盒，与日常主浏览器数据彻底隔离，防止 Cookie 串号与指纹交叉污染。
- Claude Code 终端：自动化注入受控环境变量与安全中继配置，免除手动 export 配置及误修改 settings.json 的潜在风险。
- 生命周期安全清场：主控制台退出时执行关联清理流程，提示并协同回收受控子进程，避免残留进程降级脱离防护。

### 2.5 原生系统实现与全局 3D 轨迹映射
- 原生开发框架：macOS 端基于 Swift 6、SwiftUI 与 AppKit 深度重构，启动即时且内存占用低，深度融合系统级视觉规范。
- 流量路径 3D 可视化映射：通过点阵投影实时映射物理发起来源与海外出口节点的空间链路关系，直观呈现网络拓扑状态。
- 跨区域瞬移防护：记录实际业务会话出口节点，防止无意切节点时引发虚假跨国瞬移风控判定。

---

## 3. 系统界面与功能概览

<div align="center">

### 通行控制中心
集中呈现出口网络状态、安全水闸控制开关及三端受控启动入口，直观展示实时拓扑链路。

![通行控制中心](docs/images/passage.png?v=2.0.3)

<br/>

### 代理环境与配置管理
管理订阅源与节点列表，支持内置与外部代理引擎切换、节点延迟测速与直连规则配置。

![代理环境](docs/images/environment-proxy.png?v=2.0.3)

<br/>

### 环境配置与设置选项
统一管理时区状态、端口分配、启动偏好与系统代理修复工具。

![设置中心](docs/images/settings.png?v=2.0.3)

</div>

> 📌 *注：界面截图中展示的订阅名称、节点标签及网络出口均为用于演示的示例数据。*

---

## 4. 获取与安装说明

| 平台 | 版本 | 分发文件 | 运行环境要求 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| macOS | v2.0.3 | [DMG 镜像](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.dmg) · [ZIP 归档](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.zip) | Apple Silicon 架构（M 系列芯片），macOS 13.0 及更高版本 | 原生 Swift 6 构建，内置引导式安装界面 |
| Windows | v1.3.23 | [EXE 单文件](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.exe) · [ZIP 归档](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.zip) | Windows 10 / 11 64 位操作系统 | 独立便携版本，基于 WebView2 渲染架构 |

macOS 安装流程：打开 DMG 镜像后，将小帆船拖移至 Applications 应用程序目录完成安装。本开源分发包采用本地临时签名机制，若首次启动出现系统安全提示，请前往「系统设置 → 隐私与安全性」页面点击「仍要打开」。软件包完整性可通过发布页提供的 [SHA256SUMS.txt](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/SHA256SUMS.txt) 进行校验。

---

## 5. 快速启动流程

```mermaid
flowchart LR
    Step1["1. 接入代理网络<br/>(导入订阅源或指定外部客户端)"]
    Step2["2. 自动化环境核验<br/>(水闸自检、时区校验与出口探测)"]
    Step3["3. 受控启动业务端<br/>(拉起桌面端 / 沙盒浏览器 / CLI)"]

    Step1 --> Step2 --> Step3
```

1. 接入代理网络：在「环境 → 代理环境」中导入可用订阅源，或指定外部客户端并配置本地端口。
2. 自动化环境核验：系统自动探测出口 IP 归属并执行环境合规审查，完成水闸安全基线确认。
3. 受控启动业务端：在通行页面开启安全护航，按需启动 Claude 桌面应用、专用沙盒浏览器或 Claude Code 命令行终端，在受控边界内执行研发任务。

---

## 6. 合规说明与设计准则

- 纯净辅助定位：小帆船属于纯粹的客户端网络环境治理与启动调度工具。本项目不提供、不内置、亦不销售任何网络节点、代理服务或第三方商业账号。使用人员应自行准备合规网络环境。
- 非侵入式受控：本地断流水闸仅对受控端口及由小帆船拉起的进程实施流控，杜绝意外旁路直连，不包含非法的系统核心修改行为。
- 配置资产安全：对所有配置文件变更实施时间戳快照机制，保障开发者的个性化配置与敏感凭据安全。详见 [注意事项与隐私说明](docs/注意事项与隐私说明.md)。

---

## 7. 致谢与引用说明

小帆船系统参考并集成了开源社区的相关成果：
- Mihomo：代理内核标准与底层网络通信实现。
- CCBaga：区域字典与地理代码匹配逻辑。
- Clash Verge Rev：跨平台桌面客户端工程实践参考。

完整许可范围详见 [LICENSE](LICENSE.md)，依赖项来源与版权声明详见 [参考项目与许可](docs/参考项目与许可.md) 以及 [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt)。

---

<div align="center">

让每一次 AI 交互，都在规范、透明与受控的环境中稳定运行。  
欢迎通过 [GitHub Issues](https://github.com/zhongyuanl/xiaofanchuan/issues) 提交缺陷报告或改进建议。

</div>
