# 🚀 Bootstrap — Claude Code 新项目全流程启动 Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blue)](https://claude.ai/code)

**一条命令，从零到完整项目骨架。**

你有一个产品想法，Claude Code 帮你完成从产品调研、技术选型、开发计划到项目规范的全部初始化工作。不是生成几行模板代码就完事 — 而是产出一整套**可落地、可交付、可持续开发**的项目工程体系。

---

## 🎯 适合谁用

| 角色 | 场景 | 痛点 |
|------|------|------|
| **独立开发者** | 一个人从零搭建 SaaS/工具产品 | 没人讨论技术方案，从调研到编码全自己扛 |
| **个人负责完整业务线** | 公司里独立有一条业务线，前后端都要做 | 项目结构、开发规范、日报周报全要从头建 |
| **小团队技术负责人** | 公司新启一个项目，需要把规范立起来 | 不想每次开新项目都手动拷旧项目的脚手架 |
| **AI 编程工具重度用户** | 用 Claude Code/Cursor/Copilot 写代码 | 希望 AI 记住项目规范，每次会话一致行动 |

如果你是上述任意一种，这个 skill 能让你的新项目从 **"空目录"→"可立即开发的工程体系"** 只需要 5 分钟。

---

## ✨ 核心能力

```
你的想法 → /bootstrap → 完整项目工程
```

### 9 个阶段，一气呵成

```
Phase 1  产品方向收集    →  交互式收集你的产品想法（支持链接/截图/文档）
Phase 2  产品调研        →  WebSearch 竞品分析 + 技术方案对比
                           →  生成 docs/Product-Report.md（技术调研报告）
Phase 3  开发计划        →  生成 ROADMAP.md（按阶段划分，不用时间约束）
Phase 4  前端界面规划    →  确认前端需求，生成设计规格文档
                           →  自动衔接 /frontend-design 生成高质量 UI
Phase 5  项目骨架        →  目录结构 + BaseNode/BaseTool 基类 + server/engine
Phase 6  开发规范        →  生成 CLAUDE.md（每次会话自动加载）
Phase 7  日报周报体系    →  devlog.md + 日报模板 + 周报模板
                           →  明确触发时机：每会话/每日/每周
Phase 8  Git 初始化      →  git init + 首次规范化 commit
Phase 9  输出总结        →  完整项目树 + 下一步建议
```

### 输出的项目结构

```
my-project/
├── CLAUDE.md                       # 开发基线（每次会话自动加载）
├── ROADMAP.md                      # 分阶段开发计划
├── devlog.md                       # 开发日志（每次会话追加）
├── pyproject.toml                  # 项目依赖管理（取决于技术栈）
├── .gitignore
├── .claude/
│   └── settings.json               # Claude Code 项目配置
├── config/                         # 配置文件目录（按需）
├── src/                            # 源码目录（模块由 ROADMAP 决定）
│   ├── server.py                   # 主入口
│   └── ...                         # 具体模块根据产品调研生成
├── docs/
│   ├── Product-Report.md           # 产品技术调研报告
│   ├── Architecture-and-Dev-Standards.md
│   └── Frontend-Design-Spec.md     # 前端设计规格
├── reports/
│   ├── _模板.md                    # 周报模板
│   ├── _日报模板.md                # 日报模板
│   └── daily/                      # 日报存档
├── web/                            # 前端页面（如有）
├── tests/
└── scripts/
```

> 架构由调研和计划驱动，不预设特定技术栈。Python/FastAPI、Node.js/Express、Go/Gin 均支持。

---

## 📦 安装

### 方式一：项目级安装（推荐）

```bash
# 在你的项目根目录
mkdir -p .claude/skills
git clone https://github.com/YOUR_USERNAME/claude-bootstrap-skill.git /tmp/bootstrap-skill
cp -r /tmp/bootstrap-skill/skills/bootstrap .claude/skills/
rm -rf /tmp/bootstrap-skill
```

### 方式二：用户级全局安装

```bash
# 所有项目都能用
cp -r skills/bootstrap ~/.claude/commands/
```

### 方式三：从 Claude Code 插件市场安装（即将上线）

```
/install-plugin bootstrap
```

---

## 🚀 使用

在 Claude Code 会话中，进入你的空项目目录：

```bash
cd ~/Projects/my-new-product
```

然后调用：

```
/bootstrap my-awesome-product
```

或者不带参数，进入交互式流程：

```
/bootstrap
```

**交互示例：**

```
Claude: 你好！让我们来启动这个新项目。
先问你几个问题：

1. 产品方向 — 你要做什么产品？
   你可以直接给我一段描述、一个竞品链接、甚至截图。

> 我要做一个给宠物医生的 AI 问诊辅助工具

2. 目标用户是谁？
> 宠物医院的医生

3. 最重要的 3-5 个功能？
> ①症状→诊断建议 ②用药方案推荐 ③病例记录自动整理
   ④宠物主人端的健康报告

4. 技术偏好？默认 Python + FastAPI
> 可以

5. 需要前端界面吗？
> 需要，医生后台 + 主人端页面

...

[Claude 开始调研、生成文档...]
```

---

## 🔥 为什么不是简单的脚手架？

| 普通脚手架 | Bootstrap Skill |
|------------|-----------------|
| 固定的目录结构 | 根据你的产品定制目录 |
| 没有技术调研 | 自动做竞品分析 + 技术选型 |
| 没有开发计划 | 产出分阶段的 ROADMAP |
| 没有开发规范 | 产出 CLAUDE.md 规范每次会话 |
| 没有日志周报体系 | 日报/周报/开发日志全线打通 |
| 拷完就忘了 | 每次会话自动加载项目规范 |

---

## 🧩 技术栈适配

不带技术偏见。Skill 会**根据你的产品方向和需求推荐最合适的技术方案**：

| 后端 | 前端 | AI 部分 |
|------|------|---------|
| Python/FastAPI | 纯 HTML/CSS/JS（无框架） | LangGraph |
| Node.js/Express | React/Vue | OpenAI SDK |
| Go/Gin | Next.js | LangChain |
| 按需生成 | 调用 /frontend-design | 按需选型 |

---

## 📋 日报/周报体系

这是核心差异化能力之一。Skill 初始化时自动建立完整的时间汇报体系：

### 触发时机

| 文档 | 何时生成 | 存放位置 |
|------|---------|---------|
| **devlog.md** | 每次开发完成立即追加 | 项目根目录 |
| **日报** | 每天最后一次会话结束 | `reports/daily/2026-06-04.md` |
| **周报** | 每周日 18:00 后 / 周一开工前 | `reports/week-03-0608.md` |

### 会话自动检查

每次新会话启动时，Claude Code 会：
1. 检查昨天是否缺日报 → 提示补上
2. 检查上周是否缺周报 → 提示生成
3. 然后再开始今天的开发

> 再也不用被领导催"周报发一下"，也不用周末加班补周报。

---

## 🔗 配合使用的 Skills

| Skill | 用途 |
|-------|------|
| `/frontend-design` | 开发前端界面时自动调用，生成高质量 UI 代码 |
| `/bootstrap:superpowers` | 多 Agent 协作，调研/分析阶段并发加速 |

---

## 📖 开发规范哲学

这套体系来自真实项目的踩坑经验。核心理念：

1. **每次会话可复现** — CLAUDE.md 保证 AI 每次都知道项目全貌
2. **YAML 驱动，不硬编码** — 节点/工具/配置全通过 YAML 注册
3. **每阶段有验收标准** — 不做完不确定"做完没"的开发
4. **时间汇报体系自动化** — 不用专门花时间写周报，从 devlog 汇总
5. **前后端同步演进** — 不先做后端再补前端

---

## 🗺️ 路线图

- [x] Phase 1-9: 全流程项目初始化
- [x] 日报/周报模板 + 触发时机规范
- [ ] 更多后端模板（Express/Go/Gin）
- [ ] 数据库迁移脚本集成（Alembic/Prisma）
- [ ] CI/CD 模板集成
- [ ] Docker Compose 一键部署模板

---

## 🤝 贡献

这是给独立开发者和个人业务负责人的工具。如果你有好的想法或模板，欢迎 PR。

## 📄 License

MIT — 随便用，随便改，随便发给别人。
