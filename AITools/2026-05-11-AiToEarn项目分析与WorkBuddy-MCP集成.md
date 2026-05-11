# AiToEarn 项目分析与 WorkBuddy MCP 集成

> 对话日期：2026-05-11
> 分类：AITools
> 标签：#AiToEarn #MCP #WorkBuddy #内容变现 #easy-vibe #商业化

## 核心内容

### AiToEarn 项目概况

- **项目名**：[AiToEarn](https://github.com/yikart/AiToEarn) — OPC（一人公司）的 AI 内容营销智能体
- **协议**：MIT（可商用、可修改、可销售，仅需保留版权声明）
- **一句话定位**：AI 驱动的多平台内容变现中台
- **覆盖平台**：抖音、小红书、快手、B站、TikTok、YouTube、Facebook、Instagram、Threads、Twitter/X、Pinterest、LinkedIn（12个平台）

### 四大核心 Agent

| Agent | 功能 | 说明 |
|-------|------|------|
| 💰 **Monetize** | 内容赚钱 | 接商家推广任务，CPS/CPE/CPM 结算 |
| 📢 **Publish** | 内容发布 | 一键分发到12个平台 + 日历排期 |
| 💬 **Engage** | 内容互动 | 自动点赞/评论/回复/品牌监控（需浏览器插件） |
| 🎨 **Create** | 内容创作 | AI 自动生成视频/图文内容 |

### MCP 集成到 WorkBuddy

**配置方式**：在 `~/.workbuddy/mcp.json` 中新增 AiToEarn 的 MCP 服务配置

```json
{
  "mcpServers": {
    "aitoearn": {
      "type": "http",
      "url": "https://aitoearn.cn/api/unified/mcp",
      "headers": {
        "x-api-key": "ak_X6yPO71MUXcJOMwyuobMnnRu6eL0exs2jWyFUKXphxbXDNoR"
      }
    }
  }
}
```

注意：使用 `curl` 测试时需添加 `Accept: application/json, text/event-stream` header，否则返回 406。

**MCP 端点测试**：
- 端点：`https://aitoearn.cn/api/unified/mcp`
- 方法：POST (JSON-RPC)
- 认证：`x-api-key` header
- 已验证可用，共暴露 109 个 tools

**可用 MCP 工具分类（完整 109 个）**：
1. 账号管理（查询账号组、账号列表、账号详情）
2. 内容发布（公众号、B站、抖音、YouTube、Twitter/X、Instagram、Pinterest、Threads、TikTok、快手、Facebook）
3. 内容创作（AI生成视频草稿、AI生成图文草稿）
4. 赚钱任务（任务市场浏览、接单、提交、查余额、查积分）
5. Twitter/X 全套运营（搜索、发推、回复、关注/粉丝管理、点赞、收藏、书签、屏蔽）
6. 推广分销（邀请链接、佣金查询、结算）
7. 媒体和草稿管理（上传、创建、查询、删除）
8. 品牌活动（浏览、报名、提交内容）
9. 数据看板（任务数据、趋势）

### easy-vibe 项目分析

- **项目**：[easy-vibe](https://github.com/datawhalechina/easy-vibe) — Datawhale 的 Vibe Coding 教程
- **协议**：CC BY-NC-SA 4.0（署名-非商业-相同方式共享）
- **核心结论**：**不可直接商用**（NC条款禁止商业用途），需自己独立实现差异化教程
- **差异化方向**：聚焦国内中文开发者，用豆包/Trae/Marscode 替代 Cursor/Claude，用微信支付替代 Stripe，用国内云厂商替代 Vercel

### 推荐商业方案

**AiToEarn** 推荐走"私有化部署+解决方案销售"路线（MIT 协议允许）：
- 🏆 优先度最高：Docker 私有部署 → 包装成"AI内容自动化解决方案"卖给商家/MCN/品牌
- 🚀 立即见效：接入 WorkBuddy 后，实现内容全自动分发（公众号+CSDN+多平台）
- 💰 增值方案：基于源码二次开发，加 Agent 工作流，做成商用增值版

**easy-vibe** 建议作为学习参考，商业教程需完全原创。

## 详细记录

### 关键操作
1. `git clone https://github.com/datawhalechina/easy-vibe.git` → `~/Desktop/个人规划/VibCoding/easy-vibe/`
2. `git clone https://github.com/yikart/AiToEarn.git` → `~/Desktop/个人规划/VibCoding/AiToEarn/`
3. 配置 `~/.workbuddy/mcp.json`，加入 AiToEarn MCP 服务
4. 验证 MCP 端点 `https://aitoearn.cn/api/unified/mcp`
5. 确认 API Key 有效，获取到 109 个 tools

### 易踩坑点
- MCP HTTP 端点要求 `Accept: application/json, text/event-stream`，否则返回 406
- API Key 分中国版（cn）和国际版（ai），必须匹配对应域名
- 中国版 Key 配国际版域名会返回 401

## 后续行动
- [ ] 在 aitoearn.cn 上绑定社交媒体账号（公众号、小红书、CSDN 等）
- [ ] 尝试用 MCP 发布第一篇内容到公众号或 CSDN
- [ ] 探索 AiToEarn 的任务市场看看有哪些赚钱任务可接
- [ ] 评估是否需要 Docker 私有部署

---

**元数据**
- WorkBuddy会话ID：当前对话
- 本地路径：`/Users/lifang/Documents/Knowledge-Base/AITools/2026-05-11-AiToEarn项目分析与WorkBuddy-MCP集成.md`
