# Active Interview Service
You will be using the AIS project as a starting point for your semester project. This is a legacy code project meaning that the application is still useable, there is little documentation, and you can't reach out to the project team to ask questions. 

## Resources
Below are a couple of helpful resources to get you started:
1. Code Repo: https://github.com/UCCS-SP25-CS4300-CS5300-1/Group-7-Spring-2025
1. Video: youtube.com/watch?v=RcscVk9oHtw&feature=youtu.be

## Requirements
You will implement the user stories and acceptance criteria below. Some of the features might already be implemented. In addition you will follow these requirements:
1. You are REQUIRED to use Claude and Claude Code with an [agents.md](https://agents.md) file for all code implementations. 
1. You will store your code in https://github.com/UCCS-CS4300-5300/Fall-25-CS-5300 
Note: DevEdu might not be the best environment for this activity so please plan accordingly. 


## AIS Extension User Stories & Acceptance Criteria

## 1. OAuth sign-in
**User Story:**  
As a **candidate**, I want to **sign in with Google**, so **I avoid password management**.

**Scenario:**  
```gherkin
Given Google OAuth is configured
When I click "Continue with Google" and approve
Then I am logged in
And my profile shows Google as the auth provider
```

---

## 2. Role-based access
**User Story:**  
As an **admin**, I want **RBAC (admin/interviewer/candidate)**, so **permissions are enforced**.

**Scenario:**  
```gherkin
Given roles "admin","interviewer","candidate" exist
And I am logged in as candidate
When I request /admin/users
Then I receive HTTP 403
And when I am logged in as admin
Then I can view /admin/users
```

---

## 3. Interview templates
**User Story:**  
As an **interviewer**, I want to **create reusable interview templates with sections and weights**, so **scoring is consistent**.

**Scenario:**  
```gherkin
Given I am an interviewer
When I create a template with sections "Algorithms(40)", "System Design(60)"
Then the template is saved
And can be used to start a new interview
```

---

## 4. Question bank tagging
**User Story:**  
As an **interviewer**, I want to **tag questions (e.g., #python #sql #behavioral)**, so **I can auto-assemble interviews**.

**Scenario:**  
```gherkin
Given a question bank with tags
When I generate an interview from tags "#python" and "#behavioral"
Then at least 5 tagged questions are included
And untagged questions are excluded
```

---

## 5. Resume parsing
**User Story:**  
As a **candidate**, I want **automatic resume parsing (skills, experience, education)**, so **AIS can tailor questions**.

**Scenario:**  
```gherkin
Given I upload a PDF resume
When parsing completes
Then my profile shows extracted skills and experience entries
```

---

## 6. Job-listing ingestion
**User Story:**  
As a **candidate**, I want to **paste a job description and get extracted requirements**, so **the interview matches the role**.

**Scenario:**  
```gherkin
Given a job description input
When I click "Analyze"
Then I see a list of required skills and seniority level
And a recommended interview template
```

---

## 7. Latency budget
**User Story:**  
As a **candidate**, I want **prompt responses (<2s median)** during interviews, so **the experience feels natural**.

**Scenario:**  
```gherkin
Given an audio Q&A session
When I ask 10 questions
Then 90% of responses return in under 2 seconds (logged)
```

---

## 8. Scoring transparency
**User Story:**  
As a **candidate**, I want to **see how my score was computed**, so **I can learn and improve**.

**Scenario:**  
```gherkin
Given I completed an interview
When I open my results
Then I see section scores with weights and rationales
And a final weighted score
```

---

## 9. Bias guardrails
**User Story:**  
As an **admin**, I want **bias-term detection in feedback**, so **reports avoid discriminatory language**.

**Scenario:**  
```gherkin
Given an interviewer feedback draft contains flagged terms
When I attempt to save
Then I am shown warnings and suggested neutral phrasing
And I can revise and save clean feedback
```

---

## 10. Offline/spotty network support
**User Story:**  
As a **candidate on flaky Wi-Fi**, I want **transient disconnect handling and autosave**, so **I don’t lose progress**.

**Scenario:**  
```gherkin
Given I am mid-interview
When my connection drops for 10 seconds
Then my last answer is cached locally
And the session resumes automatically when reconnected
```

---

## 11. Rate limiting & abuse controls
**User Story:**  
As an **admin**, I want **per-IP and per-user rate limits**, so **costs and abuse are contained**.

**Scenario:**  
```gherkin
Given default rate limit 60 requests/min
When a user exceeds the limit
Then the API returns 429 with a Retry-After header
And logs the event
```

---

## 12. GDPR/CCPA data export & delete
**User Story:**  
As a **candidate**, I want to **export or delete my data**, so **I control my privacy**.

**Scenario:**  
```gherkin
Given I request "Export my data"
Then I receive a downloadable archive within the portal
And when I request "Delete my data"
Then my interviews and PII are removed and anonymized references remain
```

---

## 13. Audit logging
**User Story:**  
As a **compliance officer**, I want **immutable audit logs (who/what/when/where)**, so **we can investigate incidents**.

**Scenario:**  
```gherkin
Given I am an admin
When I view audit logs for a user
Then I see timestamped entries for login, data access, and admin actions
```

---

## 14. Observability dashboard
**User Story:**  
As an **SRE**, I want **metrics (RPS, latency, error rate, provider cost)**, so **I can spot regressions**.

**Scenario:**  
```gherkin
Given the system is running
When I open /admin/observability
Then I see charts for p50/p95 latency, error rates, and provider spend by day
```

---

## 15. Cost caps & API key rotation
**User Story:**  
As an **admin**, I want **monthly spend caps and auto key-rotation**, so **we don’t blow the budget or keep stale keys**.

**Scenario:**  
```gherkin
Given a monthly spend cap is $200
When projected spend exceeds the cap
Then interviews switch to a fallback LLM/TTS tier
And a rotation job rotates provider keys
```

---

## 16. Calendar & invitation flow
**User Story:**  
As an **interviewer**, I want to **invite candidates and add to Google Calendar**, so **scheduling is painless**.

**Scenario:**  
```gherkin
Given I create an interview
When I click "Invite"
Then an email is sent with a join link
And I can add the event to Google Calendar from the confirmation page
```

---

## 17. Exportable report
**User Story:**  
As a **candidate**, I want an **exportable PDF report (score, strengths, practice plan)**, so **I can share with mentors**.

**Scenario:**  
```gherkin
Given I completed an interview
When I click "Download Report"
Then I receive a PDF with my scores, section feedback, and recommended exercises
```
