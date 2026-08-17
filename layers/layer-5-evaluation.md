# Layer 5: evaluation/ — The Testing Layer for AI Quality

```
evaluation/
├── golden_dataset.json
├── offline_eval.py
├── online_monitor.py
└── eval_results/
```

This is the layer most people skip.

- They build the AI feature.
- They test it with 2 or 3 examples.
- It gives a good answer.
- Then they ship it.

But production AI cannot be tested like that. Because AI output is not always fixed like normal code. The same system can behave differently depending on the prompt, model, retrieved context, user input, and temperature. That is why we need an `evaluation/` layer. The purpose of this layer is simple:

The `evaluation/` layer checks whether the AI system is actually giving useful, accurate, safe, and consistent answers.

### Why Evaluation Matters

In normal software, we test things like:

- Does the button work?
- Does the API return data?
- Does login succeed?
- Does the database save the record?

But in AI software, we also need to test things like:

- Is the answer correct?
- Did the AI use the right context?
- Did it hallucinate?
- Did it follow the expected format?
- Did it give fair marks?
- Did it miss important points?
- Did the answer become worse after a prompt change?

This is why AI evaluation is different from normal testing. A production AI app should not only work technically. It should also work intelligently.

### golden_dataset.json

This file contains your best test examples. A golden dataset is a small but high-quality collection of inputs and expected outputs. For example, in an AI auto-grading app, it may look like this:

```json
[
  {
    "question": "What is photosynthesis?",
    "teacher_answer": "Photosynthesis is the process by which green plants use sunlight, carbon dioxide, and water to make food and release oxygen.",
    "student_answer": "Photosynthesis is when plants make food using sunlight and release oxygen.",
    "expected_marks": 4,
    "total_marks": 5,
    "expected_feedback": "Good answer, but carbon dioxide and water are missing."
  }
]
```

This helps you check whether your AI system is grading properly. Without a golden dataset, you are only guessing that your AI works. With a golden dataset, you can measure it.

### offline_eval.py

This file runs evaluation before deployment. For example, before you release a new prompt, new model, or new RAG pipeline, you can run offline evaluation. It checks your system against the golden dataset. It can answer questions like:

- Did the new prompt improve grading?
- Did the model become stricter?
- Did the feedback quality improve?
- Did the JSON output break?
- Did the system miss important reference points?

This is very important. Because in AI apps, one small prompt change can affect many outputs. A prompt may look better in one example but perform worse in twenty others. Offline evaluation helps catch that before users see the problem.

### online_monitor.py

Offline evaluation happens before deployment. Online monitoring happens after deployment. Once real users start using your AI app, you need to watch how the system performs in the real world.

The `online_monitor.py` file can track things like:

- How often does the AI fail?
- How often does it return invalid JSON?
- How many users give negative feedback?
- Which questions produce low-confidence answers?
- Which requests cost too much?
- Which outputs need human review?

This is important because real users ask messy, unexpected, and unclear questions. Your test dataset may be clean. Real users are not. Online monitoring helps you improve the system continuously.

### eval_results/

This folder stores evaluation reports. For example:

```
eval_results/
├── grading_eval_2026_06_01.json
├── rag_eval_2026_06_02.json
└── prompt_v2_comparison.md
```

These reports help you compare versions. You can track:

- Prompt v1 vs Prompt v2
- Model A vs Model B
- Old RAG pipeline vs new RAG pipeline
- Without reranker vs with reranker
- Old grading logic vs improved grading logic

This gives you confidence before making changes. Instead of saying:

> I think this prompt is better.

You can say:

> This prompt improved accuracy from 72% to 84% on our test dataset.

That is how AI engineering becomes measurable.

### Why We Need This Layer

The `evaluation/` layer exists because AI systems can fail silently.

- The app may still return a response.
- The API may still work.
- The frontend may still show an answer.

But the answer may be wrong. That is dangerous. Evaluation helps us check quality before and after deployment. It gives us a way to measure improvement, catch regressions, and build trust in the system. A demo can survive without evaluation. A production AI product cannot.
