# 🧳 Travel Planner with LangGraph + Groq

This is a modular **Travel Planning AI workflow** built using [LangGraph](https://www.langgraph.dev/), a library for creating stateful and graph-based LLM applications. It leverages **Groq’s blazing-fast LLMs** (like LLaMA 3) for generating flight options, hotels, and activities based on your destination and budget.

---

## 🚀 Features

- ✈️ Searches for flights
- 🏨 Searches for hotels (optional)
- 🎭 Plans top tourist activities
- 📊 Summarizes your travel plan
- ⚙️ Powered by **LangGraph nodes and edges**
- 🤖 Uses **Groq API** with LLaMA 3 model
- 🧠 Modular design for easy reuse and expansion

---

## 🔧 Tech Stack

| Tool           | Purpose                        |
|----------------|--------------------------------|
| LangGraph      | Workflow engine (nodes & state)|
| Groq API       | Free, fast LLM for generation  |
| Python         | Main language                  |
| .env file      | Secure API key storage         |
| Jupyter (.ipynb)| Interactive notebook interface |

---

## 🧠 LangGraph Concepts Used

This project defines a **state machine** using:

### 📦 State
The state is a Python `TypedDict` that stores:
- `destination`, `budget`
- `flights`, `hotels`, `activities`
- `include_hotels` (bool)
- `messages` (log)
- `step_count` (incremental count)

### 🧩 Nodes

Each node is a function that takes and returns state:
- `add_destination`: Gets user input
- `search_flights`: Queries Groq for flights
- `search_hotels`: Queries Groq for hotels
- `plan_activities`: Queries Groq for activities
- `summarize`: Prints and logs the plan
- `router`: Decides if hotel search is needed

### 🔀 Edges

Edges connect nodes:
- Linear: `START → add_destination → search_flights → summarize`
- Conditional: Checks `include_hotels` to decide if `search_hotels` is run
- Parallel branches: Flights + Hotels + Activities can run in parallel
- Merge at `summarize → END`

---

## 🧪 Example Output

```
📋 TRAVEL PLAN SUMMARY for Paris:
✈️ Flights: 3 options
🏨 Hotels: 3 options  
🎭 Activities: 3 planned
📊 Total processing steps: 5
```

---

## 🔐 Environment Setup

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Create `.env` file

Inside the project root:

```env
GROQ_API_KEY=your_actual_key_here
GROQ_MODEL=llama3-8b-8192
```

> **Note:** `.env` is excluded from version control using `.gitignore`.

---

## 🧠 How to Run

### Option A: Run all in notebook
> File: `travel_planner.ipynb`

### Option B: Modular run
1. Load Groq model from `model.py`
2. Import model into notebook:
```python
from model import GroqChatModel
model = GroqChatModel()
```
3. Run the LangGraph workflow from `travel_planner.ipynb`

---

## 🛡️ Security

- `.env` is **not committed** to GitHub thanks to `.gitignore`
- API key is safely loaded via `python-dotenv`

---

## 📚 Resources

- [LangGraph Documentation](https://www.langgraph.dev/)
- [Groq API Docs](https://console.groq.com/docs)
- [GitHub Repo](https://github.com/Captain-Droid3125/Travel-Planner)

---

## 🧑‍💻 Author

> Built by [Captain-Droid3125](https://github.com/Captain-Droid3125) — passionate about LLM workflows and AI systems 🚀

