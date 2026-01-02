# Hint Layer Architecture

## 1. Introduction
The Hint Layer is a modular AI-assisted scaffolding engine designed to support
students learning to code. It provides structured, progressive hints without
revealing full solutions, ensuring academic integrity and promoting deep
learning.

This document describes the system architecture, data flow, and pedagogical
principles underpinning the design.

---
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

The Hint Layer processes student code, detects misconceptions, constructs
context-aware prompts, and generates progressive hints through a Large Language
Model (LLM). A parallel **Frustration Detection Layer** monitors behavioural
signals to determine when a student may need human intervention.

Student Code
     │
     ▼
Error Detector ───► Prompt Builder ───► LLM Engine ───► Hint Formatter
     │                                                      │
     └──────────────► Frustration Detector ◄────────────────┘
                                │
                                ▼
                         Mentor Notification

At a high level, the system works as follows:

- At a high level:

- **Student Code** is captured from the editor.  
- The **Error Detector** performs static analysis.  
- The **Prompt Builder** constructs a structured prompt.  
- The **LLM Engine** generates a pedagogically aligned hint.  
- The **Hint Formatter** applies progressive scaffolding rules.  
- The **Frustration Detector** monitors behavioural indicators.  
- If needed, a **mentor notification** is triggered.


This architecture ensures that the AI supports learning without replacing the
student’s own reasoning process.


---

## 3. Components
### 3.1 Error Detector
- Performs lightweight static analysis  
- Identifies syntax, logic, and conceptual errors  
- Classifies error type  
- Outputs structured metadata  

---

### 3.2 Prompt Builder
Constructs a context-rich prompt including:
- task description  
- student code  
- error metadata  
- scaffolding level  
- academic integrity guardrails  

---

### 3.3 LLM Engine
- Receives structured prompts  
- Generates hints aligned with scaffolding theory  
- Avoids providing full solutions  

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

## 4. Frustration Detection Layer

The Frustration Detection Layer monitors behavioural indicators that suggest a
student is struggling. It does not infer emotional state; instead, it uses
objective signals such as:

- repeated errors  
- excessive hint requests  
- long periods without progress  
- oscillating code patterns  
- increasing error severity  

These signals are combined into a **frustration score**. When the score exceeds
a threshold, the system triggers a **mentor intervention event**, allowing a
human educator to provide timely support.

This layer ensures that students receive help at the right moment, preventing
disengagement and supporting mastery-based learning.

### 4.1 Frustration Scoring Model

The system computes a frustration score based on weighted behavioural indicators:

frustration_score =
    (hint_requests * 2) +
    (time_stuck_minutes * 1.5) +
    (repeated_errors * 3) +
    (no_progress_events * 4)

When the score exceeds a configurable threshold, the system triggers a mentor
intervention event.

## 5. Pedagogical Foundations
The architecture is grounded in:
- Vygotsky’s Zone of Proximal Development  
- Scaffolding theory  
- Mastery learning  
- Cognitive load management  
- Responsible AI principles  

---

## 6. Future Extensions
- Adaptive hint sequencing  
- Teacher dashboards  
- Misconception analytics  
- Multi-language support  
- Integration with LMS platforms  

---

## 7. Conclusion
This architecture represents a novel approach to AI-assisted learning that
prioritises student thinking, academic integrity, and pedagogical rigour. It is
modular, extensible, and suitable for integration into modern coding education
environments.


