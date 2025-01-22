# 🌟 **Advanced AI Code Agent: Harnessing SmolAgents & Hugging Face** 🌟  

Welcome to the **AI Code Agent** repository! This project showcases an intelligent code execution and retrieval agent powered by Hugging Face's API and SmolAgents. It integrates **state-of-the-art tools** for automation, exploration, and advanced model interaction.  

---

## 🔍 **Overview**  

The AI Code Agent can:  
- Perform advanced **code execution** and mathematical calculations.  
- Query real-time information using **DuckDuckGo Search**.  
- Retrieve **top downloaded models** from Hugging Face for specific tasks.  
- Leverage authorized libraries for broader computations and visualizations.  

---

## 🚀 **Features**  

### 🌐 **Hugging Face API Integration**  
- Automate interactions with Hugging Face Hub models without manual API calls.  
- Retrieve the **most downloaded model** for tasks like text classification, text-to-image generation, and more.  

### 🛠️ **Custom Tooling**  
- Includes a **DuckDuckGo Search Tool** for real-time data.  
- Custom-built **HfDownloadsTool** to fetch the most downloaded model based on task-specific queries.  

### 📡 **Dynamic Capabilities**  
- Enables interaction with additional libraries such as `math`, `pandas`, `requests`, `bs4`, `matplotlib`, and `yfinance`.  
- Extensible architecture to add more tools or modify workflows.  

---

## 💡 **Code Flow**  

### **1. Environment Setup**  
The Hugging Face API key is configured globally via:  
```python
os.environ["HF_API_KEY"] = "***"
```

### **2. Model Initialization**  
A `CodeAgent` is initialized with the Hugging Face model:  
```python
from smolagents import CodeAgent, HfApiModel

model = HfApiModel()
agent = CodeAgent(tools=[], model=model)
```

### **3. Real-Time Search**  
By integrating the **DuckDuckGoSearchTool**, the agent queries real-time events:  
```python
from smolagents import DuckDuckGoSearchTool

agent = CodeAgent(tools=[DuckDuckGoSearchTool()], model=model)
agent.run("what is the result of the latest Cricket test series between India and Australia?")
```

### **4. Hugging Face Tool for Top Downloads**  
The custom `HfDownloadsTool` identifies the most downloaded models for a specific task:  
```python
class HfDownloadsTool(Tool):
    def forward(self, task: str):
        from huggingface_hub import list_models
        model = next(iter(list_models(filter=task, sort="downloads", direction=-1)))
        return model.id
```

### **5. Complex Queries**  
Authorized imports allow advanced queries with broader functionality:  
```python
agent = CodeAgent(
    tools=[model_downloads_tool],
    model=HfApiModel(),
    additional_authorized_imports=['math', 'pandas', 'requests', 'bs4', 'matplotlib', 'yfinance']
)

response = agent.run("What is the most downloaded text-classification model?")
print(response)
```

---

## 🧠 **Key Tools in Action**  

### **HfDownloadsTool**  
- **Purpose**: Fetches the most downloaded model for a specific task.  
- **Inputs**:  
  - Task category (e.g., `text-classification`, `depth-estimation`).  
- **Output**:  
  - Model checkpoint name.  

### **DuckDuckGoSearchTool**  
- **Purpose**: Queries real-time data using the DuckDuckGo API.  
- **Applications**: Event lookups, trending updates, and general-purpose searches.  

---

## 📦 **Installation**  

1. **Clone the Repository**:  
   ```bash
   git clone https://github.com/your-username/ai-code-agent.git
   cd ai-code-agent
   ```  

2. **Set Up the Environment**:  
   Create and activate a virtual environment:  
   ```bash
   python -m venv myenv
   source myenv/bin/activate  # For Linux/macOS
   myenv\Scripts\activate     # For Windows
   ```  

3. **Install Dependencies**:  
   ```bash
   pip install -r requirements.txt
   ```  

4. **Add Hugging Face API Key**:  
   Set the key as an environment variable:  
   ```bash
   export HF_API_KEY=your_api_key_here  # Linux/macOS
   set HF_API_KEY=your_api_key_here     # Windows
   ```  

---

## 📊 **Examples in Action**  

1. **Simple Query**:  
   ```python
   response = agent.run("what is 24*7?")
   print(response)
   ```  

2. **Real-Time Cricket Updates**:  
   ```python
   response = agent.run("What is the result of the latest Cricket test series between India and Australia?")
   print(response)
   ```  

3. **Top Hugging Face Models**:  
   ```python
   response = agent.run("What is the most downloaded text-classification model?")
   print(response)
   ```  

---

## 🔗 **Extensions and Usage**  

- **Integrate More Tools**: Add custom tools to enhance functionality.  
- **Expand APIs**: Combine Hugging Face with other APIs for richer datasets.  
- **Broaden Scope**: Explore text-to-image generation, depth estimation, or domain-specific models.  

---

## 🤝 **Contributing**  

Contributions are welcome! If you encounter issues, feel free to open an issue or submit a pull request.  

---

## 📜 **License**  

This project is licensed under the MIT License.  

---
