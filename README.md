# 🛡️ Insurance MCQ Quiz (Gradio + Gemini)

A Gradio chat app that generates multiple-choice quizzes on Indian insurance topics. After you pick an option, it tells you whether you were right or wrong, and **only if you were wrong** it explains the correct answer in 1-2 lines.

## Features

- **Pre-loaded subjects:** choose one or more of the IC study PDFs (IC-01, IC-02, IC-11, IC-14, IC-38, IC-67, IC-72, IC-74, IC-85). For the demo, only IC-01 is pre-loaded.
- **Your own material:** upload PDF/TXT/MD files and/or paste text to be quizzed on it.
- **Focus area:** type a free-text area (e.g. "exclusions"). If subjects are selected and random is unticked, questions come only from those subjects, focused on that area where possible.
- **Random questions:** optionally include general insurance questions generated from the model's knowledge.
- **Scoring:** running score and no repeated questions in a session.

## Requirements

- Python 3.10+
- A Google Gemini API key
- Load other IC series pdfs and update the list in the code.

## Setup

```bash
pip install -r requirements.txt
```

Create a file named `.env` in the project folder (do not share or upload it):

```
GOOGLE_API_KEY=your_gemini_api_key_here
```

## Configure file paths

At the top of `app.py`, update these to match your machine:

```python
DEFAULT_PDF = r"<path-to>\IC01 Principles of Insurance.pdf"
DEFAULT_SUMMARY = r"<path-to>\summary.txt"
```

The other subject PDFs are read from the same folder as `DEFAULT_PDF`, using the file names listed in the `SUBJECTS` dictionary.

## Run

```bash
python app.py
```

Then open the local URL shown in the terminal (usually http://127.0.0.1:7860).

## How to use

1. Select subject(s), and/or upload documents, and/or paste text.
2. Optionally tick **Include random insurance questions from the Web** and/or type a specific area.
3. Click **Next question**, then choose A, B, C or D.
4. Click **Next question** to continue, or **Reset quiz** to start over.

## Settings you may want to change

| Setting | Where | Purpose |
|---|---|---|
| `MODEL` | top of the script | Gemini model used |
| `MAX_CONTEXT_CHARS` | top of the script | Size of the document excerpt sent per question |
| `SUBJECTS` | top of the script | Subject names and PDF file names |

## Notes

- The "random questions" option uses the model's general knowledge; it does not perform a live web search.
