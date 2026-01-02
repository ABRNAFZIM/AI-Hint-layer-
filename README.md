# AI Scaffolding Hint Layer for Coding Education

## Overview
This repository documents the design and early prototype work for an AI-powered
**Hint Layer** that provides structured, progressive scaffolding for students
learning to code. Unlike traditional AI tutors that provide direct answers, this
system is designed to promote **critical thinking**, **academic integrity**, and
**mastery-based learning**.

The Hint Layer integrates:
- Static analysis of student code  
- Error classification  
- Context-aware prompt construction  
- Multi-level progressive hinting  
- Frustration detection and mentor escalation  
- Guardrails to prevent over-helping  
- Pedagogically grounded scaffolding (ZPD, mastery learning)

This work represents an original contribution to the field of AI-driven
education technology and demonstrates a novel approach to responsible AI in
learning environments.

---

## Key Features

### Real-time Misconception Detection
Identifies syntax, logic, and conceptual errors before generating hints.

### Progressive Hinting Engine
Four levels of scaffolding:
1. Metacognitive nudge  
2. Conceptual guidance  
3. Specific technical hint  
4. Worked example (non-solution)

### Static Analysis + LLM Hybrid Pipeline
Combines deterministic error detection with AI reasoning to ensure accuracy and reduce hallucinations.

### Context-Aware Prompt Builder
Constructs structured prompts based on:
- task description  
- student code  
- error type  
- scaffolding level  
- academic integrity guardrails  

### Frustration Detection Layer
Monitors behavioural indicators such as:
- repeated errors  
- excessive hint requests  
- long periods without progress  
- oscillating code patterns  

Triggers a **mentor intervention event** when a student is stuck.

### Academic Integrity by Design
The system is engineered to:
- avoid giving full solutions  
- encourage critical thinking  
- maintain student ownership of work  

### Editor Integration Ready
Designed to plug into:
- browser IDEs  
- VS Code  
- LMS-based editors  
- custom learning platforms  

---

## Repository Structure
