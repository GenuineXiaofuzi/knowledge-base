# Codex 登录手机号验证问题解决方案

> 对话日期：2026-05-24
> 分类：AITools
> 标签：#Codex #OpenAI #登录问题 #国内用户 #手机号验证

## 核心问题

用户作为国内用户，在登录 OpenAI Codex 桌面客户端时被要求验证手机号，但 +86 中国大陆手机号无法接收验证码，导致无法正常使用 Codex。

## 解决方案汇总

### 方案1：绑定通行密钥（Passkey）⭐ 推荐首选

利用 WebAuthn 协议绕过手机号验证。

**操作步骤：**
1. 打开 [chat.openai.com](https://chat.openai.com) 网页端登录
2. 点击右上角头像 → **Settings（设置）**
3. 找到 **Security（安全）** → **Passkeys（通行密钥）**
4. 点击 **Add a passkey**，按 macOS 提示用 Touch ID 或系统密码完成绑定
5. 打开 Codex.app → **Sign in with ChatGPT**
6. 浏览器弹出登录界面，输入账号密码后会触发 Passkey 验证（而非手机号验证）
7. 用 Touch ID 或系统验证完成登录

> ⚠️ 成功率约 70%，部分账号仍可能强制要求手机号

---

### 方案2：迁移 auth.json（有旧设备时）

将已登录设备的凭据文件复制到新设备：

```bash
# 旧 Mac 提取凭据
cat ~/.codex/auth.json

# 新 Mac 先运行一次 codex 生成目录
codex

# 将旧设备 auth.json 内容写入新设备 ~/.codex/auth.json
# 然后验证
codex login status
```

> ⚠️ `auth.json` 是敏感凭据，用 AirDrop 或加密U盘传输，不要通过聊天工具

---

### 方案3：使用 API Key 登录（无需手机号）

```bash
# 方式1：通过 stdin 传入
echo "sk-proj-你的APIKey" | codex login --with-api-key

# 方式2：环境变量
export OPENAI_API_KEY="sk-proj-你的APIKey"
codex
```

> ⚠️ API Key 登录使用独立计费，不享受 ChatGPT Plus 订阅额度

---

### 方案4：接码平台（虚拟海外号）

| 平台 | 地址 | 说明 |
|------|------|------|
| Hero-SMS | https://hero-sms.com/cn | 需充值 $3，支持 OpenAI 接码 |
| Doge SMS | https://www.dogesms.com | 专做 OpenAI 接码 |

**操作要点：**
- 搜索服务选 `OpenAI` 或 `ChatGPT`
- **优先选 WhatsApp 通道**（成功率更高）
- 避开印尼、巴西等低价滥用区
- 选平台标注成功率 ≥80% 的国家
- 若3分钟内未收到验证码，取消订单换号重试

> ⚠️ 接码平台风险：号码可能被多人使用导致 `Phone already used` 错误，充值余额通常不退款

---

### 方案5：设备码登录

```bash
codex login --device-auth
# 终端显示验证码和链接
# 在另一台能开浏览器的设备上打开链接
# 登录账号并输入验证码完成授权
```

---

## 方案选择建议

```
首选 → 方案1（Passkey 通行密钥）
        ↓ 不行
次选 → 方案3（API Key 登录）
        ↓ 不行
再次 → 方案4（接码平台）
```

## 常见报错处理

| 报错 | 原因 | 解决办法 |
|------|------|---------|
| 收不到验证码 | 虚拟号不支持 / IP高风险 | 换国家号码；切换干净代理节点 |
| Phone number already used | 号码已被多人绑定达到上限 | 取消订单，重新购买新号码 |
| Unsupported country | 代理IP位于OpenAI屏蔽地区 | 切换全局代理至美国/日本，清缓存重试 |
| 403 / No active subscription | 验证通过但无Codex使用权益 | 订阅 ChatGPT Plus/Pro |

## 重要注意事项

1. **+86 手机号基本无法通过验证**（收不到短信 / Unsupported country）
2. 此前「Google账号 + 纯净住宅IP免验证」方法现已失效
3. 完成手机号验证 ≠ 拥有 Codex 订阅权益，免费账号验证成功也可能无法调用高级接口
4. 不要频繁点击「重新发送」验证码，极易被 OpenAI 拉黑 IP 甚至封号

---

**元数据**
- 归档时间：2026-05-24
- 信息来源：V2EX、知乎、掘金、API易文档
- GitHub 路径：`AITools/2026-05-24-Codex-Login-Phone-Verification-Solution.md`
