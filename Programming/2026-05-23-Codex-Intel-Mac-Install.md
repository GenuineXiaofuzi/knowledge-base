# Intel Mac 安装 Codex 完整实录

> 对话日期：2026-05-23
> 分类：Programming / AITools
> 标签：#Codex #IntelMac #Electron #better-sqlite3 #Node原生模块

## 核心问题

OpenAI Codex 官方仅提供 Apple Silicon（ARM64）版本，Intel Mac 无法直接运行。
社区有非官方转换方案，但 `better-sqlite3` 原生模块需要针对 Electron 的 Node.js 版本重新编译。

## 解决方案（最终成功）

### 方案一：Homebrew 第三方 Tap（推荐）

```bash
# 1. 安装 Homebrew（如未安装）
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. 添加第三方 Tap
brew tap soham2008xyz/codex-intel https://github.com/soham2008xyz/codex-intel

# 3. 安装 Codex Intel 版本
brew install --cask codex-intel
```

源地址：https://github.com/soham2008xyz/codex-intel

### 方案二：手动下载预转换版本

```bash
# 下载 Intel 转换版
curl -L -o ~/Downloads/Codex-Intel.zip \
  "https://github.com/soham2008xyz/codex-intel/releases/download/26.519.41501-intel/Codex-Intel.zip"

# 解压并安装
cd ~/Downloads && unzip Codex-Intel.zip
mv Codex.app /Applications/
xattr -cr /Applications/Codex.app   # 移除 quarantine 属性
```

## better-sqlite3 编译问题修复

Codex 使用 Electron 42.1.0（NODE_MODULE_VERSION=146），
预编译的 `better-sqlite3` 不匹配，需要从源码重新编译。

### 关键步骤

```bash
# 1. 进入 Codex 应用目录
cd /Applications/Codex.app/Contents/Resources/app.asar.unpacked

# 2. 安装最新 better-sqlite3（git 版本）
npm install better-sqlite3@git+https://github.com/WiseLibs/better-sqlite3.git

# 3. 修复 V8 API 不兼容问题（两个文件）

# 文件1: src/better_sqlite3.cpp 第60行
# 修改前：
v8::Local<v8::External> data = v8::External::New(isolate, addon);
# 修改后：
#if defined(V8_MAJOR_VERSION) && V8_MAJOR_VERSION >= 13
v8::Local<v8::External> data = v8::External::New(isolate, addon, v8::kExternalPointerTypeTagDefault);
#else
v8::Local<v8::External> data = v8::External::New(isolate, addon);
#endif

# 文件2: src/util/macros.cpp 第30行
# 修改前：
#define OnlyAddon static_cast<Addon*>(info.Data().As<v8::External>()->Value())
# 修改后：
#if defined(V8_MAJOR_VERSION) && V8_MAJOR_VERSION >= 13
#define OnlyAddon static_cast<Addon*>(info.Data().As<v8::External>()->Value(v8::kExternalPointerTypeTagDefault))
#else
#define OnlyAddon static_cast<Addon*>(info.Data().As<v8::External>()->Value())
#endif

# 文件3: src/util/helpers.cpp 第89-94行
# 将 0 改为 nullptr（修复 SetNativeDataProperty 重载歧义）

# 4. 使用 Electron headers 编译
cd node_modules/better-sqlite3
npx node-gyp rebuild \
  --target=42.1.0 \
  --arch=x64 \
  --dist-url=https://artifacts.electronjs.org/headers/dist
```

### 编译成功标志

```
gyp info ok
```

输出文件：`build/Release/better_sqlite3.node`（Mach-O 64-bit bundle x86_64）

## 关键发现

| 问题 | 原因 | 解决方案 |
|------|------|---------|
| `better-sqlite3 is only bundled with Electron app` | 模块缺失 | `npm install better-sqlite3` 到 `app.asar.unpacked/` |
| `compiled against a different Node.js version` | 预编译版本 ABI 不匹配 | 从源码针对 Electron 42 重新编译 |
| `too few arguments to function call, expected 3, have 2` | V8 API 变更（External::New 新增 tag 参数） | 宏定义条件编译，兼容新旧 API |
| `SetNativeDataProperty' is ambiguous` | 传入 `0` 导致重载歧义 | 改为 `nullptr` |

## 后续行动

- [ ] 验证 Codex 是否能正常启动
- [ ] 如成功，可将修复后的 `better_sqlite3.node` 提交到 GitHub Release
- [ ] 向 `WiseLibs/better-sqlite3` 提 PR 修复 V8 13+ 兼容性问题

## 相关链接

- Codex Intel 转换项目：https://github.com/soham2008xyz/codex-intel
- better-sqlite3 官方仓库：https://github.com/WiseLibs/better-sqlite3
- Electron headers 镜像：https://artifacts.electronjs.org/headers/dist/

---

**元数据**
- WorkBuddy 会话：bf68b9db-220c-463c-98b6-e4a6697ff624
- 本地路径：`/Users/lifang/Documents/Knowledge-Base/Programming/2026-05-23-Codex-Intel-Mac-Install.md`
- 涉及工具：Homebrew, node-gyp, Electron, V8
