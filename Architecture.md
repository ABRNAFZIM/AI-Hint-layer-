# Hint Layer Architecture

## 1. Introduction
The Hint Layer is a modular AI-assisted scaffolding engine designed to support
students learning to code. It provides structured, progressive hints without
revealing full solutions, ensuring academic integrity and promoting deep
learning.

This document describes the system architecture, data flow, and pedagogical
principles underpinning the design.

---
## 2. High-Level Architecture

The Hint Layer is designed as a modular pipeline that processes student code,
detects misconceptions, constructs context-aware prompts, and generates
progressive hints through a Large Language Model (LLM). Each component has a
clear responsibility, ensuring transparency, academic integrity, and
pedagogically aligned support.

Student Code
     │
     ▼
Error Detector ───► Prompt Builder ───► LLM Engine ───► Hint Formatter ───► Editor UI

At a high level, the system works as follows:

- **Student Code** is captured directly from the editor.
- The **Error Detector** performs static analysis to identify syntax, logic, or
  conceptual issues.
- The **Prompt Builder** constructs a structured, context-rich prompt for the
  LLM, including the task, the student’s code, and the detected error.
- The **LLM Engine** generates a pedagogically aligned hint rather than a full
  solution.
- The **Hint Formatter** applies progressive scaffolding rules to determine the
  appropriate hint level.
- The **Editor UI** displays the hint and allows the student to request deeper
  levels of support.

This architecture ensures that the AI supports learning without replacing the
student’s own reasoning process.


---

## 3. Components

### 3.1 Error Detector
- Performs lightweight static analysis  
- Identifies syntax, logic, and conceptual errors  
- Classifies error type (e.g., IndexError, off-by-one, infinite loop)  
- Outputs structured metadata for the Prompt Builder  

### 3.2 Prompt Builder
Constructs a context-rich prompt for the LLM, including:
- Task description  
- Student code  
- Error metadata  
- Instruction to provide a hint, not a solution  
- Guardrails to prevent over-helping  

Example prompt structure:

---

### 3.3 LLM Engine
- Receives structured prompts  
- Generates pedagogically aligned hints  
- Uses system-level instructions to maintain academic integrity  

---

### 3.4 Progressive Hint Formatter
Implements four levels of scaffolding:

1. **Metacognitive Nudge**  
   Encourages reflection without pointing to the error.

2. **Conceptual Guidance**  
   Highlights the relevant concept or area of the code.

3. **Specific Technical Hint**  
   Identifies the exact issue without giving the fix.

4. **Worked Example (Non-Solution)**  
   Provides a similar solved example for comparison.

---

### 3.5 Editor Integration
Hints can be displayed via:
- Sidebar panel  
- Tooltip  
- “Request Hint” button  
- Progressive reveal interface  

---

## 4. Pedagogical Foundations
The architecture is grounded in:
- Vygotsky’s Zone of Proximal Development  
- Scaffolding theory  
- Mastery learning  
- Cognitive load management  
- Responsible AI principles  

---

## 5. Future Extensions
- Adaptive hint sequencing  
- Teacher dashboards  
- Misconception analytics  
- Multi-language support  
- Integration with LMS platforms  

---

## 6. Conclusion
This architecture represents a novel approach to AI-assisted learning that
prioritises student thinking, academic integrity, and pedagogical rigour. It is
designed to be modular, extensible, and suitable for integration into modern
coding education environments.

