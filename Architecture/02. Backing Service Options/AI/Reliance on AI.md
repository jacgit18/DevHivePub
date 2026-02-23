---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Step-by-Step Process for Coding Without Over-Reliance on AI

  

This process emphasizes **understanding, reading, and writing code manually** before leveraging AI for assistance. The goal is to build foundational skills while using AI as a **tool for efficiency**, not a crutch.

  

---

  

### **Phase 1: Understand the Problem**

1. **Define the Goal Clearly**  

   - Write down the feature/bug-fix in plain English (or your language).  

   - Example: *"Add a button that fetches user data from an API and displays it in a table."*

  

2. **Break Down the Problem**  

   - Split into smaller sub-tasks:  

     - Create a button in the UI.  

     - Call an API on click.  

     - Parse the response.  

     - Display data in a table.  

  

3. **Research (Without AI First)**  

   - Check existing code/documentation for similar patterns.  

   - Search official docs (MDN, React, Python docs, etc.).  

   - Only use AI if stuck after 10-15 mins of manual research.

  

---

  

### **Phase 2: Read and Analyze Existing Code**

1. **Locate Relevant Code Files**  

   - Use `grep`, IDE search, or file structure to find where changes are needed.  

   - Example: If adding a button, find the related UI component.

  

2. **Trace Data/Control Flow**  

   - For APIs: Follow the request from frontend → backend → database.  

   - For UI: Check parent/child component relationships.  

   - **Draw a flowchart** if the logic is complex.

  

3. **Understand Dependencies**  

   - Note libraries/frameworks used (e.g., Axios for HTTP, Redux for state).  

   - Check for side effects (e.g., does the API call trigger other actions?).

  

---

  

### **Phase 3: Write Code Manually (First Draft)**

1. **Pseudocode**  

   - Write logic in plain language:  

     ```python

     # When button clicked:

     #   1. Show loading spinner

     #   2. Call /api/users

     #   3. On success, update table; on error, show message

     ```

  

2. **Implement Step-by-Step**  

   - Start with the simplest working version (e.g., a hardcoded button).  

   - Gradually add functionality (e.g., mock API call → real API call).  

  

3. **Refer to Past Code**  

   - Reuse patterns from existing code (e.g., how other buttons handle clicks).  

  

4. **Avoid AI Here**  

   - Try to write at least a rough draft without AI assistance.

  

---

  

### **Phase 4: Debug and Test Manually**

1. **Manual Testing**  

   - Run the code and test edge cases:  

     - Empty responses.  

     - Network errors.  

     - Invalid user inputs.  

  

2. **Debugging**  

   - Use `console.log`/debugger to inspect variables.  

   - Check error messages and stack traces.  

  

3. **Fix Errors Yourself First**  

   - Spend 10-15 mins troubleshooting before asking AI.  

  

---

  

### **Phase 5: Leverage AI Strategically**

1. **Use AI for Specific Gaps**  

   - Example prompts:  

     - *"How do I handle a 403 error in Axios?"*  

     - *"Why is my React state not updating?"*  

   - **Avoid:** "Write a button that fetches users."  

  

2. **Compare AI Suggestions with Your Code**  

   - Paste your code and ask: *"How can I improve this?"*  

   - Understand every line AI suggests—don’t blindly accept.  

  

3. **Ask for Explanations**  

   - *"Why did you use `useCallback` here?"*  

   - *"What’s the time complexity of this approach?"*  

  

---

  

### **Phase 6: Refactor and Document**

1. **Optimize Your Code**  

   - Remove duplication.  

   - Improve readability (rename variables, add comments).  

  

2. **Write Tests**  

   - Manual → Automated (unit/integration tests).  

   - Example: Mock API calls and test UI updates.  

  

3. **Document Learnings**  

   - Add comments explaining tricky logic.  

   - Update project docs if APIs/behavior change.  

  

---

  

### **Phase 7: Review and Repeat**

1. **Code Review (Even Solo)**  

   - Revisit your code after a break—would it make sense to a teammate?  

  

2. **Track Knowledge Gaps**  

   - Note topics to study (e.g., "Learn React hooks deeper").  

  

3. **Reduce AI Reliance Gradually**  

   - For similar tasks, try writing 100% manually next time.  

  

---

  

### Key Principles:

- **AI is a Assistant, Not a Replacement**  

  Use it like a senior dev reviewing your code—not writing it for you.  

- **Understand Before Implementing**  

  Never paste AI code you don’t fully grasp.  

- **Build Muscle Memory**  

  Typing code manually reinforces learning better than copy-pasting.  

  

By following this, you’ll grow independent while still benefiting from AI’s speed.