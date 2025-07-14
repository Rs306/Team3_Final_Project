# Team_3 final_project 

This is a Streamlit-based document assistant application that allows users to upload PDF files and interact with their contents using a conversational interface. The chatbot answers questions strictly based on the uploaded documents and includes page number citations. If the answer cannot be found, it politely informs the user.

## Features

- Upload and process one or more PDF files
- Ask natural language questions about the content
- Answers cite specific page numbers (e.g., “(page 3)”)
- Clear fallback message if the answer isn’t in the documents
- Adjustable retrieval settings:
  - Top context chunks
  - Candidate pool size
  - Diversity (MMR)
- Toggle between OpenAI models (`gpt-4o` or `gpt-3.5-turbo`)

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/final_project.git
cd final_project
```

### 2. Create a virtual environment and activate it

```bash
python -m venv venv
# On macOS/Linux
source venv/bin/activate
# On Windows
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

Or manually install:

```bash
pip install streamlit langchain langchain-community langchain-openai openai faiss-cpu
```

### 4. Set your OpenAI API key

```bash
# On macOS/Linux
export OPENAI_API_KEY="your-api-key"

# On Windows (CMD)
set OPENAI_API_KEY="your-api-key"
```

## Run the App

```bash
streamlit run final_project.py
```

Visit `http://localhost:8501` in your browser.

## How It Works

1. PDF files are uploaded and converted to text.
2. The text is split into manageable chunks.
3. FAISS creates a vector store from the text embeddings.
4. When a question is asked, the most relevant chunks are retrieved.
5. A prompt is passed to an OpenAI model to generate an answer, grounded only in the document content.
6. If no relevant context is found, the assistant responds accordingly.

## System Prompt Logic

- The assistant must always cite page numbers.
- If insufficient context is available, it says:
  _“I don’t have enough information in the document to answer that. Could you please clarify or ask a different question?”_
- No hallucinations or external data are allowed.
- The assistant is polite, accurate, and document-focused.

## License

This project is for educational or internal use. Feel free to modify or extend it as needed.

---
