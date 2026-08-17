# Layer 1: services/ — The Brain of the AI Application

```
services/
├── rag_pipeline.py
├── semantic_cache.py
├── conversation.py
├── query_rewriter.py
└── query_router.py
```

The purpose of this layer is simple:

It controls how the user's question moves through the AI system.

Think of `services/` like the main control room of your AI app.

When a user asks a question, this layer decides:

- What is the user really asking?
- Do we need to rewrite the query?
- Do we need to search documents?
- Can we use a cached answer?
- Which AI model or agent should handle this request?
- How should the final response be prepared?

This is where your AI app starts becoming a real system instead of a simple API call.

### rag_pipeline.py

This file handles the RAG flow. RAG means Retrieval-Augmented Generation. In simple words, before asking the AI model to answer, we first search our own knowledge base or documents and give the model the right context.

Without RAG, the model answers from general knowledge. With RAG, the model answers using your actual data. For example, in an AI auto-grading app, the student's answer should not be checked randomly. The system should first retrieve the teacher's reference answer, then compare the student answer with it. That work belongs inside the RAG pipeline.

### semantic_cache.py

This file helps save time and cost. Sometimes users ask the same or very similar questions again and again. Instead of calling the AI model every time, semantic cache checks whether a similar question was already answered before. If yes, it can return the previous useful response.

This helps in three ways:

- It reduces cost.
- It makes responses faster.
- It avoids unnecessary model calls.

In production AI apps, cost control is very important. A small demo may work fine, but when hundreds or thousands of users start using the app, every extra AI call matters.

### conversation.py

This file manages conversation memory.

A user may ask:

> What is RAG?

Then the next question may be:

> Can you explain it with an example?

The second question depends on the first one. So the AI system needs to understand the conversation flow. The `conversation.py` file helps manage previous messages, user context, session history, and continuity. Without this layer, the AI app may forget what the user was talking about.

### query_rewriter.py

Users do not always ask perfect questions. Sometimes they write short, unclear, or messy queries.

For example:

> grade this

But the system may need to understand:

> Compare this student answer sheet with the teacher reference answer sheet and generate marks with feedback.

That is where query rewriting helps. The `query_rewriter.py` file improves the user's raw question before sending it to retrieval or the model. It makes the query cleaner, more specific, and easier for the system to understand.

This improves answer quality a lot.

### query_router.py

Not every user request should go to the same flow.

- Some questions need RAG.
- Some need an agent.
- Some need a direct AI response.
- Some need a database lookup.
- Some should be blocked by security.

The query router decides where the request should go.

For example:

- User asks a document-based question → send to RAG pipeline
- User asks for grading → send to document grader agent
- User asks a simple explanation → send to normal LLM flow
- User asks unsafe content → send to security layer

This makes the system smarter and more organized.

### Why We Need This Layer

The `services/` layer exists because production AI apps need control. A simple demo can directly call the model. But a real AI product needs a proper flow. It needs to understand the request, improve the query, retrieve context, manage memory, reduce cost, choose the right path, and return a reliable answer. That is why `services/` is not just a folder. It is the brain of the AI system.
