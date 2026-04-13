# 🦙 Meta’s LLaMA-3 Models (Cloud & Local Deployment)

This lab demonstrates how to use **Meta's LLaMA-3 models** both in **Cloud Deployment** and **Local Deployment** for building AI-powered applications.

---

# 📌 Overview

Meta’s **LLaMA-3** models are powerful open-weight Large Language Models designed for:

* Chatbots
* Content Generation
* Code Generation
* AI Assistants
* RAG Systems

This notebook demonstrates:

* Cloud Deployment using Groq API
* Model Initialization
* Prompt Engineering
* Custom Use Case Example

---

# 🎯 Objectives

By completing this lab, you will learn:

* How to use LLaMA-3 via cloud API
* How to securely load API keys
* How to generate responses
* How to build AI applications
* Cloud vs Local deployment concepts

---

# ☁️ Cloud Deployment — LLaMA-3

## Step 1 — Install Dependencies

```python
!pip install -q groq
```

---

# 🔐 Step 2 — Load API Key Securely

```python
import os
from google.colab import userdata

os.environ["GROQ_API_KEY"] = userdata.get("GROQ_API_KEY")

if os.getenv("GROQ_API_KEY") is None:
    raise ValueError("❌ GROQ API KEY not found. Add it in Colab Secrets.")

print("✅ API Key Loaded Securely")
```

---

# ⚙️ Step 3 — Initialize Client

```python
from groq import Groq

client = Groq(api_key=os.environ["GROQ_API_KEY"])

print("✅ Groq Client Initialized")
```

---

# 🤖 Step 4 — Generic Response Function

```python
def generate_response(prompt, model="llama-3.1-8b-instant"):
    try:
        response = client.chat.completions.create(
            model=model,
            messages=[{"role": "user", "content": prompt}]
        )
        return response.choices[0].message.content
    
    except Exception as e:
        return f"❌ Error: {str(e)}"
```

---

# 🧪 Step 5 — Test LLaMA-3

```python
prompt = "Explain Large Language Models in simple terms."

print(generate_response(prompt))
```

---

# 🎬 Step 6 — Custom Use Case (Instagram Reel Generator)

```python
def generate_reel_script(topic):
    prompt = f"""
    Create a 30-second Instagram reel script on: {topic}

    Requirements:
    - Break into scenes of 2-3 seconds each
    - Each scene should have:
        Scene number
        Visual description
        Voiceover text
    """

    return generate_response(prompt)
```

---

# 🚀 Step 7 — Generate Output

```python
topic = "Future of AI in Daily Life"

script = generate_reel_script(topic)
print(script)
```

---

# 💾 Step 8 — Save Output

```python
with open("reel_script.txt", "w") as f:
    f.write(script)
```

---

# 🖥️ Local Deployment (Optional)

You can run LLaMA-3 locally using:

* Ollama
* HuggingFace Transformers
* llama.cpp

Example:

```bash
ollama run llama3
```

---

# ☁️ Cloud vs Local Deployment

| Feature    | Cloud       | Local              |
| ---------- | ----------- | ------------------ |
| Setup      | Easy        | Moderate           |
| Cost       | Pay-per-use | Free after setup   |
| Speed      | Very Fast   | Hardware dependent |
| Privacy    | Lower       | High               |
| GPU Needed | No          | Yes (recommended)  |

---

# 🔥 LLaMA-3 Models Available

* llama-3-8B
* llama-3-70B
* llama-3.1-8b-instant
* llama-3.1-70b

---

# 📦 Requirements

```
groq
python
google colab (optional)
```

---

# ▶️ Run Notebook

```bash
jupyter notebook Lab8.ipynb
```

---

# 📈 Use Cases

* Chatbots
* Content generation
* AI assistants
* Coding assistants
* RAG pipelines

---

# 🎓 Learning Outcomes

You will understand:

* LLaMA-3 usage
* Cloud deployment
* Prompt engineering
* AI application building

---

# 📄 License

Educational Use

---

# 👨‍💻 Lab

**Meta’s LLaMA-3 Models (Cloud & Local Deployment)**
