# Arturia 收藏图鉴（V Collection 11 + FX Collection 6）

一个**单文件静态网页**，含两套图鉴，由页面顶部的 **V Collection ⇄ FX Collection 分段切换控件**切换：

- **V Collection 11 Pro**：按 9 大家族介绍全部 45 件乐器，每件含「为什么传奇」专栏 + 6 个代表音色（特点、感觉、适用曲风、原型硬件经典曲目）。
- **FX Collection 6 Pro**：按 9 大家族介绍全部 39 件效果器（外加购买即赠送的最新混响 **Rev OCEAN**，列于混响家族顶部、带「最新·赠送」徽标），每件含「为什么传奇/独到之处」专栏 + 6 个代表用法/预设（特点、适用对象/场景、硬件复刻类附经典案例）。v6 全新 5 款：Efx AMBIENT、Pitch SHIFTER-910、Tape J-37、Bus TRANSIENT、Mix DRUMS。

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

- **顶部视图切换**：header 里的 `.view-switch`（`#viewSwitch`）在 V / FX 两套图鉴间切换；JS 切换两个 `<main>`（`#view-v` / `#view-fx`）的 `hidden`、并同步 `#brand`、`document.title` 与两套 `nav.chips[data-nav]`。当前视图记忆在 `location.hash`（`#fx` / `#v`），默认 V。
- **9 大家族分类**：V = 电钢键盘 / 风琴 / 弦机磁带 / 经典模拟 / 复音模拟 / 数字FM / Augmented / 原创工具 / 启动器；FX = 混响 / 延迟 / 调制 / 滤波器 / 前置&EQ / 压缩 / 饱和&磁带 / 总线母带&混音 / 创意&音高。
- **速查（多选交集）**：V 按曲风、FX 按处理对象/用途；点结果跳转到对应卡片（折叠家族自动展开 + `flash` 高亮）。两套速查由同一个 `initQuickref(opts)` 按视图作用域各初始化一次。
- **分类折叠**：点分类标题收起 / 展开（两视图通用）。

## 内容准则（编辑 `index.html` 时遵守）

- 「♪」= 该**原型硬件**做出过此类声音/处理的公认关联（FX 为听感参考），非逐音轨考据；**可疑 / 争议归属一律不收录**（宁缺毋滥）。
- 无单一硬件原型的现代乐器 / 工具用「◆ 适合 / 参考」而非原型曲目：V 侧（Augmented 系列、MiniFreak / MiniBrute、Pure Lo-Fi、Analog Lab）；FX 侧（Rev OCEAN、Rev INTENSITY、Delay ETERNITY、四款 Filter、Dist COLDFIRE / OPAMP-21、Bus TRANSIENT / PEAK / FORCE、Mix DRUMS、Efx 全系列）。
- 物理建模乐器（Piano V）配「原声名曲」，按音色性格匹配。
- 清单以 arturia.com 官方页面为准（V Collection 11 / FX Collection 6，2026-06 核对）。**Rev OCEAN 非 FX Collection 6 的 39 件之一**，是购买即赠送的独立最新混响，仅作置顶展示并标「最新·赠送」。
- 速查映射数据在 `index.html` 末尾 `<script>`：V 在 `GENRES`/`INST`，FX 在 `FACETS`/`FX`；**预设/用法名须与正文 `snd-name` 完全一致**（可用脚本批量核对）。

## 提交规范

使用 **gitmoji-commit** 技能（见 `.agents/skills/gitmoji-commit/SKILL.md`）：中文 subject，格式 `<emoji-code> <type>(<scope>): <subject>`，默认单个 `-m`，不自动推送。
