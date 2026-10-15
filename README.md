# 📄 ATS Resume Checker

A Streamlit app that scores a resume for Applicant Tracking Systems (ATS) and gives specific, prioritized improvements using Google Gemini Flash.

## Features
- Upload a resume as **PDF, DOCX or TXT**
- Optional **job description** for a more accurate keyword score
- **ATS score (0-100)** with a breakdown: keywords, sections, impact, formatting, readability
- Strengths, weaknesses, **missing keywords**
- Prioritized **improvement suggestions** and **before/after rewrite examples**
- Quick rule-based checks (email, phone, LinkedIn, word count, standard sections)

## Run locally

```bash
# 1. Clone and enter the project
git clone https://github.com/<your-username>/ats-resume-checker.git
cd ats-resume-checker

# 2. (Recommended) create a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Add your Gemini API key (get one free at https://aistudio.google.com/apikey)
mkdir .streamlit
echo 'GEMINI_API_KEY = "your-key-here"' > .streamlit/secrets.toml

# 5. Run
streamlit run app.py
```

You can also set the key as an environment variable (`GEMINI_API_KEY`) or paste it into the app's sidebar.

## Configuration

| Setting | Where | Purpose |
|---|---|---|
| `GEMINI_API_KEY` | `.streamlit/secrets.toml` or env var | Your Gemini API key |
| `GEMINI_MODEL` | env var (optional) | Override the model (default: `gemini-3.5-flash`) |

## Deploy on Streamlit Community Cloud

1. Push this repo to GitHub (never commit `.streamlit/secrets.toml`).
2. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
3. Click **Create app**, choose your repo, branch `main`, and main file `app.py`.
4. Open **Advanced settings → Secrets** and paste:
   ```toml
   GEMINI_API_KEY = "your-key-here"
   ```
5. Click **Deploy**.

## Notes
- Scanned (image-only) PDFs have no extractable text. Use a text-based PDF or DOCX.
- The ATS score is an AI-based estimate, not the output of a real employer's ATS. Use it as guidance.
- Resumes are sent to the Gemini API for analysis. Don't upload anything you aren't comfortable sharing.
