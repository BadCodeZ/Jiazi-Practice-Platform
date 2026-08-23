# 综合教资备考工作台 · 使用说明

**Comprehensive Teacher Certification Preparation Workbench · User Guide**

---

## English Version

### Overview

**jiazi-practice-platform** is a **single-file offline web application** for Chinese Teacher Certification (教师资格证) exam preparation. It runs entirely in your browser — no installation, no registration, no server required. All your study data stays on your own device.

- **Author**: BadCodeZ
- **Version**: V1.1 (meta 2.0) · SW artwb-v2
- **File**: `综合教资备考工作台.html` (2.95 MB)
- **Questions**: 3,342 built-in questions covering all exam subjects
- **Subjects**: 17 secondary school subjects (科三)
- **Repository**: https://github.com/BadCodeZ/jiazi-practice-platform

### Features

- **Offline-first**: Core practice, error review, mock exams, and knowledge cards all work without internet.
- **Cross-platform**: Works on desktop (Chrome/Edge) and mobile (browser → Add to Home Screen).
- **Full exam coverage**: Subject 1 (综合素质), Subject 2 (教育知识与能力), Subject 3 (学科知识与教学能力) across 17 subjects.
- **Smart error tracking**: Auto-categorize mistakes, intelligent review sessions.
- **Mock exams**: Weighted random sampling based on chapter importance.
- **AI commentary**: Optional integration with third-party AI providers for question explanations.
- **Multi-device sync**: WebDAV-based encrypted sync (AES-GCM) for backup and cross-device data transfer.
- **Lesson planning**: Built-in 12-element lesson plan editor with template library.
- **Knowledge cards**: Chapter-based review cards with spaced repetition reminders.
- **PDF/Word parsing**: On-demand parsing for uploaded documents (with offline fallback).

### How to Use

1. **Open the file**: Double-click `综合教资备考工作台.html` with Chrome or Edge.
2. **Set exam date**: Click "设置目标日" on the home page to set your target exam date.
3. **Start practicing**: Click "开始练习" or go to "练习" tab to select a practice mode.
4. **Review mistakes**: Automatically collected in "错题本" for targeted review.
5. **Sync (optional)**: Use WebDAV sync in Settings to transfer data between devices.

### Data Storage

- All data is stored in your browser's `localStorage` under key `artwb_v2_data`.
- No data is uploaded to any server.
- Clearing browser cache will delete your data — export regularly via Settings → Data Sync → Export.

### Technical Details

- **Build**: Single-file HTML (all CSS, JS, and data inlined)
- **MD5**: `7c10091b03f64b71083399b0a2c705cf`
- **PWA**: Service worker `artwb-v2` for offline caching (requires http(s) access)
- **Data format**: AES-GCM encrypted sync packages (`SYNCPKG1`)
- **Dependencies**: pdf.js, mammoth.js (loaded on demand for document parsing)

---

## 中文版

### 概述

**jiazi-practice-platform** 是一个**单文件离线网页应用**，用于教师资格证考试备考。它不需要安装、不需要注册、不需要服务器，打开浏览器就能用，所有学习数据只存在你自己的设备上。

- **作者**: BadCodeZ
- **版本**: V1.1（meta 2.0）· SW artwb-v2
- **文件**: `综合教资备考工作台.html`（2.95 MB）
- **题量**: 3342 道内置题，覆盖全部考试科目
- **学科**: 17 个科三学科
- **仓库地址**: https://github.com/BadCodeZ/jiazi-practice-platform

### 功能列表

- **纯离线使用**：核心刷题、错题本、模考、知识卡片全部不需要联网。
- **跨平台**：电脑（Chrome/Edge）和手机（浏览器→添加到主屏幕）均可使用。
- **全科覆盖**：科一（综合素质）、科二（教育知识与能力）、科三（学科知识与教学能力），支持 17 个学科方向。
- **智能错题本**：自动归类错因，按薄弱度排序组卷复习。
- **全科模考**：按章节权重加权随机抽题，模拟真实考试。
- **AI 讲评**：可选接入第三方 AI 服务，每题可生成详细讲解（需自备 Key）。
- **多端同步**：基于 WebDAV 的加密同步（AES-GCM），支持备份和跨设备数据迁移。
- **备课模块**：内置十二要素教案编辑器、模板库，支持课标库和教材库上传引用。
- **知识卡片**：按章节组织的复习卡片，支持到期复习提醒。
- **PDF/Word 解析**：按需加载第三方解析器，支持 `.docx` 和 `.pdf` 文件解析（离线环境降级为手动粘贴）。

### 如何使用

#### 快速上手（三步）

1. **打开文件**：双击 `综合教资备考工作台.html`，用 **Chrome 或 Edge** 打开。
2. **设置考试日期**：首页点击「设置目标日」，选择考试日期，首页出现倒计时。
3. **开始刷题**：首页点击「开始练习」或进入「练习」选项卡选择模式。客观题点选即判，主观题写要点看答案，答错后勾选错因（半强制至少选一项）。

#### 核心功能详细说明

**练习**
- 支持科一 / 科二 / 科三 + 学科选择
- 客观题点击选项立即判对错
- 主观题写要点后查看参考答案
- 答错题需勾选错因（≥1 项），用于后续智能组卷

**错题本**
- 按错因筛选和分组
- 智能组卷：按薄弱度降序排列，支持 seed 种子确保可复现
- 支持「仅复习错题」模式

**全科模考**
- 按 `CHAPTER_WEIGHT` 加权抽取约 50 题
- 科一 / 科二 / 科三 ≈ 33/33/34% 比例
- 不跨科三学科混出

**知识卡片**
- 按章节整理考点
- 可收藏标记
- 到期复习提醒

**AI 讲评**
- 设置中配置 provider + API Key
- 每题可请求 AI 分析讲解
- 无 Key 时自动使用离线样例兜底

**多设备同步**
- 设置 → WebDAV 配置
- 支持「仅上传 / 仅下载 / 双向合并」三种方向
- AES-GCM 加密（`SYNCPKG1` 格式）
- 同一 WebDAV 空间 + 同一口令即可互通

**备课模块**
- 十二要素教案编辑器（教学目标 / 重难点 / 教学过程 / 板书设计等）
- 模板库：预设教案模板，可直接套用
- 科三训练：按学科专项训练
- 中枢 Hub：统一管理备课资源
- 课标库 / 教材库：上传 `.txt/.md/.docx/.pdf` 文件，支持「从库插入」引用
- 课本「按课抽取」直达编辑器

**PDF / Word 按需解析**
- 课标库 / 教材库上传支持 `.docx`（mammoth 解析）和 `.pdf`（pdf.js 解析）
- 运行时按需加载，不增加初始加载体积
- 离线环境自动降级为手动粘贴
- `.caj` 文件提示先转 PDF

### 运行环境

- **推荐浏览器**：Chrome 或 Edge（Chromium 内核，视觉与门禁校验基于此）
- **手机**：用系统浏览器（不是微信内浏览器）打开，然后「分享 → 添加到主屏幕」
- **离线可用**：`file://` 双击也可打开，但不持久化；要持久化数据请通过 http 本地静态服务或托管访问

### 数据存储

- 所有数据存在浏览器 `localStorage`，键名为 `artwb_v2_data`
- 不联网、不上传任何服务器
- 清缓存 / 换浏览器 / 换电脑后数据不可见
- 分享 html 文件给他人，对方拿到的是空白工作台（不含你的数据）
- AI Key 单独存 `ai_key`，不进备份、不同步

### 数据迁移与备份

**导出同步包**
- 设置 → 数据同步 → 导出
- 复制生成的文本

**导入合并**
- 另一设备粘贴 + 同口令 → 解密合并
- 显示新增 / 更新数量

**WebDAV 同步**
- 可选配置，填同一空间 + 口令即可互通
- `localStorage` 为 null 时（如 `file://` 或隐私模式）自动降级为内存会话并提示

### FAQ

**Q: 打开后白屏？**
A: 请用 Chrome / Edge 打开。如果之前访问过旧版本，硬刷新一次（Ctrl+Shift+R）以绕过旧 PWA 缓存。

**Q: 数据丢失了怎么办？**
A: 用「导入同步包」恢复。检查是否换浏览器、清缓存或走 `file://` 未持久化。

**Q: 需要联网吗？**
A: 仅 AI 讲评和多端同步需要联网。核心刷题全离线。

**Q: 安全性如何？**
A: 纯本地运行，数据不上传。同步可选零知识加密（AES-GCM）。

**Q: 手机微信打不开？**
A: 微信内浏览器功能受限。请用系统浏览器打开并「添加到主屏幕」。

**Q: 如何切换科三学科？**
A: 设置中切换学科，题库和知识图谱随当前科三学科隔离。

**Q: PDF/Word 解析失败？**
A: 离线环境自动降级为手动粘贴。CAJ 文件请先转 PDF。

### 给分享者

- **单文件分发**：直接分享 `综合教资备考工作台.html` 一个文件即可（约 2.95 MB）
- **保留署名**：保留作者 **BadCodeZ** 与「正式版 V1.1」标识
- **覆盖 html 不影响用户数据**：用同名新 html 覆盖，浏览器 `localStorage` 中的 `artwb_v2_data` 不动，用户记录保留
- **版本线提醒**：网页端 V1（meta 1.0）与安卓端版本号互不对齐属正常，仅数据互通

### 技术规格

| 项目 | 值 |
|------|------|
| 文件 | 综合教资备考工作台.html |
| 大小 | 2.95 MB（3,097,824 字节） |
| MD5 | `7c10091b03f64b71083399b0a2c705cf` |
| 内部版本 | meta 1.0 |
| SW 版本 | artwb-v2 |
| 内置题量 | 3342 道 |
| 科三学科 | 17 个 |
| 数据键名 | `artwb_v2_data`（localStorage） |
| 同步格式 | `SYNCPKG1`（AES-GCM） |
| 设计主题 | 宣纸 / 水墨 / 青绿 / 朱砂印章 |

### 免责声明

1. 本工具为个人备考辅助，题库含 AI 批量生成题，个别解析 / 答案可能存在争议，正式考试以官方大纲与教材为准。
2. AI 功能依赖第三方 API，需自备 Key 并自担费用；结果仅供参考。
3. 数据存于本机浏览器，作者不对因清缓存 / 换设备 / 误操作导致的数据丢失负责；请定期导出备份。
4. PDF / Word 解析依赖运行时按需加载的第三方解析器（pdf.js / mammoth），联网首次解析、离线降级手动粘贴。
5. 本软件按「现状」提供，不提供任何明示或暗示的保证。