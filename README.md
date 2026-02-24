# AI-Powered Academic RAG Study Assistant  
## Database Management Systems (DBMS)

This project implements a Retrieval-Augmented Generation (RAG) based AI study assistant for the subject **Database Management Systems (DBMS)**.

The assistant answers academic questions strictly using the provided course materials (PDF lecture notes and textbooks). The system was built as part of an AI/ML academic assignment and demonstrates a complete ML lifecycle including:

- Data collection and analysis  
- Baseline RAG implementation  
- Controlled experimentation  
- Evaluation using defined metrics  
- System optimization  
- Reflection and production-ready configuration  

The focus of this project is on ML experimentation and analysis rather than frontend or deployment infrastructure.

---

# 📌 Project Overview

The study assistant:

1. Processes DBMS PDF documents.
2. Extracts and cleans text.
3. Splits text into chunks.
4. Generates embeddings.
5. Stores vectors in a local vector database (ChromaDB).
6. Retrieves relevant context using similarity search.
7. Generates answers using an open-source LLM.
8. Evaluates performance using structured metrics.
9. Compares different design choices (chunking, prompting, retrieval depth).

---

academic-rag-study-assistant/
│
├── data/                               
│
├── notebook/                           
│   ├── RAG-Study-Assistant.ipynb        
│   └── Experiment-Result-Markdown.ipynb    
│  
├── rag_env/                             
│  
├── .env                                 
├── .gitignore                           
│  
├── experiment_results.md               
├── README.md                            
├── requirements.txt                     
│
├── RAG-Study-Assistant.pdf                
└── Sample-Questions-Answers-Result.pdf   


---

# ⚙️ Prerequisites

- Python 3.9 or higher
- Jupyter Notebook or VS Code
- Minimum 8GB RAM recommended
- Internet connection

---

# 📦 Dependencies

Install all required libraries using:

pip install -r requirements.txt


If installing manually:

pip install langchain
pip install chromadb
pip install sentence-transformers
pip install transformers
pip install pdfplumber
pip install python-dotenv
pip install matplotlib
pip install pandas


---

# 🔐 API Keys

This project primarily uses **open-source transformer models** (e.g., FLAN-T5 ).

No OpenAI API key is required.

If switching to OpenAI:

1. Create a `.env` file in the root directory.
2. Add:
OPENAI_API_KEY=your_api_key_here


3. Load it using `python-dotenv`.

---

# ▶️ How to Run the Project

### Step 1: Clone Repository
git clone https://github.com/VaibhavChougule236/academic-rag-study-assistant.git


### Step 2: Add Course Materials

Place your DBMS PDF documents inside the `data/` folder.

### Step 3: Launch Jupyter Notebook


Open `RAG-Study-Assistant.ipynb` and run cells sequentially.

---

# 🧠 What the Notebook Covers

The notebook is structured according to assignment requirements:

## Part 1 – Data Collection & Understanding
- Analysis of PDF structure
- Identification of formatting challenges
- Description of dataset characteristics

## Part 2 – Baseline RAG Implementation
- Text extraction
- Fixed chunking
- Embedding generation
- Vector storage (ChromaDB)
- Basic retrieval + answer generation

## Part 3 – Experimentation & Comparison
- Chunking strategy comparison
- Prompt engineering comparison
- Retrieval depth (Top-k) comparison
- 3-metric evaluation (Relevance, Correctness, Completeness)
- Graph-based visualization
- Retrieval vs generation error analysis

## Part 4 – Handling Real-World Challenges
- Noise removal in PDF extraction
- Table and SQL formatting distortion handling
- Before/after examples
- Trade-off discussion

## Part 5 – Final Production Configuration & Reflection
- Selected optimal system design
- Reflection on failures and improvements
- Cost analysis
- ML lifecycle insights

---

# 📊 Evaluation Methodology

Each experiment was evaluated using:

- **Relevance (1–5)** – Does answer match question?
- **Correctness (1–5)** – Is information accurate?
- **Completeness (1–5)** – Is explanation sufficient?

Graphs are generated inside the notebook for visual comparison.

---

# 🧪 Experiments Conducted

### Experiment 1 – Chunking Strategies
- Fixed-size chunking
- Sentence-based chunking

### Experiment 2 – Prompt Engineering
- Basic prompt
- Structured improved prompt

### Experiment 3 – Retrieval Strategy
- Top-k = 3
- Top-k = 5
- Top-k = 8

Each experiment includes:
- Methodology
- Results table
- Observations
- Pros & cons
- Final decision rationale

Full details available in:
Experiment-Result-Markdown.ipynb


---

# 📈 Expected Output

When running the notebook, you will see:

- Raw and cleaned text samples
- Retrieved chunks for test questions
- Generated answers
- Evaluation scores
- Bar charts comparing experiments
- Final system configuration summary
- Generated `evaluation_results.csv` file

---

# 🏆 Final Production Configuration

Based on systematic experimentation:

- Sentence-based chunking
- Improved structured prompt
- Top-k = 3 retrieval
- Text preprocessing enabled
- Open-source transformer model

This configuration achieved the highest average relevance and completeness scores.

---

# 💡 Key Learnings

- Chunking strategy significantly affects semantic retrieval.
- Prompt engineering directly impacts answer completeness.
- Increasing retrieval depth can introduce noise.
- Preprocessing improves embedding quality.
- RAG systems require tuning at every stage.

---

# 🚀 Future Improvements

If developed further:

- Hybrid search (semantic + keyword)
- Layout-aware PDF parsing
- Re-ranking model
- Stronger LLM (Llama 3 / GPT-4)
- Automated evaluation metrics (BLEU / ROUGE)

---

# 🧾 Academic Integrity Note

All code was implemented individually as part of an AI/ML academic assignment.  
Experiments and conclusions are based on observed results and documented analysis.

---

# 👨‍💻 Author

Developed as part of AI/ML Assignment for building a practical RAG-based academic study assistant.

---



