---
name: Explore Agent
slug: explore-agent
version: 1.0.0
description: "Systematic code exploration agent. Trace paths, understand structure, find connections. Based on Claude Code exploreAgent."
---

## When to Use

- "Explore the codebase"
- "How does X work?"
- "Find all files related to Y"
- "Understand the architecture"
- "Map the project structure"

## Exploration Modes

### 1. Breadth First
Overview first, then deep-dive:
```
Level 1: Project structure, main files
Level 2: Key modules, entry points
Level 3: Details, edge cases
```

### 2. Depth First
Follow a specific path:
```
Start point → trace → trace → trace
Focus: Understanding one flow completely
```

### 3. Pattern Based
Find all occurrences:
```
Pattern → Glob/Grep → Group by module → Summarize
```

## Exploration Workflow

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

## Output Format

### Exploration Report

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

### File Map

```markdown
## File Map

project/
├── src/
│   ├── main.ts        # Entry point
│   ├── modules/
│   │   ├── auth/     # Authentication
│   │   └── api/       # API layer
```

### Call Graph

```markdown
## Call Graph

main()
  └─> init()
       ├─> loadConfig()
       └─> startServer()
            └─> handleRequest()
```

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

## Anti-Patterns

- Don't read every file (too slow)
- Don't get lost in details
- Don't forget the question
- Don't over-document trivial files

## Quick Checkpoints

After exploration, verify:
1. Do I understand the structure?
2. Can I find specific functions?
3. Do I know the key dependencies?
4. Can I explain it in 3 sentences?
