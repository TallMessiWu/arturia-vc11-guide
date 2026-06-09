# Arturia V Collection 11 Pro 插件图鉴

一个**单文件静态网页**，按 9 大家族系统介绍 Arturia V Collection 11 Pro 收录的全部 45 件乐器，并为每件乐器提供「为什么传奇」专栏与 6 个代表音色（含特点、感觉、适用曲风，以及原型硬件的经典曲目）。

## 项目结构

- `index.html` — **全部内容与代码都在这一个文件里**：内联 CSS + 原生 JS，无构建步骤、无依赖（仅 Google Fonts 走 CDN）。
- `.agents/` — Agent 指令与技能的**主目录**。
  - `.claude/skills` 是指向 `../.agents/skills` 的符号链接；`CLAUDE.md` 是指向 `AGENTS.md` 的符号链接。
  - 仓库 `core.symlinks=false`，符号链接在 Windows 下以文本文件落地、git mode 为 `120000`，clone 到 Linux/macOS 会还原成真链接。

## 本地预览

直接用浏览器打开 `index.html` 即可。或起静态服务器：

```powershell
python -m http.server 8000   # 然后访问 http://localhost:8000
```

## 部署

托管于 **GitHub Pages**，源为 `main` 分支根目录。推送到 `main` 后约 1 分钟自动发布。

## 主要功能

- **9 大家族分类**：电钢键盘、风琴、弦机磁带、经典模拟、复音模拟、数字/FM、Augmented、原创工具、启动器。
- **音色速查**：顶部可多选曲风做**交集**筛选，点结果跳转到对应插件。
- **分类折叠**：点分类标题收起 / 展开。

## 内容准则（编辑 `index.html` 时遵守）

- 「♪」曲目 = 该**原型硬件**做出过此类声音的公认关联，非逐音轨考据；**可疑 / 争议归属一律不收录**（宁缺毋滥）。
- 无单一硬件原型的现代乐器 / 工具（Augmented 系列、MiniFreak / MiniBrute、Pure Lo-Fi、Analog Lab）用「◆ 适合 / 参考」而非原型曲目。
- 物理建模乐器（Piano V）配「原声名曲」，按音色性格匹配。
- 乐器清单以 arturia.com 官方 V Collection 11 页面为准。
- 速查的曲风 / 预设映射数据在 `index.html` 末尾 `<script>` 的 `INST` 数组里，预设名须与正文一致。

## 提交规范

使用 **gitmoji-commit** 技能（见 `.agents/skills/gitmoji-commit/SKILL.md`）：中文 subject，格式 `<emoji-code> <type>(<scope>): <subject>`，默认单个 `-m`，不自动推送。
