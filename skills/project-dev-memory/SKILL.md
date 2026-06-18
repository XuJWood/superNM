---
name: project-dev-memory
description: Run and maintain a complete developer-facing project workflow from planning through delivery.
---

# Project Development Operating System

Use this skill when a developer wants a repeatable project operating system: project initialization, architecture planning, development execution, reporting, roadmap maintenance, delivery verification, and long-term skill improvement from local Codex conversations.

This skill is developer-facing. A new user should be able to use it to run a project consistently without reading prior chats.

## Operating Principles

- Keep project rules in files, not chat memory.
- Preserve a clear boundary between project bootstrap, daily execution, reporting, and long-term skill improvement.
- Prefer local processing of Codex session logs. Do not depend on OpenViking or any external memory backend.
- Treat generated skill candidates as review-first proposals unless the user explicitly asks for direct application.
- Never save secrets, API keys, bearer tokens, account identifiers, or raw chat transcripts into skills.

## Project Files

Every managed project should maintain these durable files:

- `AGENTS.md` or `CLAUDE.md`: project architecture, conventions, required workflow, commands, forbidden actions, and completion rules.
- `ROADMAP.md`: phase-based development plan, current phase, next phase, acceptance criteria, and status.
- `devlog.md`: top-prepended development log for each completed task.
- `CONTINUITY.md`: compact compression-safe ledger for goals, decisions, state, working set, and important receipts.
- `docs/Product-Report.md`: product and technical research report when the project starts or pivots.
- `docs/Architecture-and-Dev-Standards.md`: architecture, module boundaries, interface contracts, and UI/backend standards.
- `docs/Frontend-Design-Spec.md`: page list, information architecture, interaction rules, visual rules, and responsive constraints when frontend exists.
- `reports/_日报模板.md`: daily report template.
- `reports/_模板.md`: weekly report template.
- `reports/daily/YYYY-MM-DD.md`: daily reports.
- `reports/week-NN-MMDD.md`: weekly reports.

## Project Lifecycle

### 1. Project Discovery

Collect the minimum information needed to plan the project:

- Product goal and target users.
- Core workflows and 3-5 highest-value features.
- Required interfaces, data sources, integrations, and deployment environment.
- Frontend pages or operational dashboards if needed.
- Known constraints such as timeline, privacy, model provider, hardware, or existing codebase.

Produce or update `docs/Product-Report.md` with:

- Product positioning and user scenarios.
- Competitor or open-source reference analysis when useful.
- Technical architecture options and chosen stack.
- Module breakdown and risk assessment.
- Recommended development path.

### 2. Architecture Planning

Produce or update `docs/Architecture-and-Dev-Standards.md` before major implementation work. It should define:

- System boundaries and module ownership.
- Backend entry points, service boundaries, API contracts, and data flow.
- Frontend information architecture, page ownership, state flow, and design rules when applicable.
- Storage, configuration, observability, security, and deployment patterns.
- Extension rules such as plugin/node/tool protocols.
- Forbidden shortcuts and invariants that must survive future sessions.

### 3. Roadmap Planning

Maintain `ROADMAP.md` as phase-based execution, not vague task notes.

Each phase should include:

- Goal.
- Dependencies.
- Deliverables.
- Acceptance criteria.
- Status table with clear done/pending markers.
- Current phase and next phase at the top.

Prefer phases such as:

- Phase 0: project infrastructure and baseline docs.
- Phase 1: core MVP pipeline or main user workflow.
- Phase 2: frontend/config/observability surfaces.
- Phase 3: integration and data acceptance tests.
- Phase 4: production hardening and deployment.
- Phase 5+: advanced features, automation, and regression.

### 4. Session Start

Before development:

1. Read workspace `CONTINUITY.md`.
2. Read project `AGENTS.md` or `CLAUDE.md`.
3. Read `ROADMAP.md`.
4. Read latest `devlog.md`.
5. Inspect current git status and treat unrelated dirty files as user-owned.
6. Start from the current phase and next pending item unless the user redirects.

### 5. Development Execution

During implementation:

- Follow the project architecture and local coding patterns.
- Keep edits scoped to the requested task and relevant module boundaries.
- Update YAML/config/platform/observability surfaces when the project rules require them.
- Add tests or smoke checks proportional to risk.
- Avoid hardcoded secrets and avoid direct hardware access unless the architecture explicitly allows it.
- Keep user-facing progress clear and concise.

### 6. Completion

Before finishing a development task:

1. Run relevant validation.
2. Update `devlog.md` at the top with date, completed work, verification, and next step.
3. Update `ROADMAP.md` status and current/next phase if progress changed.
4. Update `CONTINUITY.md` only for durable changes: goals, decisions, state, important receipts, and working set.
5. Commit related files with a conventional message if the project requires commits.
6. Push only when the user explicitly asks or the project rules require it.

### 7. Reporting

Daily report:

- Generate `reports/daily/YYYY-MM-DD.md` near end of day or when requested.
- Summarize completed tasks from `devlog.md`, verification, blockers, and next-day plan.

Weekly report:

- Generate `reports/week-NN-MMDD.md` on Sunday evening or Monday start.
- Summarize daily reports and phase progress.
- Include completed work, status table, blockers, and next-week plan.

Reports should be written for a technical lead or manager: concrete work, visible progress, risks, and next actions.

### 8. Long-Term Skill Improvement

Use local Codex session logs to improve this skill and related `superNM` skills.

Run:

```bash
python3 -m dev_memory_system.cli daily --date today
```

Review:

```text
/home/xujj/Projects/dev-memory-system/memory/skill_candidates/YYYY-MM-DD.md
```

Apply only after review:

```bash
python3 -m dev_memory_system.cli apply-candidate memory/skill_candidates/YYYY-MM-DD.json
```

## Memory Saving Logic

The local distiller should save rules that improve future project execution, not raw chat.

Save:

- Explicit long-term user rules, especially phrases like "以后", "每次", "我的规范", "长期", "记住".
- Project workflow rules such as startup reads, completion logs, ROADMAP updates, report cadence, commits, push policy, and service verification.
- Architecture decisions and invariants that affect future coding.
- Rules about where to produce reports, architecture docs, frontend specs, development plans, and delivery evidence.
- Development route patterns that make long-running projects painless to continue.
- Tooling preferences such as `rg` for local search and configured MCP servers for web search.
- Repeated corrections that become stable preferences after confirmation.
- Conflict resolutions and scope-specific exceptions.

Do not save:

- One-off task outputs, temporary experiments, and unconfirmed guesses.
- Secrets, tokens, account identifiers, or credentials.
- Full raw chat transcripts.
- Implementation details that did not become a reusable rule or architectural invariant.

## Skill Update Rules

- Keep `supernm` focused on new-project bootstrap.
- Put ongoing memory and development-continuity behavior in `project-dev-memory`.
- Use review-first updates by default; generated candidates are proposals, not source of truth.
- If applying candidates, preserve concise skill bodies and avoid turning a skill into a chat log.
- Resolve conflicts with this priority: current user instruction, project `AGENTS.md` or `CLAUDE.md`, project ledger, local long-term memory, general skill guidance.

## Local Project

The local implementation lives at:

```text
/home/xujj/Projects/dev-memory-system
```

Important outputs:

- `memory/raw_sessions/` stores normalized session snapshots.
- `memory/extracted/` stores daily extracted memory items.
- `memory/canonical/` stores durable category files.
- `memory/skill_candidates/` stores review-first skill update proposals.

## 长期开发记忆沉淀

### 本地记忆后端
- 分类：`skill_maintenance`
- 规则：长期开发记忆只使用本地 Codex session 文件和 `dev-memory-system` 处理；不接入 OpenViking，不依赖外部记忆服务。
- 来源：用户明确要求
- 置信度：`0.98`

### 本地工具项目提交策略
- 分类：`git_workflow`
- 规则：`/home/xujj/Projects/dev-memory-system` 是本地个人记忆工具项目，默认不执行 git 提交；只有用户明确要求时才初始化、提交或推送该项目。
- 来源：用户明确要求
- 置信度：`0.95`

### Developer-facing skill 目标
- 分类：`skill_maintenance`
- 规则：最终 skills 必须面向开发者，能直接指导一个项目从调研、架构、计划、开发、日报周报、验证、提交到持续迭代的完整执行逻辑。
- 来源：用户明确要求
- 置信度：`0.98`

### 网页搜索 MCP
- 分类：`tooling`
- 规则：后续需要网页搜索时，优先使用已配置的 `WebSearch` MCP；仅当 MCP 不可用或用户另有要求时退回其他搜索方式。
- 来源：`/home/xujj/.codex/sessions/2026/06/04/rollout-2026-06-04T16-53-55-019e91d6-d2d0-7c03-9b38-ac8ea0f042b5.jsonl:27`
- 置信度：`0.92`

### MCP 密钥处理
- 分类：`tooling`
- 规则：阿里云 IQS `WebSearch` MCP 的密钥必须通过环境变量或受控配置注入，禁止写入长期记忆、skill、候选文件或代码。
- 来源：`/home/xujj/.codex/sessions/2026/06/04/rollout-2026-06-04T16-53-55-019e91d6-d2d0-7c03-9b38-ac8ea0f042b5.jsonl:35`
- 置信度：`0.76`

### superNM 职责边界
- 分类：`skill_maintenance`
- 规则：`/home/xujj/Projects/superNM/skills/supernm/SKILL.md` 负责新项目初始化；长期记忆、持续开发规范和 skill 沉淀由 `project-dev-memory` 负责。
- 来源：`/home/xujj/Projects/superNM/skills/supernm/SKILL.md`
- 置信度：`0.86`

### 工作区账本
- 分类：`project_workflow`
- 规则：使用 `/home/xujj/Projects/CONTINUITY.md` 作为工作区连续性账本；仅在目标、决策、状态、重要结果或工作集有实质变化时更新。
- 来源：`/home/xujj/Projects/CONTINUITY.md`
- 置信度：`0.90`
