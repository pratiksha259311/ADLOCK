# ADLOCK
ADLOCK: Holistic age &amp; maturity verification system ensuring safe, ethical, human-centric access.
# ADLOCK – Age & Maturity Verification System

**ADLOCK ensures users are both adults and emotionally mature before granting unrestricted access.**  
Holistic verification with **AD Badge** (age) + **INTELOCK** (behavioral maturity).

---

## 🚀 Key Features
- AD Badge → verifies chronological age (18+) via email.  
- INTELOCK → evaluates emotional & behavioral maturity (score 0–100).  
- Sensitivity → high sensitivity triggers **silent safety mode**.  
- Access Levels → UNRESTRICTED or RESTRICTED, silently enforced.  

---

## 🧩 Workflow Overview

**Step 0: Registration**  
User signs up → store in MySQL → user_id generated  

**Step 1: AD Badge Verification (Node.js)**  
```javascript
// Example snippet 
send_email_verifica
# Example snippet
responses = collect_responses(user_id)
maturity_score = run_ai_model(responses)
sensitivity = detect_sensitivity(responses)
if(badge_verified && maturity_score >= 75){
    access_level = "UNRESTRICTED";
    if(sensitivity == HIGH) safety_mode = true;
}else{
    access_level = "RESTRICTED";
    if(sensitivity == HIGH) safety_mode = true;
}
Access granted/restricted based on decision

Safety mode activated silently if required
tion_link(email)
Optional Monitoring

Track real-time interactions

Adaptive UI & content based on sensitivity and maturity
👤 Example Scenarios
User	Age	Maturity	Sensitivity	Access	Notes
Urwashi123	20	88	HIGH	UNRESTRICTED	Full adult & mature access, safety mode
Rohan456	23	45	NORMAL	RESTRICTED	Age verified, low maturity
Tanya789	16	90	HIGH	RESTRICTED	Underage, even high maturity restricted
Aarav999	25	95	HIGH	UNRESTRICTED	Adult & mature, safety mode activated
version: '3.9'
services:
  mysql:
    image: mysql:8.0
    ports: ["3306:3306"]
  python_service:
    build: ./python_service
    ports: ["5000:5000"]
  node_service:
    build: ./node_service
    ports: ["4000:4000"]
  java_service:
    build: ./java_service
    ports: ["8080:8080"]
networks:
  adlock_net:
    driver: bridge
volumes:
  mysql_data:
# ADLOCK – Age & Maturity Verification System (Demo Showcase)

> ⚠️ **Note:** Conceptual showcase only.  
> Demonstrates **architecture, workflows, and decision-making**.  
> **Not fully implemented**.

---

## 🧩 Overview

ADLOCK merges **two verification dimensions**:

| Component | Purpose |
|-----------|---------|
| **AD Badge** | Confirms user’s verified chronological age (18+) via email. |
| **INTELOCK** | Evaluates behavioral & emotional maturity using questionnaires and AI. |

**Goal:** Only users who are **adults AND emotionally mature** get **unrestricted access**.

---

## 🔹 Decision Matrix

| Scenario | Age | Maturity | Sensitivity | Badge Verified | Access Level | Safety Mode | Notes |
|----------|-----|----------|-------------|-----------------|--------------|-------------|-------|
| 1 | >=18 | High (>=75) | Normal | ✅ True | ✅ UNRESTRICTED | ⚪ False | Adult, mature, normal sensitivity → full access |
| 2 | >=18 | High (>=75) | High | ✅ True | ✅ UNRESTRICTED | ✅ True | Adult, mature, highly sensitive → full access + safety mode |
| 3 | >=18 | Low (<75) | Normal | ✅ True | ❌ RESTRICTED | ⚪ False | Adult, low maturity → restricted access |
| 4 | >=18 | Low (<75) | High | ✅ True | ❌ RESTRICTED | ✅ True | Adult, low maturity, high sensitivity → restricted + safety mode |
| 5 | <18 | High (>=75) | Normal | ❌ False | ❌ RESTRICTED | ⚪ False | Underage, mature → restricted silently |
| 6 | <18 | High (>=75) | High | ❌ False | ❌ RESTRICTED | ✅ True | Underage, mature, sensitive → restricted + safety mode silently |
| 7 | <18 | Low (<75) | Normal/High | ❌ False | ❌ RESTRICTED | ⚪/✅ | Underage, low maturity → restricted + optional safety mode |

---

## ⚙️ Pseudocode – Decision Engine

```java
if (badge_verified && maturity_score >= 75) {
    access_level = "UNRESTRICTED";
    safety_mode = (sensitivity == "HIGH") ? true : false;
} else {
    access_level = "RESTRICTED";
    safety_mode = (sensitivity == "HIGH") ? true : false;
}
// ✅ Safety mode replaces any “access denied” message




if(age >= 18) badge_verified = true
