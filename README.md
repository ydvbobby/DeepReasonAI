# DeepReasonAI
### Evaluating How Students Think, Not Just What They Answer

DeepReasonAI is a reasoning-first educational assessment system designed to
combat rote learning and exam-centric evaluation. Instead of grading final
answers, it evaluates **student reasoning**, diagnoses misconceptions, and
provides explainable feedback at scale.

Built for the Indian education context, DeepReasonAI aligns with
competency-based learning goals and works within real classroom constraints.

---

## 🚀 Key Features

- Conceptual (why / how / what-if) question generation
- Free-text answer evaluation (no MCQs)
- Multi-dimensional reasoning assessment:
  - Logical Flow
  - Conceptual Correctness
  - Assumptions
  - Explanation Clarity
  - Misconceptions
- Explainable, structured feedback for students
- Class-level analytics and insights for teachers
- Modular, scalable AI architecture

---

## 🧠 System Overview

DeepReasonAI uses a **controller-based AI architecture**:
- A central orchestrator manages the learning flow
- Specialized AI tools handle question generation, evaluation, and feedback
- A multi-step evaluator graph ensures explainable reasoning assessment
- Syllabus-aligned knowledge is accessed via RAG

The system is designed to **augment teachers**, not replace them.

---

## 🛠️ Tech Stack

- **Language:** Python
- **Backend:** FastAPI
- **AI Orchestration:** LangChain (tool routing), LangGraph (multi-step evaluator)
- **Reasoning Evaluation:** Multi-step evaluator graph
- **Knowledge Access:** RAG + Vector Database
- **Frontend:** Web (chat-style UI)
- **Storage:** Relational / NoSQL DB (responses & analytics)

---

## ⚙️ How It Works (High Level)

1. Teacher or student selects a topic and grade
2. AI generates a conceptual question
3. Student submits a free-text response
4. Multi-step evaluator analyzes reasoning
5. Misconceptions and reasoning gaps are identified
6. AI generates structured feedback
7. Teacher receives class-level insights

---

## 📁 Folder Structure

```
deepreasonai/
│
├── README.md
├── requirements.md
├── design.md
│
├── app/
│   ├── main.py
│   ├── api/
│   │   └── routes.py
│   ├── orchestrator/
│   │   └── controller.py
│   ├── tools/
│   │   ├── question_generator.py
│   │   ├── reasoning_evaluator.py
│   │   ├── misconception_detector.py
│   │   └── feedback_generator.py
│   ├── memory/
│   │   ├── stm.py
│   │   └── ltm.py
│   ├── evaluation/
│   │   ├── rubrics.py
│   │   └── scoring.py
│   └── utils/
│       └── helpers.py
│
├── data/
│   ├── misconceptions/
│   ├── syllabus/
│   └── sample_inputs/
│
├── frontend/
│   ├── student_ui/
│   └── teacher_dashboard/
│
└── docs/
    └── images/
```

---

## 🎯 Project Scope

### In Scope
- Formative assessment
- Reasoning-based evaluation
- Conceptual understanding
- Teacher augmentation

### Out of Scope
- High-stakes exam grading
- Replacing board exams
- Training custom LLMs

---

## 🧪 Current Status

- System design completed
- Core AI prompts defined
- Architecture finalized
- MVP implementation in progress

---

## 🏆 Hackathon Alignment

- AI for Bharat (India-first design)
- Scalable and affordable
- Addresses real education gaps
- Uses AI for reasoning evaluation, not just content generation

---

## 👥 Team

**Team Name:** NeuroShift  
**Project:** DeepReasonAI  

---

## 📜 License

This project is developed for hackathon and educational purposes.
