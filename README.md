# Explore Agent

[![Stars](https://img.shields.io/github/stars/Eita19/openclaw-skills?style=flat)](https://github.com/Eita19/openclaw-skills)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

**Systematic code exploration agent. Trace paths, understand structure, find connections.**

Inspired by Claude Code's exploreAgent, built for OpenClaw agents.

---

## What is Explore Agent?

When you need to understand a codebase, you don't read every file. You map, trace, and connect.

Explore Agent teaches your AI agent a systematic approach to code exploration:

- **Breadth First** — Overview first, then deep-dive
- **Depth First** — Follow one path completely
- **Pattern Based** — Find all occurrences efficiently

---

## Structure

```
explore-agent/
├── SKILL.md          # Main skill file
└── memory/           # Exploration history
```

---

## Quick Start

```bash
# Install via OpenClaw
clawhub install explore-agent

# Or manually
cp -r explore-agent/ ~/.openclaw/skills/
```

---

## When to Use

- "Explore the codebase"
- "How does X work?"
- "Find all files related to Y"
- "Understand the architecture"
- "Map the project structure"

---

## Workflow

### Step 1: Orient
```
What is the project?
What language/framework?
What is the main entry point?
```

### Step 2: Map
```
Directory structure
Key files
Dependencies
```

### Step 3: Trace
```
Follow imports/exports
Trace function calls
Find call sites
```

### Step 4: Connect
```
How do modules interact?
What are the data flows?
Where are the boundaries?
```

---

## Output Format

```markdown
## Exploration: [Topic]

### Overview
[What we found]

### Structure
[Key files and their roles]

### Key Findings
1. [Finding 1]
2. [Finding 2]

### Connections
[How things relate]

### Questions for Deeper Analysis
1. [Question]
```

---

## Techniques

### File Reading
- Read first/last 20 lines for overview
- Read import/export sections
- Jump to key functions

### Pattern Search
```
Grep: function definitions
Glob: file patterns
Find: related files
```

### Trace Methods
- Import chain: what imports this?
- Call chain: what calls this function?
- Reference chain: where is this used?

---

## Anti-Patterns

- Don't read every file (too slow)
- Don't get lost in details
- Don't forget the question
- Don't over-document trivial files

---

## Other Skills

| Skill | Description |
|-------|-------------|
| [self-check](./self-check/) | Multi-dimensional critical thinking framework |
| [context-manager](./context-manager/) | Long session context management |
| [permission-learner](./permission-learner/) | Learn tool permissions from feedback |

---

*Part of [Eita19/openclaw-skills](https://github.com/Eita19/openclaw-skills) — OpenClaw Skills Collection*
