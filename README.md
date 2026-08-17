# 9-Layer Breakdown of Production-Ready AI Systems

### A demo is one file. Production AI is retrieval, routing, security, evaluation, observability, agents, and system design working together.

## Production-Ready AI Systems

```
production-ai-app/
│
├── app/
│   ├── main.py
│   ├── config.py
│   ├── models.py
│   ├── Dockerfile
│   │
│   ├── components/
│   │   ├── hybrid_retriever.py
│   │   └── reranker.py
│   │
│   ├── services/
│   │   ├── rag_pipeline.py
│   │   ├── semantic_cache.py
│   │   ├── conversation.py
│   │   ├── query_rewriter.py
│   │   └── query_router.py
│   │
│   ├── prompts/
│   │   ├── templates.py
│   │   └── registry.py
│   │
│   ├── agents/
│   │   ├── document_grader.py
│   │   ├── query_decomposer.py
│   │   ├── adaptive_router.py
│   │   └── tools/
│   │       ├── vector_search.py
│   │       ├── web_search.py
│   │       └── code_search.py
│   │
│   └── security/
│       ├── input_guard.py
│       ├── content_filter.py
│       └── output_filter.py
│
├── evaluation/
│   ├── golden_dataset.json
│   ├── offline_eval.py
│   ├── online_monitor.py
│   └── eval_results/
│
├── observability/
│   ├── tracer.py
│   ├── feedback.py
│   └── cost_tracker.py
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── index_config/
│
├── scripts/
│   ├── seed.py
│   ├── migrate.py
│   └── healthcheck.py
│
├── frontend/
│   ├── app.py
│   ├── static/
│   ├── requirements.txt
│   └── Dockerfile
│
├── tests/
│   ├── test_retrieval.py
│   ├── test_cache.py
│   └── test_routing.py
│
├── docs/
│   ├── architecture.md
│   ├── api_reference.md
│   └── deployment.md
│
├── .claude/
│   └── rules/
│       ├── code-style.md
│       └── testing.md
│
├── CLAUDE.md
├── AGENTS.md
├── docker-compose.yml
├── pyproject.toml
└── README.md
```

## Layers

- [Layer 1: services/ — The Brain of the AI Application](layers/layer-1-services.md)
- [Layer 2: agents/ — The Workers That Think and Take Action](layers/layer-2-agents.md)
- [Layer 3: prompts/ — Where AI Instructions Are Managed Properly](layers/layer-3-prompts.md)
- [Layer 4: security/ — The Safety Gate of the AI System](layers/layer-4-security.md)
- [Layer 5: evaluation/ — The Testing Layer for AI Quality](layers/layer-5-evaluation.md)
