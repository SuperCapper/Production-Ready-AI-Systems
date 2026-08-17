# Layer 2: agents/ — The Workers That Think and Take Action

```
agents/
├── document_grader.py
├── query_decomposer.py
├── adaptive_router.py
└── tools/
    ├── vector_search.py
    ├── web_search.py
    └── code_search.py
```

In a simple AI demo, we usually send a prompt directly to the model and wait for an answer. But in production, some tasks are not that simple.

- Sometimes the AI needs to break a problem into smaller steps.
- Sometimes it needs to use tools.
- Sometimes it needs to check its own answer.
- Sometimes it needs to decide which path is best.
- Sometimes it needs to retry when the first answer is weak.

That is why we create the `agents/` layer. The purpose of this layer is simple:

The `agents/` layer handles tasks that need decision-making, tool usage, and self-correction.

Think of agents like specialized team members inside your AI app.

- One agent may grade documents.
- One agent may break complex questions into smaller parts.
- One agent may decide which system should handle the request.
- One agent may use tools like vector search, web search, or code search.

This makes the AI system more flexible and intelligent.

### document_grader.py

This agent is responsible for checking and grading documents. For example, in an AI auto-grading app, the system may receive a student answer sheet. The job is not only to say:

> Correct or incorrect.

A good grading agent should check:

- What did the student write?
- What is the correct reference answer?
- Which points are missing?
- Which points are wrong?
- How many marks should be given?
- What feedback should the student receive?

So instead of putting all this logic inside one prompt, we create a separate `document_grader.py` agent. This keeps the grading flow clean, reusable, and easier to improve.

### query_decomposer.py

Some user questions are too big to answer directly.

For example:

> Compare these 20 student answers with the teacher answer sheet, find mistakes, give marks, and generate feedback.

This is not one small task. It has many steps. The system needs to:

- Read the student answers
- Read the teacher reference answers
- Match question by question
- Compare meaning
- Calculate marks
- Generate feedback
- Prepare final report

The `query_decomposer.py` agent breaks a large task into smaller tasks. This is important because AI performs better when complex work is divided into clear steps.

In simple words:

Query decomposition helps the AI solve big problems step by step instead of trying to answer everything at once.

### adaptive_router.py

The adaptive router is like a smart traffic controller.

Not every request should go to the same place.

For example:

- A document grading request → document grader agent
- A simple question → normal LLM response
- A document-based question → RAG pipeline
- A coding question → code search tool
- A risky request → security layer

The `adaptive_router.py` agent decides the best path based on the user request. The word "adaptive" means it can adjust based on the situation.

- If the query is simple, it keeps the flow simple.
- If the query is complex, it sends it to the right agent or tool.
- If the query needs documents, it connects with retrieval.
- If the query looks unsafe, it can stop or redirect the request.

This helps avoid unnecessary cost and improves response quality.

### tools/

Inside agents, we also keep tools.

```
tools/
├── vector_search.py
├── web_search.py
└── code_search.py
```

Tools are external abilities given to agents. The AI model alone cannot do everything perfectly.

- It may need to search your vector database.
- It may need to search the web.
- It may need to inspect code.
- It may need to call an API.

That is why agents use tools.

#### vector_search.py

This tool searches your vector database. In a RAG-based system, this is very important. For example, before grading a student answer, the system can search the vector database and retrieve the correct teacher reference answer. Without vector search, the AI may answer based on guesswork. With vector search, the AI gets the correct context before generating the answer.

#### web_search.py

This tool is useful when the AI needs current or external information. For example, if your app needs the latest documentation, recent news, updated pricing, or new framework changes, the model should not depend only on old knowledge. The web search tool helps the agent fetch fresh information when needed.

#### code_search.py

This tool is useful for AI coding assistants or developer tools. For example, if the AI needs to understand your codebase, it should search existing files before making changes. This avoids random code generation. The AI can first check:

- Where is this function used?
- Which file contains this logic?
- What pattern does this project follow?
- What tests already exist?

This makes AI coding safer and more useful.

### Why We Need This Layer

The `agents/` layer exists because production AI apps need more than one simple response.

- They need planning.
- They need tool usage.
- They need task splitting.
- They need decision-making.
- They need self-correction.

A normal AI call answers a prompt. But an agent can follow a process. That is the difference.
