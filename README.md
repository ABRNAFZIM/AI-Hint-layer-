
#  **AI Scaffolding Hint Layer for Coding Education**  
*A Responsible‑AI Architecture for Adaptive, Human‑Centred Coding Support*

---

## **Overview**

This repository documents the design and early prototype work for an AI‑powered **Hint Layer** that provides structured, progressive scaffolding for students learning to code. Unlike traditional AI tutors that give direct answers, this system is engineered to promote:

- **Critical thinking**  
- **Academic integrity**  
- **Mastery‑based learning**  
- **Learner wellbeing**  
- **Human‑in‑the‑loop support**

The Hint Layer integrates:

- Static analysis of student code  
- Error classification  
- Context‑aware prompt construction  
- Multi‑level progressive hinting  
- **Frustration detection**  
- **Mentor escalation before a student gives up**  
- Guardrails to prevent over‑helping  
- Pedagogically grounded scaffolding (ZPD, mastery learning)

This work represents an original contribution to AI‑driven education technology and demonstrates a responsible, human‑centred approach to AI in learning environments.

---

## **High‑Level Architecture**

```
+-------------------+        +------------------------+        +-------------------+
|   Student Code    | -----> |   Hint Layer API       | -----> |   LLM (GPT, etc.) |
|   (Editor Input)  |        |   (Middleware)         |        |   via API         |
+-------------------+        +------------------------+        +-------------------+
        |                           |                               |
        |                           |                               |
        v                           v                               v
+-------------------+        +------------------------+        +-------------------+
|   Error Detector  |        |   Prompt Builder       |        |   AI Response     |
| (Syntax/Logic)    |        | (Context + Task + FD) |        |   (Hint Text)     |
+-------------------+        +------------------------+        +-------------------+
        |                           ^
        |                           |
        v                           |
+-------------------+               |
| Frustration       | --------------+
| Detection Layer   |
| (Signals + Score) |
+-------------------+
        |
        v
+-------------------+         +---------------------------+
| Hint Formatter    | -----> | Mentor Escalation Engine  |
| (Adaptive Hints)  |         | (Risk Threshold Check)    |
+-------------------+         +---------------------------+
        |                               |
        v                               v
+-------------------+         +---------------------------+
| Hint Display      |         | Mentor Notification       |
| (Editor Panel)    |         | (Dashboard / Email / App) |
+-------------------+         +---------------------------+
```

---

##  **Core Components**

### **1. Error Detector**
Performs lightweight static analysis to identify:

- Syntax errors  
- Logic errors  
- Conceptual misunderstandings  

This ensures the LLM receives accurate context.

---

### **2. Frustration Detection Layer**
A responsible‑AI component that monitors behavioural indicators such as:

- Repeated identical errors  
- Excessive hint requests  
- Long periods without progress  
- Oscillating code patterns  
- Code deletion cycles  
- Long pauses  
- (Optional) emotional language in comments  

It outputs:

- `frustration_score` (0–1)  
- `frustration_state` (low / medium / high)  
- `risk_of_giving_up` (boolean)

This enables adaptive scaffolding and early intervention.

---

### **3. Prompt Builder**
Constructs structured prompts for the LLM using:

- Task description  
- Student code  
- Error type  
- Frustration state  
- Scaffolding level  
- Academic integrity guardrails  

**Example prompt:**

```
The student is solving: Reverse a string.
Their code is:
<student_code>

Error detected:
IndexError: string index out of range.

Frustration score: HIGH
Signals: repeated errors, long pause, multiple hint requests.

Provide a supportive, non-judgmental hint.
Do NOT give the full solution.
Use Level 1 or Level 2 hinting only.
```

---

### **4. Progressive Hinting Engine**

Hints are delivered in increasing levels of specificity:

#### **Level 1 — Gentle Nudge**
Encourages reflection  
> “Have you checked whether your loop runs the expected number of times?”

#### **Level 2 — Conceptual Guidance**
Points to the area of the issue  
> “Look closely at how you’re handling string indices.”

#### **Level 3 — Specific Technical Hint**
Identifies the exact bug  
> “Your loop condition goes one step too far.”

#### **Level 4 — Worked Example (Non‑Solution)**
Shows a similar solved case  
> “Here’s how another student reversed a list…”

The **Frustration Detection Layer** determines which levels are allowed.

---

### **5. Mentor Escalation Engine**
If frustration becomes high, the system triggers a **human‑in‑the‑loop intervention**.

**Escalation triggers include:**

- Frustration score > 0.85  
- More than 4 repeated errors  
- More than 5 hint requests  
- No progress for 5+ minutes  

**Mentor Notification Example:**

```
Student Support Needed – High Frustration Detected
Student: ID #4821
Task: Reverse a string
Signals: 5 repeated errors, 7 hint requests, no progress for 6 minutes
Frustration Score: 0.92
```

This ensures the system supports — not replaces — human educators.

---

##  **Example Code Snippets**

### **Frustration Score Calculation**
```js
function computeFrustrationScore(events) {
  let score = 0;

  if (events.repeatedErrors > 2) score += 0.3;
  if (events.timeStuck > 120000) score += 0.3;
  if (events.hintRequests > 2) score += 0.2;
  if (events.codeDeletes > 1) score += 0.2;

  return Math.min(score, 1);
}
```

---

### **Adaptive Hint Level Selection**
```js
function getHintLevel(frustrationScore) {
  if (frustrationScore > 0.7) return 1;
  if (frustrationScore > 0.4) return 2;
  if (frustrationScore > 0.2) return 3;
  return 4;
}
```

---

### **Mentor Escalation Logic**
```js
function shouldEscalate(frustrationScore, events) {
  return (
    frustrationScore > 0.85 ||
    events.repeatedErrors > 4 ||
    events.hintRequests > 5 ||
    events.timeStuck > 300000
  );
}
```

---

## **Responsible AI Principles**

This architecture is designed to:

- Support learning without giving away answers  
- Prevent cognitive overload  
- Detect frustration early  
- Trigger human intervention when needed  
- Maintain student dignity and psychological safety  
- Provide adaptive, personalised scaffolding  

This aligns with modern responsible‑AI frameworks in education.

---

##  **Future Roadmap**

- Emotion detection from keystroke dynamics  
- Personalised learning profiles  
- Mentor analytics dashboard  
- Multilingual hinting  
- Curriculum‑aware hinting models  

---

## **License**
This project is licensed under the **MIT License**.
