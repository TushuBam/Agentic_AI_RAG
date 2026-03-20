# RAG AI Agent

A simple Retrieval-Augmented Generation (RAG) agent built with **LangGraph** and **ChromaDB**.

## Architecture

```
PDF Files ──► Ingestion Pipeline ──► ChromaDB Vector Store
                                            │
User Question ──► LangGraph RAG Agent ──────┤
                       │                    │
                   [Retrieve] ◄─────────────┘
                       │
                   [Generate] ──► Final Answer
```

### Phase 1: Ingestion (`ingestion.py`)
1. **Data Extraction** - Load PDF files from `data/` using PyPDF
2. **Chunking** - Split documents into overlapping chunks (1000 chars, 200 overlap)
3. **Vector DB Creation** - Embed chunks with OpenAI embeddings and store in ChromaDB

### Phase 2: RAG Agent (`rag_agent.py`)
A LangGraph state graph with two nodes:
1. **Retrieve** - Similarity search against ChromaDB to find relevant chunks
2. **Generate** - LLM answers the question using only the retrieved context

## Setup

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Create .env file with your OpenAI API key
cp .env.example .env
# Edit .env and add your key

# 3. Add PDF files to the data/ folder
mkdir data
# Copy your PDFs into data/

# 4. Run the agent
python main.py
```

## Project Structure

```
├── main.py           # Entry point - runs ingestion then interactive Q&A
├── ingestion.py      # PDF loading, chunking, ChromaDB vector store creation
├── rag_agent.py      # LangGraph RAG agent (retrieve + generate nodes)
├── requirements.txt  # Python dependencies
├── .env.example      # Template for environment variables
└── data/             # Place PDF files here (gitignored)
```

## How It Works

1. Place your PDF documents in the `data/` folder
2. Run `python main.py`
3. The system ingests PDFs into ChromaDB (first run only)
4. Ask questions interactively - the agent retrieves relevant chunks and generates answers


# here attach some screen shot of my RAG testing:
1. I have create the Educational Tutor agent.
2. in .data folder upload your Educational PDf.
3. Ask the question to agent.
4. I tested agent base on my pdf.
5. first i asked question about electromagnetic field? agnet give answer and quize as below screen shot:

<img width="1840" height="863" alt="image" src="https://github.com/user-attachments/assets/45e02033-e7ae-4156-89b3-1cfd128a9f42" />

<img width="1367" height="737" alt="image" src="https://github.com/user-attachments/assets/0e403f64-cea7-4aeb-bd44-ac6b6d1d4522" />

<img width="1282" height="792" alt="image" src="https://github.com/user-attachments/assets/6140b3d4-6c19-4122-bcaf-9730fc10decb" />

6. Second I asked about Pallindrom? give answer and quize as below screen shot:

<img width="1368" height="782" alt="image" src="https://github.com/user-attachments/assets/4c01dc86-be4d-4396-a9d8-c3f467830a55" />

<img width="1361" height="832" alt="image" src="https://github.com/user-attachments/assets/bb888e68-f3ab-4d23-ae63-2f942baf0d51" />





