---
name: Context Manager
slug: context-manager
version: 1.0.0
description: "Long session context management with auto-compression, protected tail, and token budget tracking. Based on Claude Code autoCompact system."
---

## When to Use

- Session context exceeds 80% of token limit
- Long task with many intermediate steps
- Multiple sub-agent results need to be synthesized
- When you notice "context getting full" warnings

## Core Concept: Protected Tail

Always keep these untouched:
- Last 5 user messages
- Last 3 assistant messages
- Current task context
- Critical decisions made

## Compression Triggers

| Level | Token Usage | Action |
|-------|------------|--------|
| Warning | >80% | Micro-compact tool results |
| Danger | >90% | Fold early messages to summary |
| Critical | >95% | Emergency compress + notify user |

## Compression Types

### 1. Micro-Compact
Compress tool results, keep structure:
```
[Tool: file_edit] 150 lines → [File edited: 3 files modified]
[Tool: bash] 89 lines → [Command completed: npm install]
```

### 2. Context Fold
Collapse old messages to summary:
```
[Messages 1-50] → [Early discussion: resolved X, Y; decided Z]
```

### 3. Protected Tail
Never compress:
- Recent user requests (last 5)
- Final decisions
- Current task goal
- Unresolved issues

## Token Budget

Track for long tasks:
```
Budget: 500k tokens
Used: 234k (46%)
Remaining: 266k
Projected: 380k at current pace
Action: Enable auto-compact at 400k
```

## Usage

### When to Trigger

Always check token state before spawning sub-agents. If session is >60% full:
1. Pre-emptively compact
2. Warn user of compression
3. Use summaries for old content

### Compression Format

For context fold, create summary:
```
## Session Summary [date]

已完成：
- 完成了X调研
- 确定了Y方案
- 解决了Z问题

当前任务：
- 目标：xxx
- 进度：已完成A，进入B阶段

待处理：
- 问题1
- 问题2
```

## Anti-Patterns

- Never compress mid-decision
- Never fold without keeping reference
- Never delete user preferences
- Never compress current task context

## Workflow

```
Monitor token usage
    ↓
< 60% → continue normally
60-80% → micro-compact tool results
80-90% → context fold early messages
> 90% → compress + warn user
> 95% → emergency compress + pause new work
```
