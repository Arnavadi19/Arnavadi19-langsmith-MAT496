# LangSmith Tracing and Evaluation - MAT496 - Arnav Aditya - 2210110189

This repository contains notebooks demonstrating LangSmith tracing capabilities and RAG (Retrieval Augmented Generation) implementations.

## Module 1: Tracing Basics

### tracing_basics.ipynb

This notebook demonstrates the fundamentals of tracing with LangSmith for a RAG application.

**RAG System Setup:**
- Uses OpenAI's `gpt-4o-mini` model
- Implements a vector database retriever for document retrieval
- Follows a three-sentence maximum response format

**Tracing Implementation:**
The notebook shows how to trace a complete RAG pipeline with three main components:

1. **`retrieve_documents()`** - Retrieves relevant documents from a vector database using sklearn
2. **`generate_response()`** - Formats retrieved documents and generates responses using the LLM
3. **`call_openai()`** - Handles the actual OpenAI API calls
4. **`langsmith_rag()`** - Orchestrates the full RAG workflow

**Features Demonstrated:**
- Basic tracing using the `@traceable` decorator
- Adding metadata to trace runs for better organization and filtering
- Passing runtime metadata dynamically using `langsmith_extra`

### types_of_runs.ipynb

This notebook explores different types of runs supported by LangSmith and their proper formatting requirements.

**Run Types Covered:**

1. **LLM Runs** - Special formatting for chat models with proper input/output structures
2. **Streaming LLM Runs** - Using `reduce_fn` to aggregate streaming chunks
3. **Retriever Runs** - Proper document format with `page_content`, `type`, and `metadata` fields
4. **Tool Calling** - Custom rendering for function calls made by the model

**Examples Implemented:**
- Weather query tool that gets current temperature for a location
- Calculator tool that performs basic arithmetic operations (+, -, *, /)
- Proper tool response formatting with `tool_call_id` tracking

