# Layer 3: prompts/ — Where AI Instructions Are Managed Properly

```
prompts/
├── templates.py
└── registry.py
```

In many AI demos, prompts are written directly inside the main code file. Something like this:

```python
prompt = "You are a helpful AI assistant. Answer the user question."
```

For a small demo, this is fine. But in a production AI app, this becomes risky and messy very quickly. Because prompts are not just random text. In a real AI system, prompts are part of the product logic. They decide how the AI behaves, how it answers, what format it follows, what rules it respects, and what it should avoid. That is why we create a separate `prompts/` layer.

The purpose of this layer is simple:

The `prompts/` layer keeps all AI instructions organized, reusable, versioned, and easy to improve.

### Why Hardcoded Prompts Are a Problem

When prompts are hardcoded inside business logic, they become difficult to manage. For example, imagine you have prompts inside:

- `main.py`
- `rag_pipeline.py`
- `document_grader.py`
- `query_router.py`
- `conversation.py`

Now, when you want to improve one prompt, you have to search through multiple files. This creates many problems.

- You may accidentally update the wrong prompt.
- You may not know which prompt is used by which feature.
- You may break one AI flow while fixing another.
- You may not be able to test prompt versions properly.
- You may lose track of what changed and why.

In production, this is dangerous. Because a small prompt change can completely change the AI output.

### templates.py

This file stores reusable prompt templates. For example:

```python
GRADE_ANSWER_PROMPT = """
You are an expert teacher. Compare the student's answer with the reference answer.
Return:
- marks
- missing points
- wrong points
- feedback
- final score
"""
```

This keeps prompts clean and separate from the main application logic. Now your code can simply call the required prompt when needed. For example:

```python
from prompts.templates import GRADE_ANSWER_PROMPT
```

This makes your app easier to maintain.

### registry.py

This file works like a prompt manager. It tells the system which prompt should be used for which task. For example:

| Task | Prompt |
|---|---|
| grading task | `grade_answer_prompt_v1` |
| RAG answer | `rag_answer_prompt_v2` |
| query rewrite | `query_rewrite_prompt_v1` |
| safety check | `safety_prompt_v3` |
| summary task | `summary_prompt_v1` |

This is useful because production AI apps usually have multiple prompts. Not one. You may have different prompts for:

- Answer grading
- Query rewriting
- RAG response generation
- Output formatting
- Safety checking
- Feedback generation
- JSON structured output
- Summarization
- Routing decisions

The registry keeps everything organized.

### Why Prompt Versioning Matters

Prompt versioning is very important in real AI products. Imagine your current grading prompt is working well. Then you improve it and deploy a new version. But suddenly, the model starts giving lower marks than before. Now what? If you do not have prompt versioning, you may not know what changed. But if your prompts are versioned, you can compare:

- `grade_answer_prompt_v1`
- `grade_answer_prompt_v2`
- `grade_answer_prompt_v3`

This helps you test, debug, and roll back if needed. In production AI, prompt changes should be treated like code changes. They should be tracked, tested, and reviewed.

### Why Typed Prompts Matter

Typed prompts mean the prompt expects a clear input and returns a clear output. For example, a grading prompt should not return random text. It should return something structured like this:

```json
{
  "question_number": 1,
  "marks_awarded": 4,
  "total_marks": 5,
  "missing_points": ["Definition was incomplete"],
  "wrong_points": [],
  "feedback": "Good answer, but add one more key point."
}
```

This is very important because your frontend, database, reports, and dashboards need predictable data. If the AI returns a random paragraph every time, your app becomes difficult to use. So prompts should guide the model to return proper structured output.

### Why We Need This Layer

The `prompts/` layer exists because prompts are not temporary strings. They are the behavior engine of your AI app.

- A bad prompt can make the system unreliable.
- A missing rule can create unsafe output.
- An unstructured prompt can break your frontend.
- An unversioned prompt can make debugging impossible.

That is why production AI apps should never treat prompts casually. They should be managed properly.
