# RAG

## RAG Overview

The **Document Knowledge API** can be extended with Retrieval-Augmented Generation (RAG) to help applications retrieve relevant technical documentation and use that information to support AI-generated answers.

RAG allows the system to retrieve relevant content from the Document Knowledge API's knowledge source before providing that content to an AI model.

### RAG Flow

**Document Knowledge API → Knowledge Source → Retrieval → Relevant Context → AI Model → Generated Answer**

For example, when a user asks a question about a technical document, the system can retrieve the relevant documentation and provide it as context for the AI response.

## Embeddings

Embeddings are numerical representations of text that capture its meaning and relationships with other text.

In the Document Knowledge API's RAG workflow, document content can be converted into embeddings so that the system can compare the meaning of stored documentation with a user's question.

### Example

A document contains:

> Customers can return unused products within 30 days.

The document content can be converted into an embedding.

A user may ask:

> Can I return my unused product after 20 days?

The question can also be converted into an embedding and compared with stored document embeddings.

### Purpose

Embeddings help the RAG workflow identify documentation that is semantically relevant to the user's question.

## Chunking

Chunking is the process of dividing large technical documents into smaller, meaningful sections.

For the Document Knowledge API, a large technical document could contain multiple topics. Dividing the document into focused chunks allows the RAG workflow to retrieve the information relevant to a user's question.

### Example

A document could be divided into chunks such as:

- Return eligibility
- Return period
- Refund processing
- Non-returnable products

If a user asks about the return period, the relevant chunk can be retrieved instead of using the entire document.

### Good Chunking

Chunks should keep related information together and contain enough context to remain meaningful when retrieved.

## Vector Search

Vector search finds information by comparing the embeddings of a user's question with the embeddings of stored document chunks.

In the Document Knowledge API's RAG workflow:

1. The user's question is converted into an embedding.
2. The question embedding is compared with stored document embeddings.
3. The system identifies the most semantically relevant document chunks.

### Example

User question:

> Can I return my unused product after 20 days?

The system may identify this document chunk as highly relevant:

> Customers can return unused products within 30 days.

Vector search focuses on **meaning**, so the wording does not have to match exactly.

## Retrieval and Grounding

### Retrieval

Retrieval is the process of finding and obtaining relevant information from the Document Knowledge API's knowledge source.

Vector search helps identify relevant document chunks, and retrieval obtains those chunks for use by the AI model.

### Grounding

Grounding means using the retrieved documentation as the basis for the AI-generated response.

For example, if the retrieved documentation states:

> Customers can return unused products within 30 days.

The AI should use this information when answering a question about the return period.

### Important Consideration

Grounding can reduce unsupported answers and hallucinations, but it does not guarantee correctness. If the underlying documentation is outdated, incomplete, or incorrect, the AI response may also be incorrect.

## RAG Workflow

The RAG workflow connects the Document Knowledge API's documentation with an AI model.

### Workflow

1. Prepare technical documentation.
2. Divide documents into meaningful chunks.
3. Create embeddings for the document chunks.
4. Store the document representations.
5. Receive the user's question.
6. Create an embedding for the question.
7. Perform vector search.
8. Retrieve relevant documentation.
9. Provide the retrieved documentation to the AI model as context.
10. Generate the final response.

### Simplified Flow

**Document → Chunk → Embed → Store → User Question → Search → Retrieve → Ground → Generate**

### Example

User asks:

> Can I return my unused product after 20 days?

The RAG workflow retrieves the relevant documentation stating that unused products can be returned within 30 days.

The retrieved documentation is provided to the AI model as context, allowing it to generate an answer based on the Document Knowledge API's knowledge source.

## RAG Implementation Guide

This guide describes how RAG could be incorporated into the Document Knowledge API.

### Implementation Flow

1. Prepare trusted technical documentation.
2. Divide documentation into meaningful chunks.
3. Generate embeddings for the chunks.
4. Store the embeddings with their associated documentation.
5. Convert the user's question into an embedding.
6. Search for semantically relevant documentation.
7. Retrieve the most relevant chunks.
8. Provide the retrieved content to the AI model.
9. Generate the response using the retrieved content as context.
10. Validate the response against the source documentation.

The exact implementation can vary depending on the AI provider, embedding model, vector storage solution, and application architecture.

## RAG Testing

RAG testing verifies whether the Document Knowledge API's knowledge can be retrieved correctly and whether AI-generated responses are supported by the retrieved documentation.

### Example Tests

| Test | Expected Result |
|---|---|
| Ask a question covered by the documentation | Relevant documentation is retrieved |
| Ask the same question using different wording | Semantically relevant documentation is retrieved |
| Ask about unsupported information | AI should not invent information |
| Ask a question involving multiple document sections | Relevant sections are retrieved |
| Compare the AI response with source documentation | Response should be supported by the documentation |

### Key Evaluation Areas

- Retrieval relevance
- Answer factuality
- Grounding
- Hallucination risk
- Response consistency

## RAG Troubleshooting

Common RAG issues can occur at different stages of the Document Knowledge API's RAG workflow.

| Problem | Possible Cause |
|---|---|
| Irrelevant documentation retrieved | Poor chunking or search results |
| Relevant documentation not retrieved | Poor document structure or retrieval |
| AI gives unsupported information | Weak grounding or insufficient context |
| Answer is incomplete | Important documentation was not retrieved |
| AI uses outdated information | Knowledge source is outdated |
| Similar questions produce different results | Retrieval or generation inconsistency |

### Troubleshooting Approach

Identify which stage of the workflow may be causing the problem:

**Chunking → Embeddings → Search → Retrieval → Grounding → Generation**

Testing each stage separately can help identify where the issue occurs.
