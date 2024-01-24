# Chat with your docs

## Introduction

This repository demonstrates how to build a simple LLM-based chatbot that can answer questions based on your documents (retrieval augmented generation - RAG)

The software stack only uses open source tools [streamlit](https://streamlit.io), [LlamaIndex](https://llamaindex.ai) and local open LLMs via [Ollama](https://ollama.ai). Real open AI for the GPU poor.

Everyone is invited to fork this repository, create their own specific purpose chatbot based on their documents, improve the setup or even hold your own workshop.

## Setup

For the local setup a Mac M1 with 16GB unified memory and above are recommended. First download Ollama from [ollama.ai](https://ollama.ai) and install it.

On Linux you can disable the Ollama service for better debugging:

```
sudo systemctl disable ollama
sudo systemctl stop ollama
```

and then manually run `ollama serve`.

For the local example have a look at the folder `streamlit` and install the requirements:

```
pip install -r requirements.txt
```

Then start streamlit with:
```
streamlit run app.py
```

![](linuxbot.gif)

Modify the system prompt and copy different data sources to `docs/` in order to create your own version of the chatbot.
You can set the ollama host via the enviroment variable `OLLAMA_HOST`.

You can download models locally with `ollama pull zephyr` or via API:

```
curl -X POST http://ollama:11434/api/pull -d '{"name": "zephyr"}'
```

First start the ollama service as described and download the [Zephyr model](https://ollama.ai/library/zephyr).
To test the ollama server you can call the generate API:

```
curl -X POST http://ollama:11434/api/generate -d '{"model": "zephyr", "prompt": "Why is the sky blue?"}'
```

All of these commands are also documented in our [cheat sheet](cheatsheet.txt).


## References

- [Build a chatbot with custom data sources, powered by LlamaIndex](https://blog.streamlit.io/build-a-chatbot-with-custom-data-sources-powered-by-llamaindex/)
- [SQL Query Engine with LlamaIndex + DuckDB](https://gpt-index.readthedocs.io/en/latest/examples/index_structs/struct_indices/duckdb_sql_query.html)
- [AI on Openshift - LLMs, Chatbots, Talk with your Documentation](https://ai-on-openshift.io/demos/llm-chat-doc/llm-chat-doc/)
- [Open Sourcerers - A personal AI assistant for developers that doesn't phone home](https://www.opensourcerers.org/2023/11/06/a-personal-ai-assistant-for-developers-that-doesnt-phone-home/)

