---
created:
  - "{{date}} {{time}}"
tags:
  - Log/WeeklyLog
---
```toc
style: number
```

# 🌌 Overview

```dataview
TABLE WITHOUT ID
	link(file.name) as "Day",
	Feeling AS "✨",
	working-on AS "✏️",
	Motivation AS "🔥",
	Pomodoro AS "🍅",
	Focus AS "🎯",
	Workout AS "💪"
WHERE file.folder = "06.Daily" 
AND file.name >= this.start 
AND file.name <= this.end
SORT file.name DESC
```

---

# 📊 Weekly Metrics (auto insight)

```dataview
TABLE 
avg(Pomodoro) as "Avg 🍅",
avg(Motivation) as "Avg 🔥",
avg(Focus) as "Avg 🎯",
sum(Workout) as "Total 💪"
FROM "06.Daily"
WHERE file.name >= this.start AND file.name <= this.end
```

---

# 🔥 Active Projects (current focus)

```dataview
TABLE 
priority,
next as "Next Action",
file.mtime as "Last Update",
file.link as "Project"
FROM "01.Projects"
WHERE contains(file.name, "TRACKING") 
AND contains(status, "active")
SORT priority DESC, file.mtime DESC
```

---

# ⚠️ Stale Projects (danger zone)

```dataview
TABLE 
file.link as "Project",
file.mtime as "Last Update"
FROM "01.Projects"
WHERE contains(file.name, "TRACKING") 
AND file.mtime < date(today) - dur(7 days)
```

---

# 🧠 Weekly Review

## 🔃 Reflection (short, honest)

- What actually mattered this week?
    
- Did I focus or get distracted?
    

---

## 📜 Events (important only)

---

## 📃 Projects

### ✅ What did I accomplish?

### 😐 Am I satisfied?

- (Yes / No — why?)
    

### ⚠️ What blocked me?

### 🔧 Improvement (specific)

---

# 💰 Decisions (MOST IMPORTANT)

- Stop:
    
- Continue:
    
- Double down:
    

---

# 🧠 Key Learnings (max 3)

---

# 🎯 Next Week Focus (max 3)

---

# 💾 Keep / Drop

### Keep doing:

### Stop doing: