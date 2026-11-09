<div align="center">

# 净屏

**开屏广告、弹窗广告，打开就没了。**

[![release](https://img.shields.io/github/v/release/MY-moss/jingping?style=flat-square&color=14624F&label=release)](https://github.com/MY-moss/jingping/releases/latest)
[![downloads](https://img.shields.io/github/downloads/MY-moss/jingping/total?style=flat-square&color=14624F&label=downloads)](https://github.com/MY-moss/jingping/releases)
[![android](https://img.shields.io/badge/Android-7.0%2B-14624F?style=flat-square&logo=android&logoColor=white)]()
[![size](https://img.shields.io/badge/APK-%E7%BA%A6%20315%20KB-14624F?style=flat-square)]()

<br>

<a href="https://github.com/MY-moss/jingping/releases/latest">
  <img src="https://img.shields.io/badge/%E4%B8%8B%E8%BD%BD%E6%9C%80%E6%96%B0%E7%89%88-14624F?style=for-the-badge&logo=android&logoColor=white" alt="下载最新版" height="42">
</a>

<br><br>

<img src="./preview.png" width="100%" alt="净屏界面预览">

</div>

> 本仓库只发布 APK，**不包含源代码**。

## ✨ 特点

- **2110 条严格生效规则**，覆盖 676 个应用；规则库编译后 2935 条 / 749 个应用，开屏 / 全屏 / 局部 / 分段四类独立开关
- **四页结构**：概览 / 战绩 / 规则 / 设置；首页支持经典 / 专注 / 紧凑三套样式
- **战绩看得见**：30 天热力图、判准率、节省时间、误跳转与误报统计
- **界面快照 + 观察模式**：误点可回放节点树，新规则可以先只看不点
- **GKD 选择器**：链式、正则、多条件 AND、`vid`、`activityIds` 等常用语法；少数表达式断言会安全丢弃
- **按应用调控 / 白名单**：逐条关闭规则，或只处理勾选的应用
- **常用规则优先**：命中越多的规则排得越前，下次更快命中
- **多源更新**：清单 4 路并发、安装包 6 源测速、sha256 校验
- **反馈刚刚好**：半透明「angela吃掉了广告」气泡，可选短震
- **轻量离线**：约 315 KB，无账号、无广告 SDK、不上传界面内容

## ⬇️ 安装

1. 下载最新的 `JingPing-*.apk`
2. 允许「安装未知来源应用」并安装
3. 打开净屏 → 开启无障碍服务
4. 建议顺手关闭电池优化，并在系统里允许自启动 / 后台运行

> Android 13+ 如果无障碍开关是灰的：应用信息 → 右上角三点 → 允许受限制的设置。

## 🔄 更新

- **1.5.0 起**：设置 → 关于与更新 → 检查更新，自动读取本仓库的最新 Release。
- **1.9.9**：规则页默认收起、快照删除/停用 App、备份预览与回滚；同时保留规则语义和点击结果确认修复。`n- **1.9.8**：多源更新、sha256 校验、更新失败保留旧规则。
- 更早的版本没有更新检查，需要手动安装一次 1.5.0。

## ❓ 常见问题

**广告还会加载吗？**

会。净屏是「秒跳」：广告刚开始显示就被点掉，声音和画面基本来不及出现，但仍会消耗少量流量。想从源头拦截，可以配合私人 DNS（`dns.adguard-dns.com`）。

**无障碍被系统关掉了？**

设置 → 系统权限 → 后台保活指南。净屏在被关闭时会发一条通知，点通知即可回来重新开启。

**不小心点错了？**

规则 → 工具 → 界面快照，选最近一次记录，用规则原文回放；确认是误报可点「这条点错了」。
也可以到 设置 → 运行记录看日志，再到 规则 → 按应用管理 单独关掉那条规则。

## 🔒 隐私

- 无账号、无统计、无上报
- 只读取当前界面的控件文字、描述和位置，用于匹配规则
- 日志只保存在本机，可随时清空
- 界面快照默认关闭；开启后只存本机节点树，最多 12 份，输入框/密码附近文字脱敏，不包含截图
- 联网仅用于规则订阅和 GitHub 检查更新

## ⚠️ 免责声明

> **仅供学习与技术研究使用，请勿用于商业用途。**

- 不注入、不 Hook、不修改任何第三方应用，只通过系统无障碍接口代替你点击界面上已有的按钮。
- 自动点击可能误触，请在「应用管理」中排除银行、支付、证券等敏感应用，后果自负。
- 软件按「现状」提供，不附带任何担保；使用者需自行遵守当地法律与所用应用的用户协议。
- 规则的版权归各订阅作者，本项目只做本地加载与解析。
- 与李跳跳、GKD、SKIP 等项目及其作者无隶属或合作关系。

## 🙏 参考的开源项目与采用方案

| 项目 | 借鉴的方案 | 落地情况 |
| --- | --- | --- |
| [GKD](https://github.com/gkd-kit/gkd) | 选择器语法（链式、`@`、`&&` / `\|\|` / `!`、`vid`、`matches`）与规则字段 `matchTime` / `actionMaximum` / `actionCd` / `resetMatch` / `position` | 纯 Java 重写解析与匹配，未复制源码 |
| SKIP | JSON 格式 `packageName` + `skipIds` / `skipBounds` | 兼容 `skipIds`；`skipBounds` 为固定分辨率坐标，已忽略 |
| 李跳跳 | 无障碍常驻 + 关键词兜底 + 跳过即时反馈 | 仅借鉴交互思路，实现自写 |

## 📄 授权与使用条款

本项目采用源可见、非商业、个人学习许可；**本发布仓库只提供 APK，不随仓库分发源代码**：

- 可以在获得源码后阅读、学习、编译、修改，在自己的设备上使用。
- 不可以：商业使用、二次分发、去除署名与免责声明。
- 不提供任何担保与技术支持。

完整条款见 [`LICENSE`](./LICENSE)。未用 MIT / GPL / CC：前两者与本项目只发布 APK 的方式不匹配，CC 不适合软件；若想换成标准文本，用 PolyForm Noncommercial 1.0.0。规则数据的版权归各订阅作者。

---

<div align="center">

如果它帮你省下了几秒钟，点个 ⭐ 就好。

</div>
