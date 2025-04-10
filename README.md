# Financial-Agent


This notebook demonstrates a **finance-focused AI agent** built using [LangChain](https://www.langchain.com/), [Groq's LLaMA3 model](https://groq.com/), and `yfinance`. The agent is capable of answering natural language questions about public companies by dynamically calling tools that fetch financial data.

---

## Features

-  **Retrieve company financials** (market cap, revenue, debt, etc.)
-  **Fetch stock-related news**
-  **Get recent dividends & earnings**
-  **See top institutional & mutual fund holders**
-  **Check stock rating upgrades & downgrades**
-  **Access stock split history**

---

## How It Works

### 1. **LLM Setup**
Uses **Groq's LLaMA3 (8B)** model via `ChatGroq` for fast, intelligent response generation.

### 2. **Custom Tools via LangChain**
The following tools are defined using `@tool` decorators:
- `company_information(ticker)`
- `last_dividend_and_earnings_date(ticker)`
- `summary_of_mutual_fund_holders(ticker)`
- `summary_of_institutional_holders(ticker)`
- `stock_grade_updrages_downgrades(ticker)`
- `stock_splits_history(ticker)`
- `stock_news(ticker)`

All of these use the `yfinance` library to fetch real-time data.

### 3. **Prompt & Agent Creation**
- Custom system prompt encourages tool usage.
- Tools are integrated into a tool-calling agent using `create_tool_calling_agent`.

### 4. **Agent Execution**
The `AgentExecutor` runs the agent, interprets the user’s natural language query, and invokes the right tools.


