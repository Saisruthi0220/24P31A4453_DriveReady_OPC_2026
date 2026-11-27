# PDF-Based Retrieval-Augmented Generation (RAG) Chatbot

## Project Overview

This project implements a Retrieval-Augmented Generation (RAG) chatbot that allows users to upload PDF documents and ask questions based on their content.

The system extracts text from PDF files, divides the text into smaller chunks, converts the chunks into vector embeddings, and stores them in a FAISS vector database. When a user asks a question, the system retrieves the most relevant information and uses the Groq API to generate an accurate, context-based response.

The chatbot is designed to answer questions using the uploaded document rather than relying on general knowledge.

## Features

- PDF document upload
- Text extraction using PyMuPDF
- Text chunking with overlapping sections
- Semantic embeddings using Sentence Transformers
- Vector similarity search using FAISS
- Context-based question answering
- Groq API integration
- Source page references
- Interactive question-answering through Google Colab
- Responses restricted to the retrieved document context

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Google Colab | Development environment |
| PyMuPDF | PDF text extraction |
| Sentence Transformers | Text embeddings |
| all-MiniLM-L6-v2 | Embedding model |
| FAISS | Vector database and similarity search |
| Groq API | Large Language Model integration |
| OpenAI Python SDK | API communication |
| NumPy | Numerical operations |

## System Architecture

1. **PDF Upload:** The user uploads a PDF document.
2. **Text Extraction:** PyMuPDF extracts text from the document.
3. **Text Chunking:** Extracted text is divided into smaller chunks.
4. **Embedding Generation:** Sentence Transformers converts chunks into numerical vectors.
5. **Vector Storage:** FAISS stores the generated embeddings.
6. **Question Processing:** The user submits a question.
7. **Information Retrieval:** FAISS retrieves the most relevant document chunks.
8. **Answer Generation:** Groq processes the retrieved context and generates an answer.
9. **Response:** The chatbot returns an answer based on the uploaded document.

## Installation

Install the required Python libraries:

```bash
pip install pymupdf sentence-transformers faiss-cpu openai numpy
```

## API Configuration

This project uses the Groq API.

1. Create an API key through the Groq Console.
2. Open Google Colab.
3. Navigate to Secrets.
4. Add your API key with the name `GROQ_API_KEY`.
5. Enable notebook access.

Example configuration:

```python
from google.colab import userdata
from openai import OpenAI

api_key = userdata.get("GROQ_API_KEY")

client = OpenAI(
    api_key=api_key,
    base_url="https://api.groq.com/openai/v1"
)
```

**Security:** Never upload your API key to GitHub or expose it in public code.

## Model Configuration

**Embedding Model:**
- all-MiniLM-L6-v2

**Language Model:**
- openai/gpt-oss-20b

**Vector Database:**
- FAISS IndexFlatIP

## Chunking Configuration

| Parameter | Value |
|---|---:|
| Chunk Size | 500 words |
| Chunk Overlap | 100 words |
| Retrieval Top K | 4 |
| Embedding Normalization | Enabled |

## Example Usage

**Uploaded Document:** Campus_Library_Guide.pdf

**Question:**
How many books can a student borrow?

**Expected Answer:**
Students may borrow up to four books at a time. The standard loan period is 14 days.

**Question:**
What is the late return fee?

**Expected Answer:**
A late fee of ₹2 per book per day applies to student loans.

**Question:**
Does the library provide free laptops?

**Expected Answer:**
The information is not available in the uploaded document.

## Project Structure

```text
PDF-RAG-Chatbot/
│
├── RAG-2.ipynb
├── Campus_Library_Guide.pdf
└── README.md
```

## Key Advantages

- Provides document-specific answers.
- Reduces the need to manually search lengthy PDF documents.
- Uses semantic similarity for relevant information retrieval.
- Keeps API credentials separate from source code.
- Can be extended to support multiple PDF documents.

## Future Enhancements

- Multiple PDF document uploads.
- Interactive chatbot user interface.
- Support for scanned PDFs using OCR.
- Conversation memory.
- Document-specific source citations.
- Support for different file formats such as DOCX and TXT.
- Improved retrieval using reranking techniques.

## Conclusion

This project demonstrates the implementation of a Retrieval-Augmented Generation pipeline by combining document processing, semantic search, vector databases, and Large Language Models.

It provides a practical approach to building an AI-powered document question-answering system using Python, FAISS, Sentence Transformers, and the Groq API.
