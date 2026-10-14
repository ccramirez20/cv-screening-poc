# cv-screening-poc

Personal prototype: LLM-assisted résumé screening. **All data is synthetic** (the sample PDFs in `src/data/` are fictional candidates). Not affiliated with any company and not a production system.

## What it does
1. Upload one or more PDF résumés.
2. Text is extracted (PyPDF2) and an LLM structures it into JSON: experience, education, languages, skills.
3. Companies mentioned are checked against Wikipedia as a basic existence check.
4. An LLM compares each profile with a job description and returns a compatibility %, strengths and gaps.
5. A chat assistant answers questions about the processed candidates.

## Stack
Python · FastAPI · OpenAI API · PyPDF2 · Wikipedia API · plain HTML/CSS/JS frontend.

## Run locally
```bash
cd src
pip install -r requirements.txt
echo "OPENAI_API_KEY=your_api_key" > .env
python main.py   # http://localhost:8000
```

## Limitations
- The target job profile is hardcoded (`descripcion_puesto` in `src/main.py`).
- Compatibility scores come from an LLM and have not been validated against human recruiters; do not use them for real hiring decisions.
- Wikipedia lookup is a weak legitimacy check (false negatives for small companies).
- No tests, no auth, no PII handling: demo only.

## License
MIT
