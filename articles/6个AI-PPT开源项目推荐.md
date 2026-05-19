![封面图](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/covers/ai-ppt-tools-cover.png)

# 推荐 6 个火火火的 AI PPT GitHub 项目，尤其是第一个

AI 生成 PPT 这件事，折腾了快两年了。

说来说去大概有四条路线：套模板、出图片、生成网页演示稿、直接出原生可编辑的 PPTX。

前三条路都有硬伤，直到最近几个月，一批新项目把「原生可编辑」这个核心痛点真正打穿了。

今天推荐 6 个 GitHub 上能打到生产环境的开源 AI PPT 项目，Star 总和接近 5 万。

---

## 01 **PPT Master**

![PPT Master GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/ppt-master/01-github-homepage.png)

说白了，它就是让你拿到手的是**真正能改的** PPTX 文件。

不是图片，不是 PDF，是 PowerPoint 里能直接点进去改文字、调形状、换颜色的原生文件。

核心逻辑很直接：你把 PDF、Word、Markdown 或者一个网址丢给它，它分析内容、出设计、生成 SVG 中间文件，最后导出标准 PPTX。

**18.4k Star**，作者本人是天天跟 PPT 打交道的投资咨询工程师，所以这个项目从第一天就是「能用」导向的。

有几个细节很到位：

支持把任意你喜欢的 PPTX 文件提取成可复用模板，主题色、字体、母版结构全部保留。

生成过程中在 `http://localhost:5050` 实时预览，点任意元素输修改意见，AI 自动重写。

支持原生动画，页面切换和单元素入场动画都能直接出，PowerPoint 和 Keynote 原生适配。

还能基于演讲者备注生成语音旁白，直接导出 MP4 视频。

装起来很简单：

```bash
git clone https://github.com/hugohe3/ppt-master.git
cd ppt-master
pip install -r requirements.txt
```

然后选一个你顺手的 AI 工具（Claude Code、Cursor、VS Code + Copilot 都行），把源文件往 `projects/` 目录一放，聊天框输入指令即可。

输出的 PPTX 默认保存到 `exports/` 目录，同时备份 SVG 中间文件到 `backup/` 方便重新导出。

实话实说有几个门槛：需要本地跑 Python 环境，对纯小白不太友好；生成速度取决于你用的模型，用 GPT-Image-2 配 Claude 效果最好但成本也高；另外它依赖 AI Agent 来驱动，你得先有一个顺手的 AI 编程工具。

所以如果你要的是「打开网页、输入主题、30秒出稿」的那种极简体验，banana-slides 可能更合适。

    开源地址：https://github.com/hugohe3/ppt-master

---

## 02 **banana-slides**

![banana-slides GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/banana-slides/01-github-homepage.png)

这个项目基于 nano banana pro 🍌 模型，做的是真正的「Vibe PPT」——一句话生成，口头修改，直接出稿。

**14.6k Star**，是在线体验最完整的一个。

三种创建方式：一句话描述、大纲模式、逐页描述，AI 自动生成结构清晰的大纲和逐页内容。

改起来也直接：框选某个区域，说「把这块改成案例分析」，AI 实时响应调整，不用在一堆菜单里找功能。

支持上传参考图片或模板来定制整体风格，这点对品牌一致性要求高的场景很实用。

导出格式覆盖 PPTX（可编辑）、PDF、讲解视频（MP4 格式，带 AI 语音旁白和字幕）。

装起来有两种方式，最简单的直接用[在线版](https://bananaslides.online)，或者 Docker 一键部署：

```bash
# Docker Compose 部署（推荐）
git clone https://github.com/Anionex/banana-slides.git
cd banana-slides
docker compose up -d
```

源码部署需要 Python 3.10+ 和 Node.js 16+，前后端分别装依赖后启动即可。

实话实说：它依赖 nano banana pro 模型，模型访问需要合规的 API Key；另外可编辑 PPTX 导出是 Beta 状态，复杂排版还原度还在迭代。

所以如果你需要的是「拿出去就能给客户改」的原生文件，现阶段 PPT Master 更成熟。

    开源地址：https://github.com/Anionex/banana-slides

---

## 03 **guizang-ppt-skill**

![guizang-ppt-skill GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/guizang-ppt-skill/01-github-homepage.png)

这个项目的切入点很刁：它不是一个独立应用，而是一个**直接跑在 Claude Code / Codex 里的 Skill**。

**10.1k Star**，出品人是 op7418，在 AI Agent 圈子里这个 Star 数很有说服力。

核心价值：AI Agent 直接帮你生成单文件 HTML 横向翻页 PPT，浏览器打开就能演示，无需任何构建工具。

内置两套完全独立的视觉系统：

Style A 是电子杂志 × 电子墨水风，适合叙事、观点表达、个人风格分享。

Style B 是瑞士国际主义风格，严格网格、直角色块、无圆角无渐变，适合事实陈述、产品分析。

还支持生成多平台社交封面：公众号 21:9 头图、1:1 分享卡、小红书 3:4 封面，一套内容多出料。

安装只需要一行：

```bash
npx skills add https://github.com/op7418/guizang-ppt-skill --skill guizang-ppt-skill
```

然后在 Claude Code 里告诉它你要做什么主题的 PPT，它会引导你走完「选风格 → 填内容 → 预览 → 迭代」全流程。

实话实说：它目前不支持直接导出 PPTX，优先交付的是 HTML 格式；而且对颜色自定义有限制，只能从预设主题里选，这是为了保证风格统一性做的取舍。

所以如果你需要拿出去给不懂 HTML 的客户直接改，这个目前不太合适。

    开源地址：https://github.com/op7418/guizang-ppt-skill

---

## 04 **PPTist**

![PPTist GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/PPTist/01-github-homepage.png)

这个项目干的事不一样：它不是 AI 生成器，而是**在浏览器里复刻了一个 PowerPoint**。

**9000+ Star**，基于 Vue 3 + TypeScript，不依赖 UI 组件库，代码很干净。

说白了，你想在网页端编辑演示文稿，又不想用 Microsoft 365，这个就是最接近桌面级体验的开源方案。

功能覆盖很全：文本、图片、形状、线条、图表、表格、视频、音频、公式，该有的都有。

支持 AI 生成 PPT（基于模板的方案），也支持导入现有 PPTX 文件编辑（还原度约 70%-80%）。

快捷键、右键菜单、磁性对齐、元素动画、切换动画、演讲者视图，这些细节都做了。

装起来很简单：

```bash
git clone https://github.com/pipipi-pikachu/PPTist.git
cd PPTist
npm install
npm run dev
```

访问 `http://127.0.0.1:5173/` 就能用。

在线体验地址：https://pipipi-pikachu.github.io/PPTist/

实话实说：它的核心定位是 Web 幻灯片编辑/演示应用，不是专门的 AI PPT 生成器；PPTX 导入导出有局限性，如果需要高精度还原，这个要打个问号。

商用需要注意：AGPL-3.0 协议，闭源商用需要购买授权（一年 2999 元，永久 5699 元），或者改用 2022 年停止维护的 Apache 2.0 版本。

    开源地址：https://github.com/pipipi-pikachu/PPTist

---

## 05 **LandPPT**

![LandPPT GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/LandPPT/01-github-homepage.png)

这个项目的定位是**全流程 AI 自动化**，从主题输入到完整 PPT 生成全链路自动，一键出稿。

**3.2k Star**，最新版本 v0.3.1（2026 年 5 月 15 日发布），迭代很活跃。

有几个差异化亮点：

内置深度研究功能，集成 Tavily 和 SearXNG 双搜索引擎，自动获取最新相关信息补充内容——说白了就是 PPT 内容也能「联网搜索」了。

幻灯片内容并行生成，构建速度比逐页串行快不少。

支持导出格式很全：标准 PPTX、图片型 PPTX、PDF、HTML、讲稿 DOCX/Markdown，还能一键生成分享链接直接分发。

模型兼容性也做得好：OpenAI 全系列、Claude、Gemini、本地 Ollama，以及所有 OpenAI 兼容接口（DeepSeek、Moonshot、Qwen 等）都能接。

部署推荐 Docker Compose 一把梭：

```bash
git clone https://github.com/sligter/LandPPT.git
cd LandPPT
cp .env.example .env
docker compose up -d
```

默认访问 `http://localhost:6003`，配置好模型 API Key 就能用。

实话实说：功能比较全但每个模块的深度不如专项工具，比如配图质量不如专门接 DALL-E 的方案，动画支持也比较基础。另外需要自己部署，对服务器环境有一定要求。

所以如果你想要的是「开箱即用、不用自己部署」的体验，在线版 banana-slides 更合适。

    开源地址：https://github.com/sligter/LandPPT

---

## 06 **MultiAgentPPT**

![MultiAgentPPT GitHub 首页](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/MultiAgentPPT/01-github-homepage.png)

这个项目的技术架构最有意思：基于 **A2A + MCP + ADK** 多智能体协作架构来生成 PPT。

**1.6k Star**，思路是把 PPT 生成任务拆给多个 Agent 并行处理，效率和准确性都比单 Agent 方案高。

工作流是这样的：Outline Agent 生成大纲 → 拆分成多个主题 → 多个 Research Agent 并行调研 → Summary Agent 汇总 → Loop PPT Agent 逐页生成 → PPTChecker Agent 自动校验质量（最多重试 3 次）。

说白了，它把「内容质量把控」这件事交给了一个专门的 Agent，这比大多数方案只管生成不管校验要严谨。

支持流式返回，生成过程实时展示在前端界面，每个 Agent 的工作进度都能看到。

还能导出标准 PPTX 文件，基于 python-pptx 渲染。

⚠️ 注意：当前版本**不再维护**，作者推荐升级到新版本 [TrainPPTAgent](https://github.com/johnson7788/TrainPPTAgent)，架构更完整，适合企业化模板方案。

所以如果只是想试用一下多 Agent 思路，可以跑起来看看；如果要用于生产，直接看 TrainPPTAgent。

    开源地址：https://github.com/johnson7788/MultiAgentPPT

---

## 07 **点击下方卡片，关注阿福研习社**

这个公众号历史发布过很多有趣的开源项目，如果你懒得翻文章一个个找，你直接关注微信公众号：**阿福研习社** ，后台对话聊天就行了：

[公众号二维码图片]
