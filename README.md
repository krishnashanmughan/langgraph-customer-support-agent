# Agentic Customer Support Workflow (LangGraph)

An LLM-powered support agent built with LangGraph that categorizes
incoming queries, analyzes sentiment, and routes each one to the right
handler — automatically escalating negative-sentiment queries to a human.

## How It Works
The agent runs as a compiled state graph:

`categorize` → `analyze_sentiment` → **conditional route** → handler → `END`

- **State:** a `TypedDict` holding the query, category, sentiment, and response.
- **Categorization:** classifies the query into Technical / Billing / General.
- **Sentiment:** scores it Positive / Neutral / Negative.
- **Routing:** negative sentiment → `escalate`; otherwise routed by category.
- **Handlers:** a dedicated LLM response node per category, plus an escalation node.

## Tech Stack
Python · LangGraph · LangChain · OpenAI · python-dotenv

## Run
```bash
pip install langgraph langchain-core langchain-openai python-dotenv ipython
# add OPENAI_API_KEY to a .env file, then run the notebook
```

## Possible Extensions
Conversation memory, RAG over a knowledge base, tool/function calling,
and an evaluation harness to measure routing accuracy.

## License
MIT
