# Layer 7: .claude/ — The AI Coding Assistant Memory Layer

```
.claude/
└── rules/
    ├── code-style.md
    └── testing.md
CLAUDE.md
AGENTS.md
```

This layer is a little different from the others. Most folders are for your application. But `.claude/`, `CLAUDE.md`, and `AGENTS.md` are for your AI coding assistant.

Today, many developers use AI tools like Claude Code, Cursor, Codex, Copilot, or other coding agents. These tools can write files, refactor code, create tests, fix bugs, and understand project logic.

But there is one problem. If the AI coding assistant does not understand your project rules, it may generate random code.

- It may use the wrong folder.
- It may break your architecture.
- It may ignore your naming style.
- It may skip tests.
- It may change files that should not be touched.
- It may write code that works, but does not fit your system.

That is why we need this layer. The purpose of this layer is simple:

The `.claude/` layer gives your AI coding assistant project context before it touches your codebase.

### Why This Layer Matters

When a human developer joins a project, we do not just say:

> Here is the code. Start changing files.

We explain the project.

- We explain the architecture.
- We explain the folder structure.
- We explain coding standards.
- We explain testing rules.
- We explain what should be avoided.
- We explain how features should be added.

AI coding assistants need the same guidance. Without this context, they guess. And guessing inside a production AI codebase is dangerous.

### CLAUDE.md

This file explains the project to the AI assistant. You can think of it like a project instruction manual.

For example:

```markdown
# Project Context
This is a production-ready AI application.

The system uses:
- RAG pipeline for document-based answers
- semantic cache to reduce repeated model calls
- agents for grading and task decomposition
- prompt registry for versioned prompts
- security guards for input, content, and output
- evaluation layer for offline and online quality checks
- observability for tracing, feedback, and cost tracking

Do not place AI logic directly inside main.py.
Use the existing layer-based architecture.
```

This helps the AI assistant understand how your project is designed. Now when you ask it to add a feature, it knows where that feature should go.

### AGENTS.md

This file explains how agents should behave in the project.

For example:

```markdown
# Agent Rules
Agents should be small and task-specific.

Each agent should:
- have one clear responsibility
- use tools through the tools/ folder
- return structured output
- handle failure safely
- log important decisions
- avoid direct database writes unless required
```

This is useful when your app has multiple agents like:

- `document_grader.py`
- `query_decomposer.py`
- `adaptive_router.py`

Instead of allowing every agent to behave differently, `AGENTS.md` creates consistency. It keeps your AI system clean and predictable.

### .claude/rules/code-style.md

This file defines coding style rules.

For example:

```markdown
# Code Style Rules
- Keep functions small and readable.
- Do not hardcode prompts inside service files.
- Use type hints wherever possible.
- Keep business logic separate from API routes.
- Use meaningful names for services, agents, and tools.
- Follow the existing folder structure.
```

This helps the AI assistant write code in your style. Otherwise, every generated file may look different.

- One file may be clean.
- Another may be messy.
- Another may duplicate logic.
- Another may ignore the architecture.

Code style rules reduce that problem.

### .claude/rules/testing.md

This file tells the AI assistant how testing should be done.

For example:

```markdown
# Testing Rules
When adding or changing a feature:
- Add or update tests.
- Test retrieval logic separately.
- Test prompt output format.
- Test security guards.
- Test routing decisions.
- Do not remove existing tests unless there is a clear reason.
```

This is important because AI coding tools often focus on "making code work," but production teams also need tests.

Especially in AI systems, testing matters because small changes can break behavior silently.

### Why We Need This Layer

The `.claude/` layer exists because AI coding assistants are powerful, but they need direction. Without project context, they can create code that looks correct but damages the architecture. With project context, they become more useful.

- They understand your structure.
- They follow your rules.
- They place code in the right folders.
- They avoid hardcoded prompts.
- They remember testing expectations.
- They behave more like a trained team member.

This layer is not about the AI app answering users. It is about helping developers maintain the AI app safely.
