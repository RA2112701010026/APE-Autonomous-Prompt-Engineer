# APE-Autonomous-Prompt-Engineer
APE is a multi-agent cognitive architecture designed to mathematically maximize the fidelity of prompts for Large Language Models (LLMs). It automates the "Trial-and-Error" process of prompt engineering by using a Critic-Refiner-Judge feedback loop, bridging the gap between casual user intent and expert-level model performance.

Research Context: This system was developed as a Final Year M.Tech Major Project, focusing on Iterative Prompt Optimization using Agentic AI on constrained edge hardware (NVIDIA T4).

🧠 System Architecture
The core of APE is a State Machine built with LangGraph. It replaces static prompt templates with a dynamic feedback loop:

Code snippet

graph TD
    User[User Input] --> Analyst[Agent 1: The Analyst]
    Analyst -->|Critique JSON| Architect[Agent 2: The Architect]
    Architect -->|Refined Prompt| Judge[Agent 3: The Judge]
    
    Judge -->|Score < 8| Architect
    Judge -->|Score > 8| Output[Final Optimized Prompt]
    
    Output --> Llama[Llama-3 Response Generation]
The Three Agents
🕵️ The Analyst (Critic): Scans user input for semantic ambiguity, missing context, and tone mismatch. Outputs a structured JSON critique.

🏗️ The Architect (Refiner): Reconstructs the prompt using the CO-STAR Framework (Context, Objective, Style, Tone, Audience, Response). It applies Python/PEP-8 standards for code and professional standards for text.

⚖️ The Judge (Guardrail): Evaluates the refined prompt against a rigorous rubric (Clarity, Specificity, Robustness). It assigns a score (0-10) and forces a retry if the quality is low.

📊 Research Validation ("The Twin-Test")
This project moves beyond simple application logic by implementing a statistical benchmarking pipeline.

Methodology: A "Twin-Test" comparison of 50 raw user prompts vs. APE-optimized prompts.

Metrics:

Hallucination Rate: Reduction in vague/wrong answers.

Token Efficiency: Improvement in concise, accurate outputs.

Statistical Significance: Validated using the Wilcoxon Signed-Rank Test (p < 0.05).

🛠️ Installation & Setup
Prerequisites
Python 3.10+

GPU with at least 12GB VRAM (NVIDIA T4 recommended for Colab/Kaggle)

HuggingFace Access Token (for Llama-3)

1. Clone the Repository
Bash

git clone https://github.com/RA2112701010026/APE-Autonomous-Prompt-Engineer.git
cd APE-Autonomous-Prompt-Engineer
2. Install Dependencies
Bash

pip install -r requirements.txt
3. Set Up Environment
You need to authenticate with HuggingFace to download Llama-3.

Python

from huggingface_hub import login
login(token="YOUR_HUGGINGFACE_WRITE_TOKEN")
🚀 Usage
Running the Web UI (Gradio)
To launch the interactive dashboard where you can see the "Before vs. After" results:

Bash

python app.py
This will generate a public link (e.g., https://1234.gradio.live) that you can share or open on mobile.

Dashboard Features
Twin-View: Side-by-side comparison of the "Raw Llama-3 Response" and the "APE Optimized Response".

Transparency: View the internal "Analyst Critique" and "Judge Score" to understand why the prompt was changed.


🔮 Future Scope
RAG Integration: Enabling the Architect to fetch "Gold Standard" prompt examples from a Vector Database (FAISS).

Multi-Modal Support: Optimizing prompts for Image Generation models (Stable Diffusion).

Security Guardrails: Detecting and neutralizing "Jailbreak" attempts (SQL Injection, DAN mode).

📜 License
This project is open-source and available under the MIT License.

👤 Author
UNDEKOTI ROWAN RONALD M.Tech, Computer Science-Artificial Intelligence 
