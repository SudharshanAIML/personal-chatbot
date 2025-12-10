# LangChain Chatbot with Gemini & LangSmith

A simple chatbot application built with LangChain, Google Gemini AI, and Streamlit, featuring LangSmith integration for observability and tracing.

## Features

- 🤖 **Google Gemini AI** - Powered by Google's Gemini 2.5 Flash model
- 🔗 **LangChain** - Uses LangChain for prompt templating and chain orchestration
- 🖥️ **Streamlit UI** - Simple and interactive web interface
- 📊 **LangSmith Integration** - Full observability and tracing for your LLM applications

## Prerequisites

- Python 3.10+
- Google API Key (for Gemini)
- LangSmith API Key (for tracing)

## Installation

1. **Clone the repository and navigate to the chatbot directory:**
   ```bash
   cd chatbot
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv langchain-series
   source langchain-series/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   
   Create a `.env` file in the `chatbot` directory:
   ```env
   GEMINI_API_KEY=your_google_api_key_here
   LANGCHAIN_API_KEY=your_langsmith_api_key_here
   ```

## Running the Application

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`.

---

## LangSmith Integration

This project uses **LangSmith** for monitoring and debugging your LLM applications.

### What is LangSmith?

[LangSmith](https://smith.langchain.com/) is a platform developed by LangChain for building production-grade LLM applications. It provides:

- **Tracing** - Track every step of your LLM chain execution
- **Debugging** - Identify issues in prompts, chains, and outputs
- **Monitoring** - Observe performance metrics and latency
- **Evaluation** - Test and evaluate your LLM outputs

### How LangSmith is Configured

In `app.py`, LangSmith tracing is enabled with:

```python
os.environ["LANGCHAIN_API_KEY"] = os.getenv("LANGCHAIN_API_KEY")
os.environ["LANGCHAIN_TRACING_V2"] = "true"
```

### Useful Insights from LangSmith

Once tracing is enabled, you can view the following in the [LangSmith Dashboard](https://smith.langchain.com/):

| Feature | Description |
|---------|-------------|
| **Run Traces** | View the complete execution flow of each chain invocation |
| **Input/Output Logs** | See exact prompts sent to the LLM and responses received |
| **Latency Metrics** | Monitor response times for each component in your chain |
| **Token Usage** | Track token consumption for cost optimization |
| **Error Tracking** | Identify and debug failed runs with detailed error logs |
| **Chain Visualization** | Visualize how prompts, LLMs, and parsers are connected |

### Accessing LangSmith Dashboard

1. Go to [smith.langchain.com](https://smith.langchain.com/)
2. Sign in with your account
3. Navigate to your project to view traces
4. Click on individual runs to see detailed execution logs

### Best Practices

- ✅ **Always enable tracing in development** to debug chain behavior
- ✅ **Use project names** to organize traces (set `LANGCHAIN_PROJECT` env var)
- ✅ **Add metadata** to runs for better filtering and analysis
- ✅ **Review traces regularly** to identify prompt improvements
- ⚠️ **Disable tracing in production** if you have sensitive data concerns (or use LangSmith's data privacy features)

### Optional: Set a Project Name

Add this to your `.env` to organize traces by project:

```env
LANGCHAIN_PROJECT=my-chatbot-project
```

---

## Project Structure

```
chatbot/
├── app.py              # Main Streamlit application
├── requirements.txt    # Python dependencies
├── test.py            # Test file
├── README.md          # This file
└── .env               # Environment variables (create this)
```

## Tech Stack

- **LangChain** - LLM application framework
- **LangChain Google GenAI** - Google Gemini integration
- **Streamlit** - Web UI framework
- **LangSmith** - Observability platform
- **python-dotenv** - Environment variable management

## License

MIT License
