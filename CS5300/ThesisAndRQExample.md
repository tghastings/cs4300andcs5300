# Course Project: Evaluating AI Tools in Software Engineering

## 🎯 Thesis & Research Questions (Scoped to Semester)

**Thesis Statement (scoped):**  
AI tools can meaningfully improve developer productivity in a single course project setting by reducing time on repetitive tasks, improving perceived code quality, and supporting defect detection.  

**Research Questions (scoped):**
1. How much time do students save on routine coding tasks when using AI-powered tools compared to manual coding?  
2. How do students perceive the quality and maintainability of AI-assisted code compared to their own code?  
3. How effective are AI tools at helping students detect bugs in their own assignments/projects?  

---

## 🛠️ Evaluation Plan

| Research Question | Evaluation Method (feasible for 16 weeks) | Metrics | Data Sources |
|-------------------|--------------------------------------------|---------|--------------|
| **1. Time saved** | Assign 2–3 small coding labs (e.g., API wrapper, data parser, unit tests). Half of class uses AI tools, half doesn’t. Swap roles later. | Avg. task completion time, # of AI-generated lines | GitHub commit timestamps, IDE plugins, self-reports |
| **2. Code quality & cognitive load** | Students submit code samples (with and without AI). Peer review sessions and short NASA-TLX survey on workload. | Code maintainability index, peer ratings, survey scores | Static analysis tools, peer feedback forms |
| **3. Bug detection** | Give students a buggy codebase as a lab. Compare bug reports found with vs. without AI tool support. | # of true positives, # of false positives, severity of bugs found | Bug reports submitted, instructor “oracle” list of seeded bugs |

---

## 📅 Semester Timeline

- **Weeks 1–2:** Introduction, background on AI in SE, thesis + research question framing.  
- **Weeks 3–6:** Run Lab 1 & 2 (routine coding tasks). Collect time + usage data.  
- **Weeks 7–10:** Run Lab 3 (peer review + surveys on AI vs non-AI code).  
- **Weeks 11–13:** Bug detection lab (seeded bug exercise).  
- **Weeks 14–15:** Data analysis (basic stats, visualizations).  
- **Week 16:** Final report & presentations (tie back to thesis).  

---

## ✅ Why This Fits a Semester

- **Labs are small and focused** → can be done in 1–2 weeks each.  
- **Data collection is lightweight** → reuses existing course assignments.  
- **Analysis is accessible** → students can run basic stats/graphs without needing advanced methods.  
- **Research experience** → ties back to thesis + structured questions, but still practical.  



### Source
@misc{chatgpt_ai_se_course_2025,
  author       = {OpenAI ChatGPT},
  title        = {Conversation with ChatGPT on scoping a one-semester course project on AI in Software Engineering},
  year         = {2025},
  month        = {September},
  day          = {21},
  howpublished = {\url{https://chat.openai.com/}},
  note         = {Accessed: 2025-09-21}
}
