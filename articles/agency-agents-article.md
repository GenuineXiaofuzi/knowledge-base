![封面图](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/covers/agency-agents-cover.png)

# GitHub 上狂揽 10 万 Star！这个 AI 代理机构集合，144+ 专项代理随你调用。

agency-agents 把一整个 AI 代理机构拆成了 144+ 个专项代理，每个都有独立人格和可交付成果。

这个项目在 GitHub 上已经狂揽 10 万 Star，被 16000+ 人复刻，社区非常活跃。

说白了，你不用再为不同任务切换不同 AI 工具，这一套就够。

## 01 **agency-agents 是什么**

![项目效果图](https://raw.githubusercontent.com/GenuineXiaofuzi/knowledge-base/main/images/screenshots/agency-agents/01-github-homepage.png)

agency-agents 是一个开箱即用的完整 AI 代理机构集合，包含了从前端开发、后端架构、UI 设计、营销推广、广告投放、项目管理到游戏开发、学术研究等全领域的专业 AI 代理。

每个代理都具备鲜明专业属性：非通用模板，拥有专属工作流、可量化的交付成果和质量评估标准，经过生产环境验证。

目前项目包含 144+ 个 AI 专项代理，覆盖 12 个专业领域，包括工程、设计、营销、销售、游戏开发、学术等方向。

开源地址：https://github.com/msitarzewski/agency-agents

## 02 **核心特点**

**多工具集成。** 支持原生适配 Claude Code、GitHub Copilot、Cursor、Windsurf 等 11 款主流 AI 编码工具，提供一键转换和安装脚本。

**灵活组合。** 小到 MVP 开发、营销活动上线，大到企业级功能交付、全渠道广告账户接管，都可以通过匹配对应领域的代理完成高质量交付。

**生产验证。** 每个代理都经过生产环境验证，不是实验室里的玩具，而是真正能干活专家。

## 03 **说实话的短板**

有个说法叫说清楚自己不适合什么，比说自己能干什么更重要。

agency-agents 有几个明显的短板：

**需要配置环境。** 虽然提供了一键安装脚本，但是首次配置仍然需要一些环境依赖，大约需要 15 分钟。

**代理数量多，选择困难。** 144+ 个代理，新手可能不知道该用哪个，需要一定的学习成本。

**某些代理可能不适合所有场景。** 比如某些工程代理可能更适合特定技术栈，通用性有局限。

所以如果你要的是开箱即用、零配置的 AI 工具，那 agency-agents 可能不适合你。

## 04 **怎么上手**

整个过程非常直接：

**第一步：** 克隆仓库到本地。

```bash
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents
```

**第二步：** 运行安装脚本，自动检测并安装到已安装的 AI 工具。

```bash
# 安装所有代理到 Claude Code 目录
./scripts/install.sh --tool claude-code

# 或者交互式安装（自动检测已安装的工具）
./scripts/install.sh

# 非交互式安装所有检测到的工具
./scripts/install.sh --no-interactive --parallel
```

**第三步：** 启动你的 AI 工具（如 Claude Code、Cursor 等），代理会自动加载。

开源地址：https://github.com/msitarzewski/agency-agents

## 05 **点击下方卡片，关注阿福研习社**

这个公众号历史发布过很多有趣的开源项目，如果你懒得翻文章一个个找，你直接关注微信公众号：**阿福研习社** ，后台对话聊天就行了：

[公众号二维码图片]
