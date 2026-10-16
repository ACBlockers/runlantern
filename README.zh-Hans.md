<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/icon-dark.png">
    <img src="assets/icon-light.png" width="128" height="128" alt="守夜人图标：一只咖啡杯，杯上升起一缕金色蒸汽">
  </picture>
</p>

<h1 align="center">守夜人 Runlantern</h1>

<p align="center">
  <strong>AI 编码代理工作时，让 Mac 保持清醒。</strong><br>
  一款免费的菜单栏工具：Claude Code、Codex、Aider、Gemini CLI 忙着的时候阻止 Mac 空闲休眠，干完活就退到一边。
</p>

<p align="center">
  <a href="https://apps.apple.com/app/id6813276551?l=zh-Hans-CN"><img alt="在 Mac App Store 免费下载" src="https://img.shields.io/badge/Mac_App_Store-%E5%85%8D%E8%B4%B9-243b4c?style=for-the-badge&logo=apple&logoColor=white"></a>
</p>

<p align="center">
  <img alt="需要 macOS 15 或更高版本" src="https://img.shields.io/badge/macOS-15%2B-5d6c74?style=flat-square">
  <img alt="支持 Apple 芯片与 Intel" src="https://img.shields.io/badge/Apple_%E8%8A%AF%E7%89%87_%2B_Intel-%E9%80%9A%E7%94%A8-5d6c74?style=flat-square">
  <img alt="简体中文与英文" src="https://img.shields.io/badge/%E8%AF%AD%E8%A8%80-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87_%C2%B7_English-5d6c74?style=flat-square">
  <img alt="隐私：未收集数据" src="https://img.shields.io/badge/%E9%9A%90%E7%A7%81-%E6%9C%AA%E6%94%B6%E9%9B%86%E6%95%B0%E6%8D%AE-287054?style=flat-square">
</p>

<p align="center">
  <a href="README.md">English</a> ·
  <a href="https://runlantern.pages.dev/">官网</a> ·
  <a href="https://runlantern.pages.dev/privacy/">隐私说明</a>
</p>

<p align="center">
  <img src="assets/zh-1-agent.jpg" width="860" alt="Claude Code 工作时，守夜人自动守护">
</p>

## 能做什么

- **代理干活时自动守护。** 选择“随代理”，受监视的命令行工具一开始忙，守夜人就开始守护；工具退出或安静下来，过完你设定的宽限时间就结束。
- **也可以自己决定。** 自定义倒计时、无限时长，以及可选的“屏幕常亮”。
- **说关就关。** 关闭守护后，所有自动开始都会暂停，重启应用依然有效，直到你重新打开。
- **安全保护。** 电量阈值、温度保护和最长会话时长；系统温度压力达到临界时一定结束守护。
- **状态如实显示。** 如果系统没有确认电源请求或释放成功，面板会直接告诉你，不显示假状态。
- **只在你的 Mac 上工作。** 无需账号，不联网，不做统计；App Store 隐私标签为“未收集数据”。

<details>
<summary><strong>更多图片</strong></summary>
<br>
<p align="center"><img src="assets/zh-2-manual.jpg" width="860" alt="手动守护，30 分钟倒计时"></p>
<p align="center"><img src="assets/zh-3-automation.jpg" width="860" alt="自动化设置：监视的工具、静默窗口与宽限时间"></p>
<p align="center"><img src="assets/zh-4-safety.jpg" width="860" alt="安全设置：电量、温度与最长会话"></p>
</details>

## 工作原理

- **识别代理。** 按可执行文件名匹配受监视的工具；通过 `node`、Python 启动的工具，按它运行的脚本识别。
- **判断在忙。** 工具的进程树 CPU 占用超过 1% 就算在忙；安静超过静默窗口、再过完宽限时间后结束守护。
- **保持清醒。** 只用一条公开的 IOKit 电源断言 `PreventUserIdleSystemSleep`，开启“屏幕常亮”时再加 `PreventUserIdleDisplaySleep`。在 `pmset -g assertions` 里看得到，会话结束即释放。
- **不碰的东西。** 合上盖子或主动选择“睡眠”时仍按 macOS 的行为；不修改你的电源设置。

使用 SwiftUI 与 AppKit 开发；启用 App 沙盒，通用二进制，1.6 MB。

## 系统要求

macOS 15 或更高版本，Apple 芯片或 Intel 处理器。

## 支持

先看[官网的常见问题](https://runlantern.pages.dev/#questions)，或发邮件到 **ac_block@outlook.com**，写明应用版本、macOS 版本和出问题前的操作。

---

<sub>这个仓库是项目主页，不包含源代码。图片是按应用界面绘制的展示图，图中的时间均为示例。守夜人与 Anthropic、OpenAI、Google 及 Aider 的开发者没有隶属关系。</sub>
