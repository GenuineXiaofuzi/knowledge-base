![封面图](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/covers/ai-ppt-tools-cover.png)

# 推荐 6 个火火火的 AI PPT GitHub 项目，尤其是第一个

AI 生成 PPT 折腾了快两年，四条路线里「原生可编辑 PPTX」最近才被真正打穿。

今天推荐 6 个能打到生产环境的开源 AI PPT 项目，Star 总和接近 5 万。

---

## 01 **PPT Master**

![PPT Master GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/ppt-master/01-github-homepage.png)
![PPT Master README](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/ppt-master/02-readme.png)
![PPT Master Demo](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/ppt-master/03-demo.png)

**核心价值**：生成真正可编辑的 PPTX 文件，不是图片也不是 PDF。

把 PDF/Word/Markdown/网址丢给它，分析内容 → 出设计 → 生成 SVG 中间文件 → 导出标准 PPTX。**18.4k Star**。

亮点：支持提取任意 PPTX 为可复用模板；`localhost:5050` 实时预览并支持 AI 迭代修改；支持原生动画和语音旁白导出 MP4。

安装：克隆仓库 → `pip install -r requirements.txt` → 用 AI 工具（Claude Code/Cursor/VS Code+Copilot）驱动。

门槛：需本地 Python 环境；生成速度取决于模型；依赖 AI Agent 驱动。

    开源地址：https://github.com/hugohe3/ppt-master

---

## 02 **banana-slides**

![banana-slides GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/banana-slides/01-github-homepage.png)
![banana-slides README](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/banana-slides/02-readme.png)
![banana-slides 在线体验](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/banana-slides/03-online-demo.png)

**核心价值**：基于 nano banana pro 🍌 模型，一句话生成、口头修改、直接出稿。

**14.6k Star**，在线体验最完整。三种创建方式（一句话/大纲/逐页描述），支持上传参考图定制风格，导出格式覆盖 PPTX/PDF/MP4。

在线版：https://bananaslides.online

部署：`git clone` → `docker compose up -d`

注意：依赖 nano banana pro 模型 API Key；PP TX 导出为 Beta 状态。

    开源地址：https://github.com/Anionex/banana-slides

---

## 03 **guizang-ppt-skill**

![guizang-ppt-skill GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/guizang-ppt-skill/01-github-homepage.png)
![guizang-ppt-skill README](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/guizang-ppt-skill/02-readme.png)
![guizang-ppt-skill 风格预览](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/guizang-ppt-skill/03-style-preview.png)

**核心价值**：直接跑在 Claude Code / Codex 里的 Skill，生成单文件 HTML 横向翻页 PPT。

**10.1k Star**。内置两套视觉系统：Style A（电子杂志×电子墨水风）和 Style B（瑞士国际主义风格）。支持生成多平台社交封面（公众号/小红书等）。

安装：`npx skills add https://github.com/op7418/guizang-ppt-skill --skill guizang-ppt-skill`

限制：不支持导出 PPTX，优先交付 HTML；颜色自定义有限制。

    开源地址：https://github.com/op7418/guizang-ppt-skill

---

## 04 **PPTist**

![PPTist GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/PPTist/01-github-homepage.png)
![PPTist README](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/PPTist/02-readme.png)
![PPTist Demo](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/PPTist/03-demo.png)

**核心价值**：在浏览器里复刻 PowerPoint，最接近桌面级体验的开源方案。

**9000+ Star**，基于 Vue 3 + TypeScript。功能覆盖文本/图片/形状/图表/表格/视频/音频/公式，支持 AI 生成 PPT（基于模板）和 PPTX 导入编辑。

在线体验：https://pipipi-pikachu.github.io/PPTist/

部署：`git clone` → `npm install` → `npm run dev`

商用注意：AGPL-3.0 协议，闭源商用需购买授权（一年 2999 元）。

    开源地址：https://github.com/pipipi-pikachu/PPTist

---

## 05 **LandPPT**

![LandPPT GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/LandPPT/01-github-homepage.png)
![LandPPT README](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/LandPPT/02-readme.png)
![LandPPT 功能展示](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/LandPPT/03-features.png)

**核心价值**：全流程 AI 自动化，从主题输入到完整 PPT 一键出稿。

**3.2k Star**，最新 v0.3.1（2026-05-15）。内置深度研究功能（集成 Tavily/SearXNG），幻灯片内容并行生成，支持导出 PPTX/PDF/HTML/讲稿。

模型兼容性强：OpenAI 全系列/Claude/Gemini/本地 Ollama/所有 OpenAI 兼容接口。

部署：`git clone` → `cp .env.example .env` → `docker compose up -d`，访问 `http://localhost:6003`

    开源地址：https://github.com/sligter/LandPPT

---

## 06 **MultiAgentPPT**

![MultiAgentPPT GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/MultiAgentPPT/01-github-homepage.png)
![MultiAgentPPT README](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/MultiAgentPPT/02-readme.png)
![MultiAgentPPT 架构图](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/MultiAgentPPT/03-architecture.png)

**核心价值**：基于 A2A + MCP + ADK 多智能体协作架构生成 PPT。

**1.6k Star**。工作流：Outline Agent 生成大纲 → 多 Research Agent 并行调研 → Summary Agent 汇总 → Loop PPT Agent 逐页生成 → PPTChecker Agent 自动校验。

⚠️ **不再维护**，作者推荐升级到 [TrainPPTAgent](https://github.com/johnson7788/TrainPPTAgent)。

    开源地址：https://github.com/johnson7788/MultiAgentPPT

---

## 07 **点击下方卡片，关注阿福研习社**

这个公众号历史发布过很多有趣的开源项目，如果你懒得翻文章一个个找，你直接关注微信公众号：**阿福研习社** ，后台对话聊天就行了：

[公众号二维码图片]
