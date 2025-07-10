**AI-Powered Medical Chatbot using LLaMA3, Groq, Pinecone & LangChain**

Project Summary:

This project is an AI-powered Medical Chatbot that answers health-related questions based on trusted medical literature, specifically the "Gale Encyclopedia of Medicine (2nd Edition)." It uses a Retrieval-Augmented Generation (RAG) pipeline with LangChain, Groq's LLaMA3-70B, HuggingFace Embeddings, and Pinecone Vector DB to retrieve contextually relevant answers from a vectorized PDF dataset.

This chatbot does not hallucinate — it only answers from the indexed medical document context.

Demo:

Example Query:
User: "What is Acne?"
Response: Identifies acne as a symptom of CAH (Congenital Adrenal Hyperplasia) from the indexed content.

Tech Stack:

* Groq (LLaMA3-70B) for LLM
* HuggingFace Sentence Transformers for embeddings
* Pinecone for vector database (serverless)
* LangChain for RAG framework
* Flask for backend
* HTML + CSS for frontend UI
* Source Document: Gale Encyclopedia of Medicine (2nd Edition)
* Document chunking: 20,000+ text chunks embedded and stored

How It Works:

1. User inputs a medical question.
2. Retriever (Pinecone) fetches top-k similar chunks from the document.
3. LangChain builds a prompt with those chunks.
4. LLaMA3-70B (via Groq API) generates an answer using ONLY that context.
5. Final response is returned through a Flask-based UI.

Project Structure:

* app.py: Flask app to serve the chatbot
* store\_index.py: Loads PDF, chunks, embeds, and indexes into Pinecone
* src/

  * helper.py: Utility functions for PDF parsing, chunking, embedding
  * prompt.py: Prompt template for the LLM
* Data/

  * medical\_book.pdf: Your indexed source file (Gale Encyclopedia of Medicine)
* templates/

  * chat.html: Chat UI
* static/

  * style.css: CSS styling
* requirements.txt
* README.md

Setup Instructions:

1. Clone the Repository:
   git clone [https://github.com/yourusername/medical-chatbot](https://github.com/nawafmir/medical-chatbot)
   cd medical-chatbot

2. Install Dependencies:
   pip install -r requirements.txt

3. Add Your .env File:
   Create a `.env` file in the root directory:
   PINECONE\_API\_KEY=your\_pinecone\_key
   PINECONE\_ENV=your\_region (e.g., us-east-1)
   GROQ\_API\_KEY=your\_groq\_key

4. Index the Medical PDF:
   python store\_index.py

5. Run the Web App:
   python app.py

   Visit [http://localhost:8080](http://localhost:8080) in your browser.

Data Source:

This chatbot is trained on:
The Gale Encyclopedia of Medicine, Second Edition
This is a comprehensive medical reference used here solely for educational and demo purposes.

Example Use Case:

Query: What is acne?
Retrieved Answer: Acne is not explicitly defined in the context but is mentioned as a symptom of Congenital Adrenal Hyperplasia (CAH). It is a common skin condition characterized by pimples, blackheads, and clogged pores.

Future Improvements:

* Add citations to each response
* Support multi-document ingestion
* Improve UI/UX with Streamlit or React
* Enable PDF file upload by users
* Add real-time feedback/ratings to improve relevance

Author:

Nawaf Mir Mohammed
LinkedIn:(https://www.linkedin.com/in/nawafmir)
Email: nawafmeer17@gmail.com

Acknowledgments:

* LangChain
* Groq LLM API
* Pinecone Vector DB
* HuggingFace Transformers
* Flask Community


