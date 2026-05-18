# 一键多平台发文工具推荐文章 - GitHub项目分析

> 对话日期：2026-05-18
> 分类：GitHub
> 标签：#GitHub #开源工具 #自媒体 #内容分发 #Wechatsync #SyncCaster #公众号写作

## 核心内容

本次对话完成了两件事：

1. **按「逛逛GitHub」风格撰写文章**：分析两个跨平台文章同步开源工具（Wechatsync + SyncCaster），输出符合逛逛GitHub写作DNA的Markdown文章
2. **生成16:9封面图**：调用混元生图API，生成纯黑背景+白色粗体「一键分发」的极简封面

## 项目对比

| 维度 | Wechatsync | SyncCaster |
|------|-------------|-------------|
| Star数 | 5.5k | 362 |
| 支持平台 | 29+ | 17+ |
| 核心定位 | 覆盖广、平台多 | 编辑体验好、内置MD编辑器 |
| 安全机制 | 本地运行、无需账号密码 | 本地运行、Cookie管理 |
| MCP支持 | ✅ 支持Claude Code/OpenClaw | ❌ 无 |
| 技术栈 | TypeScript + pnpm monorepo | Vue 3 + TypeScript + Vite |
| 开源协议 | GPL-3.0 | MIT |
| 最近更新 | 2026-03 | 2026-05 |

## 文章输出

- 文件路径：`/Users/lifang/WorkBuddy/2026-05-18-task-37/一键多平台发文工具推荐.md`
- 封面图：`/Users/lifang/WorkBuddy/2026-05-18-task-37/cover_16x9_1280x720.png`
- 写作风格：严格遵循逛逛GitHub风格（三句开头、无AI八股文词汇、固定结尾引流）

## 封面图生成记录

- API：混元生图（buddy-cloud.py image）
- 分辨率：1280×720（16:9，受API限制宽×高≤1048576）
- Prompt：纯黑背景，白色无衬线超粗字体「一键分发」，无装饰
- 生成任务ID：`1379431822-1779119357-2068bbdf-52d1-11f1-be99-5254005f4655-0`

## 待完善

- [ ] 替换文章中的 `placeholder_screenshot_1` 和 `placeholder_screenshot_2` 为真实项目截图
- [ ] 如需真正1920×1080封面，可将现有1280×720图无损放大
- [ ] 公众号二维码图片需用户自行替换 `[公众号二维码图片]` 占位符

## 后续行动

- 将文章发布到「阿福研习社」公众号
- 考虑将 Wechatsync 的 MCP 能力接入现有工作流
- 评估 SyncCaster 的编辑器能力是否可集成到公众号写作流程

---

**元数据**
- WorkBuddy会话：2026-05-18-task-37
- 本地路径：`/Users/lifang/Documents/Knowledge-Base/GitHub/2026-05-18-Wechatsync-SyncCaster-Article.md`
- 技能使用：guangguang-github-writer、多模态内容生成、knowledge-sync
