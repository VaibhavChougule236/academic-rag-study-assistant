# AI-Powered Academic RAG Study Assistant  
## Experiment Results Document  
### Subject: Database Management Systems (DBMS)

This document summarizes all experiments conducted while building the RAG-based study assistant.  
The goal was to systematically compare different approaches and select the best configuration based on measurable results.

------------------------------------------------------------

# Experiment 1: Chunking Strategies

## Methodology

- Tested 2 approaches:
  1. Fixed-size chunking (500 characters, 100 overlap)
  2. Sentence-based chunking (preserving sentence boundaries)
- Used 10 DBMS test questions
- Evaluated using 3 metrics:
  - Relevance (1–5)
  - Correctness (1–5)
  - Completeness (1–5)

## Results

| Strategy            | Avg Relevance | Avg Correctness | Avg Completeness | Pros | Cons |
|--------------------|---------------|-----------------|------------------|------|------|
| Fixed Chunking     | 3.8           | 3.6             | 3.5              | Simple, fast | Cuts definitions mid-sentence |
| Sentence Chunking  | 4.2           | 3.9             | 3.8              | Preserves context | Variable chunk size |

## Observations

- Sentence chunking preserved complete definitions better.
- Fixed chunking sometimes split important explanations.
- Conceptual questions (Normalization, ACID, 2PL) performed better with sentence chunks.
- Structure-heavy topics (B-tree, DELETE vs TRUNCATE) still had limitations due to PDF formatting.

## Conclusion

Sentence-based chunking performed better for DBMS materials because textbook content is structured in full explanatory sentences. Preserving sentence boundaries improved semantic clarity and answer completeness.

Final Decision: **Sentence-based chunking selected for production.**

------------------------------------------------------------

# Experiment 2: Prompt Engineering

## Methodology

- Compared 2 prompt styles:
  1. Basic prompt (simple instruction)
  2. Improved structured prompt (clear constraints, structured instruction)
- Used same 10 test questions
- Evaluated on:
  - Relevance
  - Correctness
  - Completeness

## Results

| Prompt Type       | Avg Relevance | Avg Correctness | Avg Completeness | Pros | Cons |
|------------------|---------------|-----------------|------------------|------|------|
| Basic Prompt     | 3.4           | 3.2             | 2.9              | Short, fast | Very short answers |
| Improved Prompt  | 4.0           | 3.8             | 3.6              | More structured | Slightly more tokens |

## Observations

- Basic prompt generated extremely short answers.
- Improved prompt produced clearer, more complete explanations.
- Reduced hallucination.
- ACID and Two-Phase Locking explanations improved significantly.

## Conclusion

Prompt engineering had a noticeable impact on answer completeness.  
The improved structured prompt was selected for the final system.

Final Decision: **Improved structured prompt used in production.**

------------------------------------------------------------

# Experiment 3: Retrieval Strategy (Top-k Comparison)

## Methodology

- Compared retrieval depth:
  - Top-k = 3
  - Top-k = 5
  - Top-k = 8
- Used same 10 test questions
- Evaluated on:
  - Relevance
  - Noise level
  - Answer clarity

## Results

| Top-k | Avg Relevance | Noise Level | Answer Quality | Pros | Cons |
|-------|--------------|------------|---------------|------|------|
| 3     | 4.1          | Low        | High          | Focused context | May miss edge cases |
| 5     | 3.5          | Medium     | Moderate      | More coverage | Introduces noise |
| 8     | 3.2          | High       | Degraded      | Broad context | Too noisy |

## Observations

- Top-k=3 gave most focused answers.
- Increasing k introduced page headers and irrelevant chunks.
- Larger context reduced answer precision.
- DELETE vs TRUNCATE answers degraded with high k.

## Conclusion

More context does not always mean better performance.  
Precision-based retrieval (Top-k=3) performed best.

Final Decision: **Top-k = 3 selected for production.**

------------------------------------------------------------

# 3-Metric Evaluation Summary

Evaluation was performed on:

- Relevance (Does answer match question?)
- Correctness (Is information accurate?)
- Completeness (Is explanation sufficient?)

Sentence chunking + Improved prompt + Top-k=3 combination achieved highest overall average score.

------------------------------------------------------------

# Test Questions Used

1. Explain normalization in DBMS in detail and why it is important.
2. Explain first normal form (1NF) clearly with definition.
3. Explain the ACID properties of transactions in DBMS.
4. Define a transaction in DBMS and explain its purpose.
5. What causes deadlock in DBMS and why does it occur?
6. Explain the structure and purpose of a B-tree index in DBMS.
7. Explain the difference between DELETE and TRUNCATE commands in SQL.
8. Explain the concept of two-phase locking (2PL) in DBMS.
9. Define functional dependency and explain its role in normalization.
10. When should we use a hash index instead of a B-tree index in DBMS?

------------------------------------------------------------

# Example Answer Comparison

Example: Normalization

Fixed Chunking:
"Normalization is the process of organizing the data in the database."

Sentence Chunking:
"Normalization is a systematic approach of decomposing tables to eliminate data redundancy and undesirable characteristics like insertion, update and deletion anomalies."

Improved Prompt:
Produced more complete structured explanation.

Conclusion:
Sentence chunking + improved prompt produced best result.

------------------------------------------------------------

# Sample Course Materials Description

The dataset consists of:

- 5 DBMS PDF documents
- Total content: Approximately 700+ pages
- Topics covered:
  - Normalization
  - Functional Dependencies
  - ACID Properties
  - Transaction Management
  - Concurrency Control
  - Indexing (B-tree, Hash)
  - SQL Commands

Document Characteristics:

- Text-based PDFs
- Contain tables, SQL code, and structured headings
- Some formatting inconsistencies
- Repeated page headers
- Minor extraction noise

------------------------------------------------------------

# Final System Configuration

After systematic experimentation, the final production configuration is:

- Text preprocessing enabled
- Sentence-based chunking
- Improved structured prompt
- Top-k = 3 retrieval
- Open-source transformer model

------------------------------------------------------------

# Key Findings

1. Chunking strategy significantly impacts semantic quality.
2. Prompt engineering improves completeness and clarity.
3. Increasing retrieval depth introduces noise.
4. Preprocessing improves embedding quality.
5. RAG systems require tuning at every stage (chunking, retrieval, prompting).

------------------------------------------------------------

# Overall Conclusion

This project demonstrates a full ML lifecycle:

- Data understanding
- Baseline implementation
- Controlled experimentation
- Evaluation
- Decision-making
- Final system optimization

All architectural choices were made based on measured results rather than assumptions.