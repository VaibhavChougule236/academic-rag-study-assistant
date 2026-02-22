# Experiment Results Summary – DBMS RAG Study Assistant

## Experiment 1: Chunking Strategies

### Methodology

Compared:

- Fixed-size chunking

- Sentence-based chunking

Used same:

- Embedding model

- Top-k value

- Prompt

- 10 DBMS questions

### Observations

Fixed-size chunking:

- More stable retrieval

- Less repetition

- Cleaner context

Sentence-based chunking:

- Sometimes provided more explanation

- But introduced repeated or merged content

- Less consistent

### Conclusion

Fixed-size chunking worked better for my DBMS PDFs due to formatting inconsistencies and merged headings.

## Experiment 2: Prompting Techniques

### Compared:

- Basic prompt

- Improved structured prompt

### Observations

Basic Prompt:

- Very short answers

- Often incomplete

Improved Prompt:

- Slightly more structured responses

- Better completeness

- Still limited by model capability

### Conclusion

Improved prompt provided marginal improvement. Prompt engineering helps, but model capability remains a limiting factor.

## Experiment 3: Retrieval Strategy (Top-k Comparison)

Tested:

- Top-k = 3

- Top-k = 5

- Top-k = 8

### Observations

Top-k = 3:

- Cleaner answers

- More focused context

Top-k = 5:

- Introduced noise

- Page numbers and headers appeared

Top-k = 8:

- Too much irrelevant context

- Answer quality degraded

### Conclusion

Increasing top-k does not always improve RAG performance.

For my dataset, top-k = 3 worked best.

## Overall Findings

1. Chunking strategy has strong impact on retrieval quality.

2. Retrieval quality matters more than quantity.

3. Prompt engineering improves clarity but cannot compensate for weak models.

4. Document preprocessing is critical in real-world RAG systems.

## Recommended Production Setup

- Fixed-size chunking

- Top-k = 3

- Cleaned text

- Improved prompt

- Sentence-transformer embeddings

- ChromaDB vector store
