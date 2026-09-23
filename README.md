# 🎓 AI StudyMate — AI-Powered Student Study Assistant

AI StudyMate is an AI-powered study assistant that allows students to upload their own **PDF or TXT study material**, ask questions about it, generate summaries and quizzes, and save their study sessions.

The project demonstrates a complete AI application pipeline:

> **Input → AI Logic → Interface → Storage → Action**

The entire project is implemented in a **single Google Colab notebook** using Python, Gradio, FAISS, Sentence Transformers, and Google Gemini.

---

## 🚀 Features

* 📄 Upload **PDF or TXT** study material
* 🧹 Automatic text extraction and cleaning
* ✂️ Text chunking for efficient retrieval
* 🧠 Semantic embeddings using **Sentence Transformers**
* 🔎 Semantic search using **FAISS**
* 🤖 Retrieval-Augmented Generation (**RAG**) using Google Gemini
* 💬 Ask questions about uploaded study material
* 📝 Generate AI-powered summaries
* ❓ Generate practice quizzes
* 📚 View previous study history
* 💾 Store study sessions in JSON
* 📥 Download generated answers, summaries, and quizzes
* 🌐 Interactive **Gradio** web interface
* ☁️ Runs directly in **Google Colab**

---

## 🏗️ System Architecture

```text
                    ┌──────────────────┐
                    │     Student      │
                    └────────┬─────────┘
                             │
                             ▼
                 ┌──────────────────────┐
                 │    PDF / TXT Input   │
                 │    + User Question   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   Text Extraction    │
                 │    & Cleaning        │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   Text Chunking      │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Sentence Transformers│
                 │  all-MiniLM-L6-v2    │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │       FAISS          │
                 │  Semantic Retrieval  │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   Relevant Context   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │     Gemini RAG       │
                 │   Answer Generation  │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   Gradio Interface   │
                 └──────────┬───────────┘
                            │
              ┌─────────────┼──────────────┐
              ▼             ▼              ▼
          Answer        Summary          Quiz
              │             │              │
              └─────────────┼──────────────┘
                            ▼
                 ┌──────────────────────┐
                 │   Study History      │
                 │ study_history.json   │
                 └──────────────────────┘
```

---

## 🔄 AI Project Pipeline

The project follows the required five-stage AI application pipeline:

| Component     | Implementation                                               |
| ------------- | ------------------------------------------------------------ |
| **Input**     | PDF/TXT study material and student questions                 |
| **AI Logic**  | Text processing, embeddings, FAISS retrieval, and Gemini RAG |
| **Interface** | Gradio web interface                                         |
| **Storage**   | In-memory state + `study_history.json`                       |
| **Action**    | Answers, summaries, quizzes, history, and downloads          |

---

## 🧠 How It Works

### 1. Upload Study Material

The student uploads a PDF or TXT file containing lecture notes, study material, textbook content, or other educational resources.

### 2. Extract and Clean Text

The system extracts text from the uploaded document and performs basic text cleaning.

### 3. Chunk the Document

Large documents are divided into smaller overlapping chunks so that relevant portions can be retrieved efficiently.

### 4. Generate Embeddings

Each chunk is converted into a numerical vector using:

```text
Sentence Transformers
all-MiniLM-L6-v2
```

### 5. Store Embeddings in FAISS

The generated embeddings are stored in a FAISS vector index.

FAISS allows the system to perform semantic similarity search and identify the most relevant document chunks.

### 6. Ask a Question

The student enters a natural-language question.

For example:

```text
What is the difference between machine learning and deep learning?
```

### 7. Retrieve Relevant Context

The question is converted into an embedding and compared against the document embeddings.

The most relevant chunks are retrieved.

### 8. Generate an Answer with Gemini

The retrieved chunks are provided to Google Gemini as context.

Gemini then generates a response based on the retrieved study material.

### 9. Additional Study Actions

The student can also:

* Generate a summary
* Generate a quiz
* View study history
* Download generated content

---

## 🛠️ Technology Stack

| Technology                | Purpose                               |
| ------------------------- | ------------------------------------- |
| **Python**                | Core programming language             |
| **Google Colab**          | Development and execution environment |
| **Gradio**                | Web interface                         |
| **Google Gemini API**     | Generative AI and RAG                 |
| **Sentence Transformers** | Semantic embeddings                   |
| **all-MiniLM-L6-v2**      | Pretrained embedding model            |
| **FAISS**                 | Vector search and retrieval           |
| **PyPDF**                 | PDF text extraction                   |
| **NumPy**                 | Numerical processing                  |
| **pandas**                | Data processing                       |
| **JSON**                  | Study history storage                 |

---

## 📁 Project Structure

```text
AI-StudyMate/
│
├── AI_StudyMate_Complete_Colab.ipynb
├── AI_StudyMate_Formal_Project_Document.docx
├── README.md
└── .gitignore
```

### Files

#### `AI_StudyMate_Complete_Colab.ipynb`

The complete implementation of AI StudyMate, including:

* Dependency installation
* Gemini configuration
* PDF/TXT processing
* Text cleaning
* Chunking
* Embedding generation
* FAISS indexing
* Semantic retrieval
* Gemini RAG
* Summary generation
* Quiz generation
* JSON storage
* Download functionality
* Gradio interface

#### `AI_StudyMate_Formal_Project_Document.docx`

The formal academic project document containing:

* Introduction
* Problem statement
* Objectives
* Proposed solution
* AI pipeline
* System architecture
* Technology stack
* Implementation
* Testing
* Results
* Limitations
* Future improvements
* Conclusion

---

## ▶️ Running the Project

### Option 1 — Google Colab

Open:

```text
AI_StudyMate_Complete_Colab.ipynb
```

in Google Colab.

Run the notebook cells from top to bottom.

The notebook will install the required dependencies automatically.

---

## 🔑 Gemini API Key

AI StudyMate requires a Google Gemini API key for AI-generated answers, summaries, and quizzes.

The notebook requests the key at runtime using a secure password-style input.

Example:

```python
import getpass

GEMINI_API_KEY = getpass.getpass(
    "Enter your Gemini API key: "
).strip()
```

The API key is **not stored directly in the source code**.

### ⚠️ Security

**Never commit your Gemini API key to GitHub.**

Do not put:

```python
GEMINI_API_KEY = "YOUR_REAL_API_KEY"
```

inside the notebook.

If an API key is accidentally exposed, revoke it and generate a new key.

---

## 📦 Required Libraries

The project uses the following main Python packages:

```text
gradio
google-genai
sentence-transformers
faiss-cpu
pypdf
pandas
numpy
scikit-learn
```

They are installed automatically by the notebook.

---

## 🧪 Testing

The completed application was tested end-to-end.

### Test Results

| Test                         | Result   |
| ---------------------------- | -------- |
| Gemini API connection        | ✅ Passed |
| Model availability           | ✅ Passed |
| PDF upload                   | ✅ Passed |
| TXT processing               | ✅ Passed |
| Text extraction              | ✅ Passed |
| Text chunking                | ✅ Passed |
| Embedding generation         | ✅ Passed |
| FAISS indexing               | ✅ Passed |
| Semantic retrieval           | ✅ Passed |
| Question answering           | ✅ Passed |
| Summary generation           | ✅ Passed |
| Quiz generation              | ✅ Passed |
| Study history                | ✅ Passed |
| Download functionality       | ✅ Passed |
| Gradio interface             | ✅ Passed |
| Complete end-to-end workflow | ✅ Passed |

---

## 💡 Example Questions

After uploading study material, students can ask questions such as:

```text
What is Artificial Intelligence?
```

```text
What is the difference between supervised and unsupervised learning?
```

```text
Explain the main concepts discussed in this document.
```

```text
What are the advantages of machine learning?
```

The system retrieves relevant content from the uploaded document before generating the answer.

---

## 🎯 Example Workflow

```text
Upload PDF
    ↓
Process Document
    ↓
Extract Text
    ↓
Clean Text
    ↓
Create Chunks
    ↓
Generate Embeddings
    ↓
Build FAISS Index
    ↓
Ask Question
    ↓
Semantic Retrieval
    ↓
Retrieve Relevant Context
    ↓
Gemini RAG
    ↓
Generate Answer
    ↓
Save Study History
```

---

## 📚 RAG Architecture

AI StudyMate uses **Retrieval-Augmented Generation (RAG)**.

Instead of directly asking the language model to answer a question from its general knowledge, the system first retrieves relevant information from the student's uploaded material.

```text
User Question
      ↓
Question Embedding
      ↓
FAISS Similarity Search
      ↓
Relevant Document Chunks
      ↓
Context + Question
      ↓
Gemini
      ↓
Grounded Answer
```

This makes the system particularly useful for questions related to specific lecture notes or study documents.

---

## 💾 Storage

The application uses two forms of storage.

### Session Storage

The active document, chunks, embeddings, and FAISS index are maintained in memory while the application is running.

### Persistent Storage

Study sessions are stored in:

```text
study_history.json
```

The stored information can include:

* Document name
* Timestamp
* Chat history
* Generated summary
* Generated quiz

---

## ⚠️ Limitations

The current prototype has several limitations:

1. Complex PDF layouts may not extract perfectly.
2. Scanned PDFs may require OCR.
3. Image-heavy documents are not fully interpreted.
4. Gemini API access depends on account and quota availability.
5. The FAISS index is session-based.
6. JSON storage is suitable for a prototype but not large-scale deployment.
7. Internet access is required for Gemini API usage and remote model resources.

---

## 🔮 Future Improvements

Possible future improvements include:

* 🔍 OCR support for scanned PDFs
* 📚 Multi-document course collections
* 🗄️ SQLite or cloud database storage
* 👤 User authentication
* 📑 Page-number citations for answers
* 🧠 Adaptive quizzes
* 🎙️ Voice input
* 🔊 Text-to-speech
* 📊 Student performance analytics
* 🌐 Cloud deployment
* 📈 Retrieval and answer-quality evaluation
* 🗂️ Persistent vector database such as FAISS-backed storage or another vector database

---

## 🎓 Academic Purpose

This project was developed as an academic AI project to demonstrate the complete development of an AI-powered application.

It demonstrates the integration of:

* Artificial Intelligence
* Natural Language Processing
* Semantic Search
* Vector Databases
* Retrieval-Augmented Generation
* Generative AI
* Web Interfaces
* Persistent Storage
* AI Application Design

---

## 👨‍💻 Project Summary

**AI StudyMate** transforms ordinary study documents into an interactive AI learning assistant.

```text
Study Material
      ↓
Understand
      ↓
Retrieve
      ↓
Generate
      ↓
Learn
```

> **Study Smarter, Not Harder.**

---

## 📄 Documentation

For the complete academic documentation, see:

```text
AI_StudyMate_Formal_Project_Document.docx
```

The document provides detailed information about the project architecture, implementation, testing, results, limitations, and future improvements.

---

## 🔐 Security Notice

This repository should **never contain**:

```text
Gemini API keys
Passwords
Private credentials
Personal study data
Private uploaded documents
```

Use environment variables, runtime input, or secret-management mechanisms when deploying the application.

---

## ⭐ Conclusion

AI StudyMate demonstrates a complete AI application pipeline from user input to intelligent processing and useful actions.

The project combines **semantic retrieval with Retrieval-Augmented Generation** to provide students with an interactive way to understand their own study material.

The implementation is intentionally kept within a single Google Colab notebook, making the project easy to run, demonstrate, test, and submit.
