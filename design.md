# Design Document – DeepReasonAI

## 1. Overview

DeepReasonAI is a reasoning-first assessment system designed to address
rote learning and exam-centric evaluation in the Indian education system.
The system generates conceptual (why/how/what-if) questions and evaluates
student responses based on how they think, rather than whether the final
answer is correct.

The core design principle is to make student reasoning visible, explainable,
and scalable using AI, while working within existing classroom and exam
constraints.

---

## 2. Design Goals

- Evaluate reasoning instead of final answers
- Provide explainable, multi-dimensional assessment
- Scale to large classrooms where human evaluation is impractical
- Remain affordable and infrastructure-light
- Augment teachers rather than replace them
- Align with Indian curriculum and assessment realities

---

## 3. High-Level Architecture

The system follows a layered architecture:

1. User Interface Layer
2. Backend / API Layer
3. AI Orchestration Layer
4. AI Tooling Layer
5. Knowledge & Data Layer


Each layer has a clear responsibility and minimal coupling.

---

## 4. User Interfaces

### 4.1 Student Interface
- Conversational interface (web/chat-style)
- Displays conceptual questions
- Accepts free-text answers
- Shows detailed reasoning-based feedback

### 4.2 Teacher Interface
- Dashboard view for class-level insights
- Aggregated reasoning scores
- Common misconception analysis
- Question-wise performance summaries

---

## 5. Backend / API Layer

The backend is implemented using FastAPI and is responsible for:
- Handling user requests
- Managing sessions
- Routing requests to the AI orchestration layer
- Persisting evaluation results and analytics

This layer does not contain any intelligence logic.

---

## 6. AI Orchestration Design

A controller agent acts as the central orchestrator of the system.

Responsibilities:
- Maintains short-term memory (STM) for the current interaction
- Decides which AI tool to invoke
- Ensures correct sequencing of question generation, evaluation, and feedback

The controller does not generate content or evaluate answers directly.

---

## 7. Memory Design

### 7.1 Short-Term Memory (STM)
Used only within a single session.

Stores:
- Current topic and grade
- Generated question
- Student response
- Temporary evaluation context

Purpose: Maintain conversational coherence.

---

### 7.2 Long-Term Memory (LTM)
Persistent pedagogical knowledge accessed via RAG.

Stores:
- Syllabus-aligned concept graph
- Evaluation rubrics
- Bloom’s taxonomy mappings
- Common misconception library

Purpose: Ensure syllabus-aware, consistent, and explainable evaluation.

---

## 8. AI Tooling Layer

The AI tooling layer consists of specialized, single-responsibility tools.

### 8.1 Conceptual Question Generator
Inputs:
- Topic
- Grade level
- Difficulty

Outputs:
- Conceptual question (why/how/what-if)
- Expected reasoning path (internal)

Design rationale:
Prevents recall-based questioning and forces conceptual thinking.

---

### 8.2 Reasoning Evaluator (Multi-Step Graph)

The evaluator is implemented as a multi-step graph rather than a single
LLM call to ensure explainability, modularity, and fairness.

Evaluation Steps:
1. Answer normalization
2. Reasoning step extraction
3. Conceptual correctness check
4. Logical flow analysis
5. Assumption identification
6. Misconception detection
7. Explanation clarity scoring
8. Score aggregation

Each step is independently debuggable and improvable.

---

### 8.3 Misconception Detection Engine
- Uses a misconception library stored in LTM
- Combines pattern-based checks with RAG
- Outputs misconception labels with confidence scores

Example:
- Mass vs Weight confusion
- Force vs Speed confusion

---

### 8.4 Feedback Generator
- Converts evaluation output into student-friendly feedback
- Highlights what was correct even if the final answer is wrong
- Suggests what to rethink
- Generates optional follow-up conceptual questions

---

## 9. Evaluation Rubrics & Scoring

Each response is evaluated independently across five dimensions:
- Logical Flow
- Conceptual Correctness
- Assumptions
- Explanation Clarity
- Misconceptions

Scores are not collapsed into a single number to preserve interpretability.

---

## 10. Data Storage & Analytics

Stored data includes:
- Student responses
- Dimension-wise evaluation scores
- Aggregated class-level analytics

The MVP does not store data for model training.

---

## 11. Technology Choices

- Large Language Models (LLMs): Natural language understanding and reasoning
- LangChain: Tool orchestration and prompt pipelines
- LangGraph: Multi-step reasoning evaluator implementation
- RAG: Syllabus-aligned and misconception-aware evaluation
- FastAPI: Lightweight backend orchestration
- Python: Core implementation language

---

## 12. Non-Goals

- Replacing board examinations
- High-stakes automated grading
- Training custom large language models
- Fully autonomous teaching systems

---

## 13. Extensibility & Future Work

- Voice-based input for accessibility
- Regional language support
- Longitudinal reasoning tracking
- Subject expansion beyond science and math
- Integration with existing LMS platforms

---

## 14. Summary

ConceptEval AI is designed as a modular, explainable, and scalable reasoning
assessment system. By separating orchestration, evaluation, and pedagogical
knowledge, the system ensures robustness, transparency, and real-world
applicability in Indian classrooms.
