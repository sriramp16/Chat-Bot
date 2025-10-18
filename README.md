# LangGraph Chatbot with Grok Integration

A powerful conversational AI chatbot built with LangGraph, Streamlit, and integrated with Grok's GPT-OSS-20B model. This chatbot features tool integration, conversation memory, and a modern web interface.

## 🚀 Features

- **Grok AI Integration**: Powered by Grok's GPT-OSS-20B model
- **Tool Integration**: Built-in tools for web search, calculations, and stock price lookup
- **Conversation Memory**: Persistent chat history across sessions
- **Multiple Chat Threads**: Manage multiple conversation threads
- **Real-time Streaming**: Live response streaming with tool usage indicators
- **Modern UI**: Clean, responsive Streamlit interface

## 🛠️ Available Tools

1. **Web Search**: DuckDuckGo search integration for real-time information
2. **Calculator**: Basic arithmetic operations (add, subtract, multiply, divide)
3. **Stock Price Lookup**: Real-time stock price information via Alpha Vantage API

## 📋 Prerequisites

- Python 3.11 or higher
- pip package manager
- Grok API key (configured in the code)

## 🔧 Installation

1. **Clone or download the project files**

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt --user
   ```

3. **Fix NumPy compatibility issue** (if encountered):
   ```bash
   pip install --upgrade numexpr bottleneck --user
   ```

## ⚙️ Configuration

The chatbot is pre-configured with your Grok API key and model:

```python
llm = ChatOpenAI(
    model="openai/gpt-oss-20b",
    api_key="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",
    base_url="https://api.groq.com/openai/v1"
)
```

## 🚀 Running the Application

### Option 1: Tool-Enabled Chatbot (Recommended)
```bash
streamlit run streamlit_frontend_tool.py
```

### Option 2: Basic Chatbot
```bash
streamlit run streamlit_frontend.py
```

### Option 3: Database-Enabled Chatbot
```bash
streamlit run streamlit_frontend_database.py
```

### Option 4: Streaming Chatbot
```bash
streamlit run streamlit_frontend_streaming.py
```

### Option 5: Threading Chatbot
```bash
streamlit run streamlit_frontend_threading.py
```

## 🌐 Accessing the Application

Once running, open your web browser and navigate to:
- **Local URL**: http://localhost:8501
- **Network URL**: http://10.1.195.35:8501 (accessible from other devices on your network)

## 📁 Project Structure

```
chatbot-in-langgraph-main/
├── langgraph_backend.py              # Basic LangGraph backend
├── langgraph_database_backend.py     # Database-enabled backend
├── langgraph_tool_backend.py         # Tool-integrated backend (main)
├── streamlit_frontend.py             # Basic frontend
├── streamlit_frontend_database.py    # Database frontend
├── streamlit_frontend_streaming.py   # Streaming frontend
├── streamlit_frontend_threading.py   # Threading frontend
├── streamlit_frontend_tool.py        # Tool-enabled frontend (main)
├── requirements.txt                   # Python dependencies
├── chatbot.db                        # SQLite database (auto-created)
└── README.md                         # This file
```

## 🎯 Usage Examples

### Basic Conversation
```
User: Hello! What can you help me with?
Bot: Hello! I can help you with various tasks including web searches, calculations, and stock price lookups. What would you like to know?
```

### Web Search
```
User: What's the latest news about AI?
Bot: [Performs web search] Here's what I found about the latest AI news...
```

### Calculator
```
User: What's 25 * 4 + 10?
Bot: [Uses calculator tool] 25 * 4 + 10 = 110
```

### Stock Price
```
User: What's the current price of AAPL?
Bot: [Fetches stock data] The current price of Apple Inc. (AAPL) is...
```

## 🔧 Troubleshooting

### NumPy Compatibility Issues
If you encounter NumPy-related errors, try:
```bash
pip install --upgrade numexpr bottleneck --user
```

### Permission Errors
If you get permission errors during installation:
```bash
pip install -r requirements.txt --user
```

### Port Already in Use
If port 8501 is already in use:
```bash
streamlit run streamlit_frontend_tool.py --server.port 8502
```

### API Key Issues
Ensure your Grok API key is valid and has sufficient credits.

## 🛠️ Customization

### Adding New Tools
1. Define your tool function in `langgraph_tool_backend.py`:
```python
@tool
def your_custom_tool(param: str) -> str:
    """Your tool description"""
    # Tool implementation
    return result
```

2. Add it to the tools list:
```python
tools = [search_tool, get_stock_price, calculator, your_custom_tool]
```

### Changing the Model
Modify the LLM configuration in `langgraph_tool_backend.py`:
```python
llm = ChatOpenAI(
    model="your-model-name",
    api_key="your-api-key",
    base_url="your-base-url"
)
```

## 📊 Database Schema

The application uses SQLite for conversation persistence:
- **Table**: `checkpoints`
- **Purpose**: Stores conversation state and message history
- **Location**: `chatbot.db` (auto-created)

## 🔒 Security Notes

- API keys are hardcoded in the configuration files
- For production use, consider using environment variables
- Database files are stored locally and not encrypted

## 📝 License

This project is for educational and personal use. Please ensure you comply with Grok's API terms of service.

## 🤝 Contributing

Feel free to fork this project and submit pull requests for improvements.

## 📞 Support

If you encounter any issues:
1. Check the troubleshooting section above
2. Verify your API key is valid
3. Ensure all dependencies are properly installed
4. Check the terminal output for specific error messages

---

**Happy Chatting! 🤖💬**
