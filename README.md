# Feedback AI Tool

A web-based document analysis platform for academic writing feedback, built with Python and Flask.

---

## Starting the Development Server

```bash
python app.py
```

The application will be available at `http://127.0.0.1:5000` in your browser.

---

## Dependencies

Make sure the following are installed before running the application:

- [Python 3.8+](https://www.python.org/)
- [Java JDK/JRE](https://www.java.com/en/download/) — **required** for LanguageTool (see note below)
- Flask
- python-docx
- PyPDF2
- language-tool-python

---

## Installation

Install each dependency:

```bash
pip install flask
pip install python-docx
pip install PyPDF2
pip install language-tool-python
```

---

## Analysis Functions

The application contains seven core analysis functions, each with a docstring describing its parameters, return type, and behaviour. You should be able to understand what each function does without needing to read the full implementation.

| Function | Description |
|---|---|
| `clean_text()` | Normalises extracted text — standardises line endings, collapses whitespace, strips leading/trailing characters |
| `get_metrics()` | Computes word count, sentence count, paragraph count, and average sentence length |
| `get_repeated_words()` | Identifies words (4+ letters) appearing 5 or more times in the document |
| `get_structure_feedback()` | Applies heuristic rules to assess paragraph count and sentence length thresholds |
| `get_content_feedback()` | Checks for the presence of key academic section keywords |
| `get_grammar_feedback()` | Runs LanguageTool grammar and spelling analysis on the full document text |
| `get_overall_feedback()` | Aggregates results from all functions into a score out of 100 |

---

##  Java Requirement

LanguageTool runs on the Java Virtual Machine (JVM). **Java must be installed on the host system** for grammar checking to work.

You can verify your Java installation by running:

```bash
java -version
```

If Java is not installed, download it from [java.com](https://www.java.com/en/download/)

---

## Supported File Formats

- `.txt` — Plain text
- `.docx` — Microsoft Word
- `.pdf` — PDF (digital/text-based only; scanned PDFs are not supported)

---

## Notes

- Session history is stored **in memory only** and will be cleared when the server restarts.
- For production deployment, replace the Flask development server with a WSGI server such as [Gunicorn](https://gunicorn.org/).
