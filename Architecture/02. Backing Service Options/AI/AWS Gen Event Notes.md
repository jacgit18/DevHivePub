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


#todo/High/Dev 
- [ ] revisit and prompt about other things [ChatGPT - Generative AI Use Cases](https://chatgpt.com/share/680a8f10-f448-800d-bf4d-74d425ffedff)
- [ ] ask about these

Explain component of gen ai application and the flow between them  
  
Explain when you should go through a guard rail and the aws guardrail service and the concept of it in the context of AWS bedrock  
  
Explain hallucinations check  
  
What is fm inference  
  
  
Explain prompt attack injection  
  
  
Explain bedrock agents and the concept of ai agents use action like with api calls, lambdas, step functions etc...  
  
  
Explain ai agent orchestration also agent group  
  
Agent executes lambda which also can contian api call there is also api schema  
  
Agent is basically acts as a controller  
  
You can apply decentralized architecture to ai agents mean your not having an agent handeling to many thing's  
  
You also leverage event sourcing and hook triggers  
  
Multi agent collaboration  
  
How does an agent look like in terms of codebase level and file architecture  
  
  
Are agents aware of each other if so how  
  
Rag is safe in comparison to agents  
  
  
  
What is the purpose and what problem did Jupiter notebook solve and explain it's use case in aws sage maker studio






Absolutely! Here's a **step-by-step guide for experimenting with Generative AI on AWS** — using only **free** or **free-tier** services.





---

## **AWS Generative AI – Free Experimentation Guide**

### **1. Set Up Your Environment**

#### **a. Create an AWS Account (if you haven’t)**

- Sign up at [aws.amazon.com/free](https://aws.amazon.com/free)
    
- Enable billing alerts to avoid unexpected charges
    

#### **b. Use AWS Free Tier Wisely**

- Use only **free-tier eligible** instance types (e.g., `ml.t2.medium`, `ml.t3.medium`)
    
- Monitor usage through the [AWS Billing Console](https://console.aws.amazon.com/billing/home)
    

---

### **2. Primary Free Services to Use**

#### **1. [Amazon SageMaker Studio Lab (100% Free)]**

- URL: [https://studiolab.sagemaker.aws/](https://studiolab.sagemaker.aws/)
    
- What it is: Hosted JupyterLab environment, GPU available
    
- Use Cases:
    
    - Run Hugging Face models
        
    - Build and test LLM apps (e.g., chatbots, summarizers)
        
    - Train small ML models
        
- How to get started:
    
    - Sign up (approval required but quick)
        
    - Create notebooks
        
    - Run code like:
        
        ```python
        from transformers import pipeline
        pipe = pipeline("text-generation", model="gpt2")
        print(pipe("Once upon a time", max_length=30))
        ```
        

---

#### **2. [Amazon Bedrock (Free Trial Tokens Available)]**

- URL: [https://console.aws.amazon.com/bedrock](https://console.aws.amazon.com/bedrock)
    
- What it is: Serverless GenAI service that lets you use models like Claude, Mistral, Llama 2, Amazon Titan
    
- Use Cases:
    
    - Prompt engineering
        
    - Rapid prototyping with no infra setup
        
- Key models:
    
    - Claude (Anthropic)
        
    - Titan (Amazon)
        
    - Mistral
        
    - Llama 2 (Meta)
        
- How to start:
    
    - Go to Bedrock console
        
    - Use “Playground” to run prompts
        
    - Example prompt:
        
        ```
        Write a haiku about cloud computing.
        ```
        

---

#### **3. [AWS CodeWhisperer (Always Free for Individuals)]**

- URL: [https://aws.amazon.com/codewhisperer/](https://aws.amazon.com/codewhisperer/)
    
- What it is: AI pair programming tool like GitHub Copilot
    
- Use Cases:
    
    - Learn Python with GenAI suggestions
        
    - Generate boilerplate code faster
        
- IDE Support:
    
    - VS Code, PyCharm, IntelliJ
        
- How to start:
    
    - Install AWS Toolkit extension
        
    - Log in with AWS Builder ID
        
    - Use suggestions while coding
        

---

#### **4. [Amazon S3 (5 GB Free Storage)]**

- Use it to:
    
    - Store datasets
        
    - Save model weights
        
    - Share files with notebooks
        
- How to use:
    
    - Create an S3 bucket in console
        
    - Upload datasets (e.g., CSV, JSON)
        
    - Access via Boto3 in Studio Lab or SageMaker
        

---

#### **5. [SageMaker Studio – Free Tier (Limited Time)]**

- Free for first **2 months**:
    
    - 250 hours/month of `ml.t2.medium` or `ml.t3.medium`
        
- Use Cases:
    
    - Run prebuilt notebooks
        
    - Test ML pipelines
        
- Access via SageMaker > Studio > Quick Start
    

---

### **3. Recommended Free Use Projects**

|Project|Tools|Notes|
|---|---|---|
|Prompt engineering playground|Bedrock|Uses free tokens|
|Simple LLM chatbot|Studio Lab + Hugging Face|GPU available|
|Code generator using Claude|Bedrock + Titan|No infra setup|
|Text summarizer from PDFs|Studio Lab + PyMuPDF + Transformers|Free compute|
|Text-to-image with Stable Diffusion|Studio Lab GPU|Try `diffusers` lib|
|Dataset cleaning + prep|S3 + Studio Lab|Free tier storage|
|Auto-code generation|CodeWhisperer|Always free|

---

### **4. Cost-Safe Practices**

- **Shut down resources**: Stop SageMaker instances after use
    
- **Monitor billing**: Set budget alerts
    
- **Stick to free-tier services**: Don't launch EC2 or use high-tier GPU unless absolutely necessary
    
- **Use Studio Lab for heavy GPU work**: It’s not billed through AWS proper
    

---

### Want a printable version or Notion doc of this guide? Or a starter project idea using one of these tools?