---
name: project-dev-memory
description: Maintain local long-term project development memory and distill stable rules into superNM skills.
---

# Project Development Memory

Use this skill when the user asks to remember project-development norms, maintain long-term development continuity, summarize Codex conversations into reusable rules, or update `superNM` skills from accumulated work.

## Core Workflow

1. Read the workspace ledger first: `/home/xujj/Projects/CONTINUITY.md`.
2. For a concrete project, read its durable sources before extracting new rules: `AGENTS.md` or `CLAUDE.md`, `ROADMAP.md`, latest `devlog.md`, and existing project `CONTINUITY.md` when present.
3. Run the local distiller in review-first mode:

```bash
python3 -m dev_memory_system.cli daily --date today
```

4. Inspect `memory/skill_candidates/YYYY-MM-DD.md` before applying any skill update.
5. Apply a reviewed candidate only when the user approves or the task explicitly asks for direct application:

```bash
python3 -m dev_memory_system.cli apply-candidate memory/skill_candidates/YYYY-MM-DD.json
```

## What To Remember

- Explicit long-term user rules, especially phrases like "以后", "每次", "我的规范", "长期", "记住".
- Project workflow rules such as required startup reads, completion logs, ROADMAP updates, commits, push policy, and service verification.
- Architecture decisions and invariants that affect future coding.
- Tooling preferences such as `rg` for local search and configured MCP servers for web search.
- Repeated corrections that become stable preferences after confirmation.
- Conflict resolutions and scope-specific exceptions.

## What Not To Remember

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

## OpenViking Integration

OpenViking can be used as the semantic memory backend after the local pipeline is stable. Prefer this order:

1. First keep deterministic local extraction from `~/.codex/sessions`.
2. Then install/configure OpenViking Codex memory plugin for automatic recall and capture.
3. Keep skill edits controlled by the local distiller, not by raw OpenViking recall results.

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
