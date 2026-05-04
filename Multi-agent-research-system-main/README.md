# 🔬 ResearchMind · Multi-Agent AI Research System

A sophisticated multi-agent AI system that autonomously conducts research on any topic, gathers information from the web, synthesizes findings into a detailed report, and provides constructive feedback.

## 🎯 Overview

ResearchMind combines multiple AI agents and LLMs to automate the entire research process:

1. **Search Agent** - Finds recent, reliable information across the web
2. **Reader Agent** - Scrapes and extracts detailed content from relevant sources
3. **Writer Chain** - Synthesizes research into a structured, professional report
4. **Critic Chain** - Reviews and evaluates the report with constructive feedback

This system demonstrates an advanced multi-agent architecture using LangChain and OpenAI's GPT models.

---

## 📋 Features

- **Automated Research Pipeline**: End-to-end research workflow without manual intervention
- **Web Search Integration**: Uses Tavily API for accurate, reliable information retrieval
- **Web Scraping**: Extracts clean content from URLs for deeper analysis
- **AI-Powered Writing**: Generates comprehensive, structured research reports
- **Critical Review**: AI critic provides quality feedback and improvement suggestions
- **Streamlit UI**: Beautiful, modern web interface for easy interaction
- **Modular Architecture**: Clean separation of concerns (agents, tools, pipeline)

---

## 🏗️ Project Structure

```
Multi-agent-research-system-main/
├── app.py              # Streamlit web application with UI
├── agents.py           # LLM agents & chains (search, reader, writer, critic)
├── pipeline.py         # Main research pipeline orchestration
├── tools.py            # Web search & URL scraping tools
├── requirements.txt    # Python dependencies
└── README.md          # This file
```

### File Descriptions

#### **app.py**
- Streamlit-based web interface
- Beautiful custom CSS styling with gradient backgrounds
- Input forms for research topics
- Display of research results in real-time

#### **agents.py**
- **build_search_agent()**: Creates an agent with web_search tool using GPT-4o-mini
- **build_reader_agent()**: Creates an agent with scrape_url tool
- **writer_chain**: LLM chain that drafts professional research reports
- **critic_chain**: LLM chain that reviews and critiques reports

#### **pipeline.py**
- **run_research_pipeline(topic)**: Orchestrates the complete research workflow
  - Step 1: Search agent gathers initial information
  - Step 2: Reader agent scrapes detailed content from top sources
  - Step 3: Writer chain synthesizes into a report
  - Step 4: Critic chain provides quality feedback

#### **tools.py**
- **web_search(query)**: Searches the web using Tavily API
  - Returns titles, URLs, and content snippets
  - Limits to 5 most relevant results
- **scrape_url(url)**: Scrapes and cleans HTML content
  - Removes scripts, styles, navigation, footers
  - Returns up to 3000 characters of clean text

#### **requirements.txt**
All necessary Python packages for LLM agents, web scraping, and API integrations.

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.9 or higher
- OpenAI API key
- Tavily API key

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/Multi-agent-research-system.git
cd Multi-agent-research-system-main
```

### Step 2: Create Virtual Environment
```bash
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables
Create a `.env` file in the project root:
```env
OPENAI_API_KEY=your_openai_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here
```

Get your keys from:
- **OpenAI API**: https://platform.openai.com/api-keys
- **Tavily API**: https://tavily.com/ (sign up and get API key)

---

## 💻 Usage

### Option 1: Streamlit Web Interface (Recommended)
```bash
streamlit run app.py
```
Then open your browser to `http://localhost:8501` and enter a research topic.

### Option 2: Command Line
```bash
python pipeline.py
```
Enter your research topic when prompted.

### Example Research Topics
- "Latest developments in quantum computing"
- "Impact of AI on healthcare"
- "Renewable energy trends 2024"
- "Machine learning in finance"

---

## 📊 How It Works

### Research Pipeline Flow

```
User Input (Topic)
    ↓
Search Agent (Web Search via Tavily)
    ↓ [Search Results + URLs]
Reader Agent (Scrape URLs)
    ↓ [Detailed Content]
Writer Chain (Synthesize & Draft)
    ↓ [Professional Report]
Critic Chain (Review & Feedback)
    ↓
Final Output (Report + Feedback)
```

### Example Output Structure

**Report includes:**
- Introduction to the topic
- Key Findings (minimum 3 points)
- Detailed conclusion
- List of all sources

**Critic Feedback includes:**
- Quality score (out of 10)
- Strengths of the report
- Areas for improvement
- One-line verdict

---

## 🔧 Configuration

### Model Settings
Edit `agents.py` to change the LLM model:
```python
llm = ChatOpenAI(model="gpt-4o-mini", temperature=0)
```

### Available Models
- `gpt-4o-mini` (recommended, fast & affordable)
- `gpt-4o` (more powerful)
- `gpt-4` (legacy)

### Temperature Control
- `temperature=0` - Deterministic, consistent responses
- `temperature=0.7` - Balanced creativity
- `temperature=1.0` - Maximum randomness

---

## 📦 Dependencies

| Package | Purpose |
|---------|---------|
| `langchain` | Multi-agent framework |
| `langchain-openai` | OpenAI integration |
| `openai` | GPT models API |
| `tavily-python` | Web search tool |
| `beautifulsoup4` | HTML parsing & scraping |
| `streamlit` | Web UI framework |
| `python-dotenv` | Environment variables |
| `requests` | HTTP library |
| `pydantic` | Data validation |
| `rich` | Console output formatting |

---

## 🎨 UI Customization

The Streamlit interface includes custom CSS styling in `app.py` with:
- Dark theme with orange accents (#ff8c32)
- Gradient backgrounds
- Custom fonts (Syne, DM Mono, DM Sans)
- Responsive design
- Smooth transitions

Modify the CSS in the `st.markdown()` section to customize colors and styling.

---

## ⚠️ Error Handling

The system includes error handling for:
- **Network failures**: Gracefully handles scraping timeouts
- **Invalid URLs**: Returns error message instead of crashing
- **API failures**: Falls back or retries with exponential backoff
- **Empty responses**: Provides meaningful feedback

---

## 🔐 Security & Best Practices

1. **Never commit `.env` file** - Keep API keys private
2. **Use environment variables** - All sensitive data loaded from `.env`
3. **Rate limiting** - Tavily API has usage limits
4. **User-Agent headers** - Required for web scraping
5. **Timeout protection** - 8-second timeout on web requests

---

## 🐛 Troubleshooting

### Issue: "API key not found"
```
Solution: Ensure .env file exists and contains OPENAI_API_KEY and TAVILY_API_KEY
```

### Issue: "Tavily API error"
```
Solution: Verify your Tavily API key is valid and active
```

### Issue: "Streamlit not found"
```
Solution: pip install streamlit
```

### Issue: "Connection timeout"
```
Solution: Check internet connection and firewall settings
```

---

## 📈 Performance Tips

1. **Use gpt-4o-mini** for faster responses and lower cost
2. **Limit search results** - Currently set to 5 results
3. **Cache results** - Implement caching for repeated topics
4. **Adjust temperature** - Lower for consistency, higher for creativity
5. **Parallel execution** - Tools support async operations

---

## 🚀 Future Enhancements

- [ ] Database storage for research history
- [ ] Citation management and formatting
- [ ] Multi-language support
- [ ] Custom report templates
- [ ] Real-time progress updates
- [ ] Export to PDF/Word
- [ ] User authentication & workspace
- [ ] Advanced filtering and source verification

---

## 📝 Example Research Output

### Input Topic
"Latest developments in quantum computing"

### Output Report
```
INTRODUCTION
Quantum computing represents one of the most transformative 
technologies of the 21st century...

KEY FINDINGS
1. Recent Breakthroughs in Quantum Error Correction
   [Detailed explanation with sources]

2. Industrial Applications Expanding
   [Real-world implementations discussed]

3. Investment Growth and Company Initiatives
   [Market trends and key players]

CONCLUSION
The quantum computing field is experiencing unprecedented growth...

SOURCES
- https://arxiv.org/...
- https://research.google.com/...
- https://quantumcomputing.ibm.com/...
```

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👨‍💻 Author

Created as an advanced demonstration of multi-agent AI systems using LangChain and OpenAI.

---

## 🔗 Useful Resources

- **LangChain Docs**: https://python.langchain.com/
- **OpenAI API**: https://platform.openai.com/docs/
- **Tavily Search**: https://tavily.com/
- **Streamlit Docs**: https://docs.streamlit.io/
- **BeautifulSoup Docs**: https://www.crummy.com/software/BeautifulSoup/

---

## 📞 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review error messages in the logs

---

**Happy Researching! 🚀**
