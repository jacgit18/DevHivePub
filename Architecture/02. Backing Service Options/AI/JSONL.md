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
**JSONL** (JSON Lines) is a format for storing structured data where each line is a separate JSON object. It is commonly used for processing large datasets efficiently, as each line can be read and processed independently.

### **Example JSONL File:**

```
{"name": "Alice", "age": 25, "city": "New York"}
{"name": "Bob", "age": 30, "city": "San Francisco"}
{"name": "Charlie", "age": 22, "city": "Chicago"}
```

Each line is a valid JSON object, making it easy to work with in streaming or line-by-line processing scenarios.

### **Key Features of JSONL:**

- Each line is a **separate JSON object** (not a list).
- No need for commas between entries like in standard JSON arrays.
- Easy to **append** new data without modifying the existing structure.
- Efficient for **processing large files** without loading everything into memory at once.

### **Use Cases:**

- Machine learning datasets (e.g., training data for NLP models).
- Logging and analytics.
- Streaming APIs.

### **Reading JSONL in Python:**

```python
import json

with open("data.jsonl", "r") as file:
    for line in file:
        data = json.loads(line)
        print(data)
```

#todo/Med/Dev 
- [ ] [10 Must-Know Python Libraries for LLMs in 2025 - MachineLearningMastery.com](https://machinelearningmastery.com/10-must-know-python-libraries-for-llms-in-2025/)