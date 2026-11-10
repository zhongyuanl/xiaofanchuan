<div align="center">

<img src="docs/images/app-logo.png" alt="小帆船 Little Sailboat" width="112" height="112" />

# 小帆船 · Little Sailboat
### 专为 Claude 与 Claude Code 打造的原生环境管理与安全护航控制台
### Native Environment Orchestration & Security Harbor for Claude & Claude Code

让每一次 AI 交互，都在纯净、透明、物理硬阻断的极安全环境中从容起航！  
Empowering every AI interaction in a pure, transparent, and fail-closed secure harbor.

[![macOS](https://img.shields.io/badge/macOS-v2.0.3-007AFF?style=flat-square&logo=apple)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v2.0.3)
[![Windows](https://img.shields.io/badge/Windows-v1.3.23-0078D6?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.23)
[![Swift 6](https://img.shields.io/badge/Core-Swift_6_%26_Rust-FA7343?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan)
[![Release](https://img.shields.io/badge/Release-Stable-brightgreen?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan/releases)

[🇨🇳 简体中文](#-简体中文) · [🇺🇸 English](#-english) · [使用指南](docs/使用指南.md) · [注意事项与隐私说明](docs/注意事项与隐私说明.md) · [问题反馈](https://github.com/zhongyuanl/xiaofanchuan/issues)

</div>

---

## 🇨🇳 简体中文

### 为什么 Claude 账号总在莫名被封？

很多开发者在使用 Claude 桌面端、Web 网页版以及 Claude Code 命令行时，常遇到毫无征兆的封号封锁。背后的真实原因往往潜藏在操作系统底层：

- 掉线瞬间静默直连：代理节点稍有抖动断开，系统就会悄悄切回本地宽带，境内真实 IP 瞬间裸奔直通，直接触发安全风控。
- 命令行子进程偷跑：使用 Claude Code 写代码时，调用的 npx、uvx、git、curl 和 MCP 子进程根本不看常规代理环境变量，在内核底层频频直连泄漏。
- 环境特征前后穿帮：虽然出口 IP 在海外，但本地时区还是东八区、DNS 频频向本地运营商查询、WebRTC 协议还在底层偷偷广播真实物理 IP。
- 浏览器混用与异地瞬移：日常浏览和 AI 开发混用同一个浏览器，Cookie 数据互相污染；上午在美西、下午在东京，极易被判定为异地盗号。

小帆船（Little Sailboat）全新版本就是为了终结这些痛点而生！它将本地物理断流水闸、双底座网络接管、全要素环境核验与三端沙盒启动浓缩在一个优雅的原生控制中心，全方位守护你的账号资产。

---

### 全新版本亮点特色

1. 原生 Apple 视觉美学与 3D 点阵交互地球仪
- 基于纯 Swift 6 + SwiftUI + AppKit 原生重构，启动瞬时响应，清透毛玻璃材质与系统浑然一体。
- 内置高性能 3D 点阵交互地球仪，支持鼠标 360° 自由旋转探索与双击平滑复位，动态映射物理网络起点到海外出口节点的出境飞线与同心圆光波。
- 通行控制中心三大卡片自适应统一布局，信息一目了然，免去滑动滚轮翻找的烦恼。

2. Fail-Closed 本地物理硬阻断水闸（127.0.0.1:17897）
- 宁可断网，绝不裸奔！独创本地断流水闸。在网络波动、节点掉线或环境异常时，水闸坚决执行硬阻断，绝不放行任何未受控直连流量，杜绝真实 IP 暴露。
- 出口 IP 纯净度检测（原生住宅网络与数据中心识别）、官方 185 个国家与地区合规校验、本地时区自动对齐；海外华人使用中文同样受到友好豁免。
- 智能保活机制：只要底层代理隧道存活且出口未漂移，绝不因单次网络探针超时误断流，杜绝频繁打扰。

3. 「系统代理 + TUN 虚拟网卡」强制双开内核底座
- 告别泄漏死角！底层强制同时启用系统代理与 TUN 虚拟网卡。桌面应用和浏览器走高效代理通道；TUN 虚拟网卡在内核层全面接管所有命令行终端、MCP 外部子进程、UDP 报文与底层 DNS，杜绝任何旁路直连。
- 内置远端加密 DoH DNS 与 STUN 协议拦截，实现真正的零 DNS 泄漏与零 WebRTC 泄漏。

4. 双引擎随心切换与智能分流
- 内置独立代理专核：直接导入订阅源，具备单节点与多节点并发异步毫秒级测速能力。
- 外部客户端无缝兼容：完美适配已有外部代理软件，具备智能网卡识别能力，秒级纠偏系统代理设置。
- 极简路由二选一：
  - 智能分流（日常推荐）：国内网页、微信直连秒开；Claude 服务与海外流量走安全专线。遇到特定内网网址，直接粘贴网址即可自动生成直连规则。
  - 全量出海（深度场景）：整台电脑所有软件与终端流量 100% 走海外专线。

5. 三端一键独立沙盒启动台
- Claude 官方桌面端：一键接管网络环境与后台 MCP 依赖。
- 独立安全沙盒浏览器：内置专用沙盒环境，完全独立于日常主浏览器，Cookie 与缓存绝不串号。
- Claude Code 命令行终端：一键自动注入受控环境变量与水闸中继，彻底告别手动 export 的繁琐与写坏配置文件的风险。
- 退出安全清场：退出小帆船时主动弹窗提示并清场受控进程，防止退出后后台进程意外滑落至本地直连网络。

6. 24 小时防瞬移保护与多账号沙盒
- 记录实际业务会话出口，只有真正启动使用 Claude 时才计入差旅切换，防止测速切节点被误判为跨国瞬移。
- 多账号环境数据物理隔离，轻松管理多个 Claude 账号。

---

### 界面概览

<div align="center">

#### 通行控制中心
三大卡片等高排布：3D 点阵地球仪实时展示出境飞线与出口位置；安全护航卡片守护物理水闸；底部一键拉起桌面端、安全浏览器与终端。

![通行控制中心](docs/images/passage.png?v=2.0.3)

<br/>

#### 代理环境与订阅管理
支持内置代理与外部客户端无缝切换，管理订阅源与节点列表，单节点异步毫秒级测速，直连规则一键配置。

![代理环境](docs/images/environment-proxy.png?v=2.0.3)

<br/>

#### 环境配置与设置中心
统筹系统时区、网络端口与开机配置，提供贴心的一键设置助理与智能修复工具。

![设置中心](docs/images/settings.png?v=2.0.3)

</div>

> 📌 *注：界面截图中展示的订阅名称、节点标签及网络出口均为用于演示的示例数据。*

---

### 获取与安装

| 平台 | 版本 | 安装包 | 运行环境要求 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| macOS | v2.0.3 | [DMG 镜像](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.dmg) · [ZIP 压缩包](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.zip) | Apple Silicon (M 系列芯片)，macOS 13.0 及更高版本 | 原生 Swift 6 架构，自带引导式安装界面 |
| Windows | v1.3.23 | [EXE 单文件](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.exe) · [ZIP 压缩包](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.zip) | Windows 10 / 11 64 位操作系统 | 便携绿色版，基于 WebView2 渲染架构 |

macOS 安装说明：双击打开 DMG 后，将小帆船拖移至 Applications 应用程序文件夹即可。若首次打开出现系统提示，请前往「系统设置 → 隐私与安全性」点击「仍要打开」。软件包完整性可通过发布页提供的 [SHA256SUMS.txt](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/SHA256SUMS.txt) 进行核验。

---

### 极速上手：3 步起航

```mermaid
flowchart LR
    Step1["1. 接入代理<br/>(导入订阅源或选择外部客户端)"]
    Step2["2. 自动核验<br/>(水闸自检、IP 纯净度与时区对齐)"]
    Step3["3. 开启护航<br/>(一键启动桌面端 / 沙盒浏览器 / CLI)"]

    Step1 --> Step2 --> Step3
```

1. 接入代理网络：在「环境 → 代理环境」导入您的订阅源，或指定外部客户端并填写端口。
2. 自动核验自检：小帆船自动探测出口 IP 归属地与纯净度，水闸即时校验时区与无泄漏防护。
3. 安全放行起航：开启安全护航，在通行页一键启动 Claude 桌面端、沙盒浏览器或 Claude Code 终端，在绝对受控的环境中安心使用！

---

## 🇺🇸 English

### Why Do Claude Accounts Get Unexpectedly Suspended?

When working with Claude Desktop, web sessions, and Claude Code CLI, developers frequently face sudden account bans. The root cause usually hides deep in operating system networking:

- Silent Fallback to Direct Connection: When proxy tunnels fluctuate, host systems quietly fall back to local networks, exposing your domestic public IP and triggering strict fraud detection.
- Command-Line Subprocess Leaks: Tools spawned by Claude Code—such as npx, uvx, git, curl, and MCP child processes—routinely bypass standard proxy environment variables, connecting directly via kernel paths.
- Contradictory Environmental Telemetry: Even if your exit IP is overseas, local timezone mismatches, DNS queries to local ISPs, and WebRTC STUN broadcasts continuously reveal your physical location.
- Cookie Cross-Contamination & Teleportation: Mixing general browsing with development pollutes session cookies; switching exit nodes between distant regions within hours raises immediate security red flags.

Little Sailboat is engineered to eliminate these threats! It unites fail-closed gatekeeping, dual-engine interception, environmental verification, and tri-terminal sandboxing into one intuitive native harbor.

---

### Major Highlights & Innovations

1. Authentic Apple Glass Aesthetics & Interactive 3D Dot-Matrix Globe
- Pure Swift 6 + SwiftUI + AppKit native architecture for instant startup and seamless macOS integration.
- Interactive 3D dot-matrix globe with 360° mouse drag rotation, double-click auto-centering, and live vector arcs from your physical location to outbound exit nodes.
- Adaptive uniform card geometry presenting all core controls at a glance without scrolling.

2. Fail-Closed Gatekeeper Proxy (127.0.0.1:17897)
- Fail-Closed by Design: If network connectivity drops or proxy nodes fail, the gatekeeper severs traffic immediately—never allowing silent fallback to direct unproxied connections, eliminating real-IP leakage once and for all!
- Full-Spectrum Verification: IP purity audit (residential vs. datacenter), compliance validation across 185 supported regions, and automatic OS timezone coordination.
- Resilient Tunnel Keep-Alive: High-frequency tunnel probes prevent false disconnects from temporary upstream API timeouts.

3. Mandatory Dual Substrate: System Proxy + TUN Virtual Interface
- Zero-Leak Guarantee: Automatically activates System Proxy and a kernel-level TUN virtual adapter simultaneously. Standard applications route through fast proxies, while all CLI tools, MCP subprocesses, UDP packets, and system DNS queries are fully captured by the TUN driver.
- Enforces remote encrypted DoH DNS and STUN protocol blocking for true zero DNS and WebRTC leaks.

4. Dual-Engine Flexibility & Smart Routing
- Built-in Mihomo Core: Direct subscription imports, single-node latency checks, and asynchronous concurrent batch benchmarks.
- External Client Integration: Compatible with external proxy clients, featuring intelligent adapter detection to restore proxy settings in seconds.
- Intuitive Split Tunneling:
  - Smart Split: Domestic services and internal endpoints route directly at full speed; Claude services route through the secure proxy tunnel. Convert any URL into a direct rule with one paste.
  - Full Global: Routes 100% of host traffic through the secure tunnel for dedicated cross-border sandboxes.

5. Tri-Terminal Sandboxed Launcher
- Claude Official Desktop: One-click launch with managed proxy settings and child MCP process protection.
- Dedicated Sandboxed Browser: Standalone sandbox profile completely isolated from your daily browser, preventing cookie cross-contamination.
- Claude Code CLI Terminal: Automatically injects proxy environment variables and gatekeeper bindings—no manual exports or broken configurations.
- Clean Exit Teardown: Prompts and terminates managed processes upon quitting Little Sailboat to prevent orphaned instances from dropping into unproxied network states.

6. 24-Hour Anti-Teleportation & Multi-Account Isolation
- Correlates active session exits to prevent false cross-border flags caused by idle node switching.
- Complete data isolation across multiple Claude accounts.

---

### Downloads & Verification

| Platform | Version | Packages | Requirements | Notes |
| :--- | :--- | :--- | :--- | :--- |
| macOS | v2.0.3 | [DMG Image](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.dmg) · [ZIP Archive](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.zip) | Apple Silicon (M Series), macOS 13.0 or later | Native Swift 6 build with guided drag-and-drop installer |
| Windows | v1.3.23 | [Standalone EXE](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.exe) · [ZIP Archive](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.zip) | Windows 10 / 11 64-bit | Portable single executable powered by WebView2 |

---

## 🛡️ 合规说明与设计准则 · Compliance & Philosophy

- 纯净辅助定位：小帆船属于纯粹的客户端网络环境治理与启动调度工具。本项目不提供、不内置、亦不销售任何网络节点、代理服务或第三方商业账号。使用人员应自行准备合规网络环境。
- 非侵入式受控：本地断流水闸仅对受控端口及由小帆船拉起的进程实施流控，杜绝意外旁路直连，不包含非法的系统核心修改行为。
- 配置资产安全：对所有配置文件变更实施时间戳快照机制，保障开发者的个性化配置与敏感凭据安全。详见 [注意事项与隐私说明](docs/注意事项与隐私说明.md)。

---

## 🤝 致谢与引用说明 · Acknowledgments

小帆船系统参考并集成了开源社区的相关成果：
- [Mihomo](https://github.com/MetaCubeX/mihomo)：代理内核标准与底层网络通信实现。
- [CCBaga](https://github.com/liseami/CCBaga)：区域字典与地理代码匹配逻辑。
- [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev)：跨平台桌面客户端工程实践参考。

完整许可范围详见 [LICENSE](LICENSE.md)，依赖项来源与版权声明详见 [参考项目与许可](docs/参考项目与许可.md) 以及 [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt)。

---

<div align="center">

让每一次与 AI 的协作，都从容不迫。  
Empowering every AI interaction with confidence, privacy, and control.  
欢迎通过 [GitHub Issues](https://github.com/zhongyuanl/xiaofanchuan/issues) 提交反馈或 Star 支持！

</div>
