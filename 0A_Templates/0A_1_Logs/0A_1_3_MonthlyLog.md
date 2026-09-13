---
created:
  - "{{date}} {{time}}"
tags:
  - Log/MonthlyLog
start: 2026-03-01
end: 2026-03-31
---
# 📆 Month {{date: MM/YYYY}}

---

# 🌌 Overview

## 📊 Monthly Metrics

```dataview
TABLE 
count(rows) as "Days Logged",
avg(Pomodoro) as "Avg 🍅",
avg(Motivation) as "Avg 🔥",
avg(Focus) as "Avg 🎯",
sum(Workout) as "Total 💪"
FROM "06.Daily"
WHERE date(substring(file.name, 0, 4) + "-" + substring(file.name, 4, 2) + "-" + substring(file.name, 6, 2)) >= date(this.start)
AND date(substring(file.name, 0, 4) + "-" + substring(file.name, 4, 2) + "-" + substring(file.name, 6, 2)) <= date(this.end)
```

---

# 🔃 Reflection (short + honest)

- What actually mattered this month?
    
- Did I move forward or just stay busy?
    

---

# 📈 Performance

### 🔷 Daily Tasks Completion Rate

- (estimate or %)
    

### 💯 Rating (0–10)

Happiness::  
Productivity::  
Relationships::  
Focus::

## 👉 Add ONE sentence why:

---

# 📜 Events

## **Biggest Personal Milestone**

## **Biggest Career Milestone**

---

# 🚀 Projects (Portfolio Review)

## 🔥 Active Projects

```dataview
TABLE 
priority,
status,
file.mtime as "Last Update",
file.link as "Project"
FROM "01.Projects"
WHERE contains(file.name, "TRACKING") 
AND contains(status, "active")
SORT priority DESC
```

---

## ⚠️ Stale / Ignored Projects

```dataview
TABLE 
file.link as "Project",
file.mtime as "Last Update"
FROM "01.Projects"
WHERE contains(file.name, "TRACKING") 
AND file.mtime < date(today) - dur(14 days)
```

---

## 🧠 Project Decisions (CRITICAL)

### 🚀 Double Down (invest more time)

### ⏸ Pause / Reduce

### ❌ Kill (remove completely)

---

# 🏢 Career

- What improved?
    
- What is missing?
    
- What is next level?
    

---

# 🧠 Knowledge & Learning

## 📚 What did I learn?

## 🧩 What skills improved?

## ⚠️ What should I learn next?

---

# 📅 Future Plan (Next Month Strategy)

## 🎯 Top 3 Priorities

## 📦 Key Deliverables

## 🧠 Learning Focus

---

# ⚖️ Life Balance

- 💻 Work:
    
- 🧠 Learning:
    
- 💪 Health:
    
- 😌 Mental state:
    

---

# ✅ Action (Execution Bridge)

> _**Be specific, not vague**_

-  Update Tasks lists
    
-  Clean inactive projects
    
-  Define next actions for top 3 projects
    

---

# 📚 To Read

---

# 💾 Information to retain from daily logs

---

# 🔄 System Improvement

- What worked well?
    
- What should change next month?