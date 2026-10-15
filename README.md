# 软件工程安全防破解

**Software Engineering Security · Agent Skill · v1.1.1**

面向自有或明确授权软件的安全工程技能：LLVM混淆与代码虚拟化、服务端鉴权、WebSocket心跳、TLS/AEAD、nonce防重放、反调试、模块注入与Hook检测、跨平台完整性和测试验收。

这是可加载的**中文文档型Agent Skill**，不是保护器、编译器、在线扫描服务或已加固的软件。不附带可执行脚本，不承诺“不可破解”或“防住99%”。实际实施必须依据项目授权、工具能力和测试证据。

## 快速安装

如果已安装Node.js/npm，可使用[skills CLI](https://github.com/vercel-labs/skills)安装。首次使用npx可能下载第三方CLI，请按提示审阅并选择目标编辑器及项目级/用户级范围：

```bash
npx skills add b0wDi/software-engineering-security --skill software-engineering-security
```

只列出仓库里的技能、不安装：

```bash
npx skills add b0wDi/software-engineering-security --list
```

仓库入口文件是根目录的[SKILL.md](SKILL.md)，技能名为`software-engineering-security`。安装时必须保留`references/`，仅复制SKILL.md会缺失完整规范。不要覆盖同名用户技能，先比较和备份。CLI的编辑器支持范围以其当前版本为准。

## 直接给AI编辑器读取

不支持Agent Skills的编辑器，可以读取[完整自包含提示词](PROMPT.md)：

```text
https://raw.githubusercontent.com/b0wDi/software-engineering-security/main/PROMPT.md
```

推荐请求：

> 请读取上面的PROMPT.md，确认读取完整后，按“软件工程安全防破解”规范检查我授权的当前项目。先核实客户端与服务端心跳、鉴权、TLS和防重放实现，给出代码证据，再分阶段加固并测试。如果不能联网，请要求我上传PROMPT.md，不要假装已加载。

不具备联网读取能力时，把PROMPT.md全文作为附件或粘贴到会话。只有具备项目访问和执行工具的代理才能实际修改代码；纯聊天环境只能提供分析与建议。

## 下载固定版本

- [最新GitHub Release](https://github.com/b0wDi/software-engineering-security/releases/latest)
- [v1.1.1技能ZIP](https://github.com/b0wDi/software-engineering-security/releases/download/v1.1.1/software-engineering-security-v1.1.1.zip)
- [v1.1.1 ZIP校验值](https://github.com/b0wDi/software-engineering-security/releases/download/v1.1.1/SHA256SUMS.txt)
- [固定v1.1.1的完整提示词](https://raw.githubusercontent.com/b0wDi/software-engineering-security/v1.1.1/PROMPT.md)

`main`链接可能随提交更新。需要可复现使用时，使用固定tag或完整commit。安装后的本地副本不会因远端更新而自动改变。

## 手动安装与编辑器调用

下载Release ZIP，解压后将整个`software-engineering-security`目录放到下表中适合你的路径。或使用Git克隆到该路径（若目标已存在，停止并先比较，不执行覆盖或清理）：

```bash
git clone https://github.com/b0wDi/software-engineering-security.git software-engineering-security
```

| 编辑器/代理 | 项目级技能目录 | 调用示例 |
| --- | --- | --- |
| Claude Code | `.claude/skills/software-engineering-security/` | `/software-engineering-security` |
| Cursor（支持Agent Skills的版本） | `.cursor/skills/software-engineering-security/`或`.agents/skills/software-engineering-security/` | 输入`/`并选择该技能 |
| Codex及支持`.agents/skills`的代理 | `.agents/skills/software-engineering-security/` | Codex：`$software-engineering-security` |
| 其他支持Agent Skills的编辑器 | 遵循其官方目录/导入约定 | 选择技能或明确要求使用 |

Claude Code可使用`~/.claude/skills/`作为本机用户级目录，Cursor可使用`~/.cursor/skills/`。重新加载技能列表/新开会话，确认参考文件可读。各编辑器版本、远程开发环境和云代理的同步规则可能不同；本仓库未在所有编辑器中实测。

## 文件结构

```text
software-engineering-security/
├── SKILL.md                         # 入口和工作流程
├── references/
│   ├── security-playbook.md         # 完整安全工程规范
│   └── acceptance-checklist.md      # 验收清单
├── PROMPT.md                        # 自包含版本
├── README.md
├── CHANGELOG.md
├── manifest.json                    # 文件大小与SHA-256
└── SHA256SUMS.txt                    # 仓库文件校验值
```

## 校验与安全边界

在解压后的技能目录运行：

```bash
shasum -a 256 -c SHA256SUMS.txt
# 或：sha256sum -c SHA256SUMS.txt
```

Windows可用`Get-FileHash -Algorithm SHA256`对照清单。同源哈希用于发现下载损坏和版本不一致，**不是独立数字签名**。Release附件的SHA256SUMS.txt验证ZIP，仓库内同名文件验证技能文件；两者用途不同。

本仓库只含通用技能文档，不接收用户代码或凭据，不授予代理超出用户指令的权限，不改变系统安全设置。客户端校验可被绕过，服务端鉴权仍是安全边界。安装本技能不代表你的软件已经完成任何防护。公开托管不等于另行授予开源许可证；本仓库未声明额外许可证。

## 版本与来源

v1.1.1增加GitHub发布、安装和固定版本下载说明；安全规范沿用v1.1.0。原世界本地技能与云端旧包不被覆盖、不自动同步。

参考：[Agent Skills规范](https://agentskills.io/specification) · [Claude Code](https://code.claude.com/docs/en/skills) · [Cursor](https://cursor.com/docs/skills) · [Codex](https://developers.openai.com/codex/skills) · [skills CLI](https://github.com/vercel-labs/skills)
