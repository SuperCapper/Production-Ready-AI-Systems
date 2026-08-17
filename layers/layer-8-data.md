# Layer 8: data/ — Where Raw Knowledge Becomes Usable AI Context

```
data/
├── raw/
├── processed/
└── index_config/
```

This layer is very important for any AI app that works with documents, PDFs, reports, answer sheets, blogs, files, or internal company knowledge. In a simple AI demo, we usually upload a document and directly send it to the AI model. But in production, that is not enough. Because raw data is messy.

- PDFs may have broken text.
- Scanned images may need OCR.
- Documents may contain headers, footers, page numbers, tables, and duplicate content.
- Student answer sheets may have spelling mistakes.
- Company documents may have old and new versions mixed together.

That is why we need the `data/` layer. The purpose of this layer is simple:

The `data/` layer manages how raw files become clean, structured, searchable knowledge for the AI system.

### raw/

This folder stores the original uploaded data.

For example:

```
data/raw/
├── teacher_reference_sheet.pdf
├── student_answer_sheet_01.jpg
├── company_policy.pdf
└── product_docs.docx
```

This is the untouched version of the file. We keep raw files because sometimes processing may fail, OCR may extract wrong text, or we may need to reprocess the file later with a better model.

In simple words:

`raw/` is the original source of truth.

### processed/

This folder stores cleaned and structured data.

For example, after OCR or document parsing, the system may convert a PDF into structured JSON:

```json
{
  "question_number": 1,
  "question": "What is photosynthesis?",
  "answer": "Photosynthesis is the process by which green plants make food using sunlight, carbon dioxide, and water.",
  "marks": 5
}
```

This processed version is much easier for the AI system to use. Instead of giving the model a messy PDF, we give it clean question-answer pairs, chunks, metadata, and useful context.

In simple words:

`processed/` is where messy files become AI-ready data.

### index_config/

This folder stores configuration for search and retrieval. For example:

```
data/index_config/
├── chunking_rules.json
├── embedding_config.json
└── metadata_schema.json
```

This tells the system how to prepare data for vector search.

It may include:

- How large each text chunk should be
- Which embedding model to use
- What metadata should be stored
- How documents should be grouped
- Which fields should be searchable

This matters because RAG quality depends heavily on how your data is prepared. Bad chunks create bad retrieval. Bad retrieval creates bad AI answers. So this layer directly affects the final output quality.

### Why We Need This Layer

The `data/` layer exists because AI is only as good as the context we give it. A powerful model with messy data can still give poor answers. But a normal model with clean, structured, well-indexed data can perform much better. In production AI, data preparation is not a side task. It is one of the core parts of the system. This layer helps us keep original files safe, clean the extracted content, structure it properly, and prepare it for search.
