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

### alternative_tracing_methods.ipynb

This notebook explores different approaches to implement tracing in LangSmith beyond the basic `@traceable` decorator.

**Tracing Methods Covered:**

1. **LangChain/LangGraph Integration** - Automatic tracing through environment variables
   - Built a simple RAG graph using LangGraph's StateGraph
   - Demonstrated automatic trace logging without decorators
   - Passing metadata through config parameters

2. **Trace Context Manager** - Manual control over trace blocks
   - Using `with trace()` for specific code sections
   - Explicitly defining inputs, outputs, and metadata
   - Fine-grained control over trace attributes

3. **wrap_openai** - Automatic OpenAI client wrapping
   - Wrapping OpenAI client for automatic trace logging
   - No need for decorators on OpenAI API calls
   - Compatible with `langsmith_extra` parameters

4. **RunTree API** - Manual trace construction
   - Creating root and child runs manually
   - Explicit control over trace hierarchy
   - Posting runs and outputs individually

**Experiments:**
- Performance comparison between different tracing methods
- Testing consistency across all approaches

## Module 2: Datasets and Evaluation

### dataset_upload.ipynb

This notebook demonstrates how to create and manage datasets in LangSmith for evaluation purposes.

**Dataset Operations:**

1. **Dataset Creation** - Creating a new dataset programmatically
2. **Example Upload** - Bulk uploading Q&A pairs to the dataset
3. **Dataset Verification** - Checking uploaded examples and statistics
4. **Dataset Augmentation** - Adding variations and new examples

**Features Demonstrated:**
- Creating datasets with the LangSmith Client
- Formatting inputs and outputs for bulk upload
- Dataset quality analysis (question/answer length statistics)
- Live testing with the RAG application
- Augmenting datasets with new examples

### evaluators.ipynb

This notebook covers creating custom evaluators to assess LLM application quality.

**Evaluator Types:**

1. **Simple Evaluators** - Basic comparison functions
   - Exact match checking
   - Custom scoring logic

2. **LLM-as-Judge** - Using LLMs to evaluate outputs
   - Semantic similarity scoring (1-10 scale)
   - Structured output with Pydantic models
   - Comparing run outputs against reference answers

3. **Multi-Metric Evaluation Suite**
   - Length appropriateness checker
   - Technical term coverage evaluator
   - Yes/No consistency validator

**Key Concepts:**
- Evaluators take inputs, reference outputs, and run outputs
- Return score and key for tracking
- Can use both Run and Example schemas
- Combining multiple evaluators for comprehensive assessment


## Module 3: Prompt Engineering

### playground_experiments.ipynb
This notebook has some example screenshots from the video 'Playgrounds'. I learnt about the playground page on langchain for comparing 2 different prompts. 
Messed around with a few different models, system prompts, questions and learnt how to compare multiple prompts together. It is also possible to see metrics like time taken, input/output cost.
I tried multiple repetitions after turning off streaming, which may be useful when the model has a higer temperature. Output schema or tools can also be used with some models. Lastly, I experimented with some testing on sample datasets.

### prompt_hub.ipynb
key learnings are prompt management, model integration and version control of prompts. I created a batman/hero persona by giving the model a prompt. i learned to push prompts and pull them from langchain. converted langchain propmts to openAI format for direct API calls. tested prompts with different input parameters and team configurations 