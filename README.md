# RAG Notebook Lab

Notebook-first experiments for Retrieval-Augmented Generation (RAG): ingest local PDF/TXT files, chunk + embed them, persist to Chroma, then generate grounded answers with sources. Includes a separate Typesense notebook for lexical search / discovery.

## What’s here

- End-to-end RAG notebook: notebook/document.ipynb
- Typesense indexing + search experiments: typesense.ipynb
- Data folders:
  - data/pdf_files/ (your PDFs)
  - data/text_files/ (your TXT files)
  - data/vector_store/ (local Chroma persistence; usually not committed)

## Requirements

- Python >= 3.11
- A Groq API key (for generation in the RAG notebook)
- Optional: Typesense (if you want to run the Typesense notebook)

## Setup (Windows PowerShell)

Create and activate a venv:

```powershell
python -m venv .venv
\.venv\Scripts\Activate.ps1
```

Install dependencies:

```powershell
pip install -r requirements.txt
```

## Environment variables

Create a .env file in the repo root:

```env
GROQ_API_KEY=your_groq_api_key

# Only needed for typesense.ipynb
TYPESENSE_API_KEY=your_typesense_api_key
TYPESENSE_HOST=your_typesense_host
TYPESENSE_PORT=443
TYPESENSE_PROTOCOL=https
```

## Run

1. Put documents in data/pdf_files/ and/or data/text_files/
2. Open notebook/document.ipynb and run the cells top-to-bottom
3. (Optional) Open typesense.ipynb to index books.jsonl and run lexical searches

## Notes

- main.py currently prints a placeholder message; the primary workflow is the notebooks.
- Chroma persistence under data/vector_store/ can be large; it’s ignored by default in .gitignore.

	- Increase top_k.
	- Rebuild index after adding files.
- Stale or duplicated results:
	- Clear and rebuild data/vector_store.
- LLM errors:
	- Validate GROQ_API_KEY.
	- Confirm model availability in your Groq account.

---

Built as an experimentation lab for mastering practical RAG design with real retrieval behavior, observable outputs, and iterative notebook-driven development.
