---
created:
  - "{{date}} {{time}}"
aliases:
  - "Games: {{title}}"
tags:
  - CodeReview
---
### **Code Review Template**  
**PR Title/Link**: [Insert PR Title or Link]  
**Author**: [Name]  
**Reviewer**: [Name/Team]  

---

#### **1. Code Readability**  
- [ ] Are variable/function/class names **clear and descriptive**?  
- [ ] Is the code logically organized (e.g., separation of concerns, modularity)?  
- [ ] Is there redundant or duplicated code that can be simplified?  
- [ ] Are comments present where necessary (e.g., explaining complex logic)?  

#### **2. Code Correctness**  
- [ ] Does the code **solve the problem** it intends to solve?  
- [ ] Are edge cases handled (e.g., empty inputs, error states)?  
- [ ] Are there potential bugs (e.g., off-by-one errors, race conditions)?  
- [ ] Are third-party/library functions used correctly?  

#### **3. Performance**  
- [ ] Are there inefficient operations (e.g., nested loops, unnecessary computations)?  
- [ ] Is memory managed properly (e.g., leaks, excessive allocations)?  
- [ ] Are database/API calls optimized (e.g., batching, caching)?  

#### **4. Security**  
- [ ] Is user input validated/sanitized?  
- [ ] Are there vulnerabilities (e.g., SQL injection, XSS, hardcoded secrets)?  
- [ ] Are permissions/access controls enforced?  

#### **5. Maintainability**  
- [ ] Is the code easy to extend/modify in the future?  
- [ ] Are configuration values hardcoded, or are they parameterized?  
- [ ] Are dependencies (libraries, services) up-to-date and secure?  

#### **6. Testing**  
- [ ] Are unit/integration tests included?  
- [ ] Do tests cover critical paths and edge cases?  
- [ ] Are mocks/stubs used appropriately?  

#### **7. Documentation**  
- [ ] Are public APIs/endpoints documented?  
- [ ] Is the README updated (if applicable)?  
- [ ] Are there outdated comments or TODOs?  

#### **8. Adherence to Standards**  
- [ ] Does the code follow **team/company conventions** (e.g., linting, formatting)?  
- [ ] Are design patterns used appropriately?  

#### **9. General Comments**  
- Suggestions for improvement:  
  - [Example: "Extract this logic into a helper function to improve reusability."]  
- Positive feedback:  
  - [Example: "Great error handling here!"]  
- Questions for the author:  
  - [Example: "Why was this approach chosen over X?"]  

---

### **Review Summary**  
- **Approved**: ✅ | **Needs Changes**: ⚠️ (Specify blocking issues)  
- **Next Steps**: [E.g., "Address points 3 and 5, then merge."]  

---

### **Best Practices for Reviewers**  
- Focus on **code, not the author**.  
- Be specific (e.g., "Line 42: Consider caching this result").  
- Balance criticism with positive feedback.  
- Ask questions instead of making assumptions.  

Feel free to tweak this template based on your project’s needs! 🚀