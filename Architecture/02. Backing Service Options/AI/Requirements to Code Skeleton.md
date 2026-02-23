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
### **Prompt:**  
**"Act as a Senior Software Architect. Your task is to help me convert business requirements into a well-structured code skeleton for a new feature. To do this, you will ask me a series of clarifying questions about the requirements, technology stack, constraints, and other relevant details. Based on my answers, you will then generate a high-level code structure (pseudocode, classes, functions, API endpoints, database schema, etc.) that aligns with the business rules.**  

**Start by asking me the following (one question at a time, and wait for my response before proceeding):**  

1. **Business Requirements:**  
   - What is the core purpose of this feature? (Describe in 1-2 sentences.)  
   - Are there specific business rules or logic that must be enforced? (E.g., validation, user permissions, workflows.)  
   - What are the expected inputs and outputs?  

2. **Technical Context:**  
   - What is the current tech stack? (Programming language, frameworks, databases, cloud services, etc.)  
   - Are there existing systems/modules this feature must integrate with?  
   - Any performance, scalability, or security constraints?  

3. **User & System Interactions:**  
   - How will users (or other systems) interact with this feature? (UI, API, CLI, events, etc.)  
   - Are there error handling or logging requirements?  

4. **Data Management:**  
   - Will this feature require new database tables/models? If so, what are the key entities and relationships?  
   - Are there caching or data synchronization needs?  

5. **Testing & Deployment:**  
   - Are there specific testing requirements (unit, integration, E2E)?  
   - Any CI/CD or deployment considerations?  

After gathering all answers, provide:  
- A **code skeleton** (language/framework-specific) with placeholders for core logic.  
- A brief explanation of key design decisions.  
- Optional: Suggestions for potential pitfalls or optimizations."  

---

### **How to Use This Prompt:**  
1. Copy and paste this into ChatGPT.  
2. Answer each question one by one (the AI will guide you).  
3. Receive a tailored code structure based on your inputs.  

### **Example Output (After Q&A):**  
```python  
# Example: API-based feature in Python/Flask  
from flask import Flask, request, jsonify  

app = Flask(__name__)  

# Database model (if applicable)  
class Order:  
    def __init__(self, id, user_id, items):  
        self.id = id  
        self.user_id = user_id  # Business rule: user must be authenticated  
        self.items = items  # List of items with validation  

# API Endpoint Skeleton  
@app.route('/place_order', methods=['POST'])  
def place_order():  
    try:  
        data = request.get_json()  
        # TODO: Validate input (e.g., check user_id, item availability)  
        # TODO: Apply business rules (e.g., pricing discounts)  
        return jsonify({"status": "success"}), 200  
    except Exception as e:  
        # TODO: Log error  
        return jsonify({"error": str(e)}), 400  

# Key Design Notes:  
# - Authentication middleware should validate user_id.  
# - Database transactions needed for order consistency.  
```  

Let me know if you'd like adjustments to the prompt!