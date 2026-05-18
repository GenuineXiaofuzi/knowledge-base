# 创建 guangguang-github-writer Skill - 逛逛GitHub写作风格蒸馏

> 对话日期：2026-05-18
> 分类：WorkBuddy技能开发
> 标签：#skill创建 #女娲 #写作风格 #GitHub #公众号

## 核心内容

使用女娲（nuwa-skill）完成了「逛逛GitHub」公众号写作风格的蒸馏，并打包成可复用的 WorkBuddy Skill。

### 完成的工作

1. **撰写跨平台文章同步工具推荐文章**
   - 基于 Wechatsync 和 SyncCaster 两个开源项目
   - 生成 3000 字左右的公众号文章
   - 应用 humanizer-zh 去 AI 味处理（v2 版本）

2. **创建 guangguang-github-writer Skill**
   - 使用女娲 Skill 进行多维度调研
   - 5个并行 Agent 收集信息（文章样本/风格DNA/封面设计/读者反馈/发布规律）
   - 完整工作流：Phase 0 → Phase 5（双Agent精修）
   - 输出完整的 SKILL.md 和 10 个调研文件

3. **Skill 特点**
   - 3个标题公式 + 三句开头 + 六步法结构 + 固定结尾
   - 30+ 高频词汇 + 10+ 禁忌词（去AI味）
   - 封面设计指南（3个构图模式 + AI生图提示词模板）
   - 风格自检清单（7个检查模块/28个检查项）

## 详细记录

### 1. 文章撰写

**输入**：
- GitHub项目链接：wechatsync/Wechatsync、RyanYipeng/SyncCaster
- 参考风格：逛逛GitHub公众号

**输出**：
- `跨平台文章同步工具推荐.md`（v1：3146字）
- `跨平台文章同步工具推荐-v2.md`（v2去AI味：3012字）

**文章结构**：
```
01 Wechatsync（5.5k Star，29+ 平台，API 方案）
02 SyncCaster（362 Star，17+ 平台，LaTeX/Mermaid 支持）
对比表格 + 选择建议
结尾引流
```

### 2. Skill 创建流程

**女娲工作流**：

| 阶段 | 内容 | 输出 |
|------|------|------|
| Phase 0 | 入口路由 | 识别为"写作风格蒸馏"任务 |
| Phase 0.5 | 创建skill目录 | `~/.workbuddy/skills/guangguang-github-writer/` |
| Phase 1 | 多源信息收集（5个并行Agent） | `references/research/01-05.md` |
| Phase 1.5 | 调研质量审查 | 发现"读者反馈"信息不足，标注为推测 |
| Phase 2 | 框架蒸馏 | 标题公式/开头结构/文章模板/结尾DNA |
| Phase 3 | Skill构建 | 生成完整的 SKILL.md |
| Phase 4 | 质量验证（3个测试Agent） | 标题生成测试/边缘情况测试/风格检查测试 |
| Phase 5 | 双Agent精修 | auto-skill-optimizer（8维度评估）+ skill-creator（可操作性审查） |

**Phase 1 调研结果**：

1. **文章样本分析**（5篇文章）
   - 标题公式：数字冲击 + 情绪动词 + 价值主张
   - 开头结构：三句话黄金法则（零寒暄）
   - 段落节奏：一段一事，短句为主（≤25字）
   - 结尾DNA：固定引流话术，无总结段

2. **风格DNA分析**（30+ 高频词，10+ 禁忌词）
   - 高频词：说白了/其实/直接/真的/基本上/但/不过/当然/实话实说
   - 禁忌词：首先/此外/值得注意的是/综上所述/总而言之/然而/因此/由此可见/毋庸置疑/显而易见
   - 技术圈网络用语：白嫖/折腾/起飞/狂揽/火火火

3. **封面设计分析**（15张封面图）
   - 色彩方案：纯黑(#000000) + 纯白(#FFFFFF) + 项目品牌色点缀（<15%）
   - 字体选择：无衬线粗黑体（PingFang SC Heavy / Noto Sans SC Black）
   - 构图模式：左右分割（47%）/ 中心聚焦（40%）/ 对称极简（13%）
   - 信息层级：只保留核心识别词，无公众号名称/副标题/日期

4. **读者反馈分析**（信息不足，标注为推测）
   - 无法获取微信公众号原文章评论区
   - CSDN博客评论区无有效反馈

5. **发布规律分析**
   - 文章长度：2500-3500字
   - 项目选择偏好：实用工具 > AI项目 > 开发者工具
   - 数字使用规则：精确数字（1.6万人/476 tokens/s），不用"最强""第一"

**Phase 5 改进（6项）**：

根据双Agent精修反馈，对 SKILL.md 进行 6 项改进：

1. **扩展触发词列表**（5 → 16个）
   ```yaml
   trigger: ["github.com", "GitHub链接", "写一篇GitHub", "写一篇开源", 
             "推荐项目", "推荐几个GitHub", "推荐本周", "推荐几个开源", 
             "写一篇项目介绍", "GitHub项目推荐", "帮我写一篇", 
             "按逛逛风格", "用逛逛风格", "狂揽", "火火火", "起飞了", "盘点"]
   ```

2. **新增触发策略**（trigger_policy）
   - 强制触发：含 `github.com` 链接、含「写一篇GitHub」「写一篇开源」「推荐项目」
   - 建议触发：含「推荐几个」「本周最火」「盘点」
   - 不触发：含「帮我用学术风格」「用正式语气」

3. **新增错误处理规则**（Step 2）
   - WebFetch 失败/超时 → 明确输出「信息不足：无法抓取项目页面」
   - 项目README无Star数/核心功能 → 搜索补充，无果则标注「数据缺失」

4. **新增序号自动计算规则**
   - 单项目文章：01=是什么，02=原理/特点，03=说实话的短板，04=怎么上手
   - 多项目合集：01=第1个项目，02=第2个项目...
   - 结尾引流模块的序号根据前文模块数自动计算

5. **新增二维码占位符说明**
   - `[公众号二维码图片]` 为占位符
   - 实际使用时需替换为真实的公众号关注二维码图片路径
   - 如用户未提供，生成文章时先输出文字引流话术，提示用户自行添加二维码图片

6. **新增风格检查清单**（7个检查模块/28个检查项）
   - 标题检查（4项）
   - 开头检查（4项）
   - 段落节奏检查（4项）
   - 表达DNA检查（3项）
   - 结尾检查（3项）
   - 价值观检查（3项）
   - 封面图检查（4项）

### 3. 最终产出

**Skill 文件**：
- `~/.workbuddy/skills/guangguang-github-writer/SKILL.md`（完整技能定义）
- `~/.workbuddy/skills/guangguang-github-writer/references/research/` （10个调研文件）

**Skill 使用方式**：
```
用户输入：https://github.com/用户名/项目名
         写一篇推荐文章

Skill执行：
1. 用WebFetch抓取GitHub项目页面（README）
2. 提取项目信息（名称/Star数/功能/安装方式）
3. 搜索项目评测（补充优缺点）
4. 按写作框架生成文章（标题公式 + 三句开头 + 六步法结构 + 固定结尾）
5. 可选：生成封面图提示词（按封面设计指南）
```

**触发词**（16个）：
- GitHub链接相关：github.com / GitHub链接
- 写作请求：写一篇GitHub / 写一篇开源 / 写一篇项目介绍 / GitHub项目推荐 / 帮我写一篇
- 推荐请求：推荐项目 / 推荐几个GitHub / 推荐本周 / 推荐几个开源
- 风格指定：按逛逛风格 / 用逛逛风格
- 逛逛GitHub特色词汇：狂揽 / 火火火 / 起飞了 / 盘点

## 后续行动

- [ ] 测试 skill 是否正常工作（输入一个GitHub链接，检查输出是否符合逛逛GitHub风格）
- [ ] 如需要，将 skill 从 `~/.workbuddy/skills/` 移动到项目级 `.workbuddy/skills/` 目录
- [ ] 定期（每3-6个月）重新调研更新，因为逛逛GitHub的写作风格可能随时间演化

## 关键发现

1. **女娲Skill的有效工作流**：Phase 0 → Phase 5 的完整流程可以系统地蒸馏任意公众号/作者的写作风格
2. **多Agent并行调研的重要性**：5个Agent分别收集不同维度的信息，最后汇总分析，比单次调研更全面
3. **双Agent精修的价值**：auto-skill-optimizer（8维度评估）+ skill-creator（可操作性审查）能发现单人审查忽略的问题
4. **风格检查清单的必要性**：生成文章后逐项检查，确保输出符合目标风格，避免"形似神不似"

---

**元数据**
- WorkBuddy会话ID：5b56c77b-2751-4746-98ad-d0844dfc96c4
- 本地路径：`/Users/lifang/Documents/Knowledge-Base/WorkBuddy/2026-05-18-guangguang-github-writer-skill.md`
- GitHub仓库：`https://github.com/GenuineXiaofuzi/knowledge-base/blob/main/WorkBuddy/2026-05-18-guangguang-github-writer-skill.md`
