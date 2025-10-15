# AI Live Meeting Summarizer Application

## Project Overview

This project implements a real-time meeting summarization system using speech-to-text, speaker diarization, and LLM-based summarization. Delivered as a Streamlit web app, it allows live meeting recording, transcript generation, speaker tagging, and concise summary export to Markdown, PDF, or email.

---

## Project Milestones

### **Milestone 1: Speech-to-Text System**
- Real-time audio recording and STT (Vosk/Whisper)
- Threaded audio capture, WER benchmarking (jiwer)
- Output: real-time live transcript display

### **Milestone 2: Diarization & Summarization**
- Speaker diarization with pyannote.audio
- Diarized readable transcripts (Speaker 1/2 tags)
- Summarization with LLaMA (Groq), BART, or T5 (transformers)
- ROUGE scoring

### **Milestone 3: UI Integration**
- Streamlit-based frontend
- Start/Stop controls, live log and results viewer
- Backend pipeline: queue transcript → diarization → summary after stop

### **Milestone 4: Output, Docs, and Packaging**
- Download transcripts and summaries (.md, .pdf)
- Email send-out with meeting summary
- Session history and logging (JSON/Parquet)
- Full documentation and demo-ready packaging

---

## Features

- **Real-time recording** and speech-to-text
- **Speaker diarization:** Who said what, when
- **Concise summaries** using open LLMs (Groq, Hugging Face)
- **One-click export:** Markdown/PDF/email
- **Session saving:** JSON/parquet logs for offline analysis
- **Configurable:** Choose STT, summarizer models, chunk sizes
- **Responsive Streamlit UI**

---

## Tech Stack

| Area                 | Tools/Libraries                              |
|----------------------|----------------------------------------------|
| STT                  | Vosk, Whisper, pyaudio, sounddevice          |
| Diarization          | pyannote.audio, torchaudio                   |
| Summarizer           | LLaMA 3.1 (Groq), T5, BART (HuggingFace)     |
| Frontend             | Streamlit                                    |
| Backend              | Python threading, asyncio, queue             |
| Evaluation           | jiwer (WER), rouge_score, BLEU               |
| Export/Logging       | Pandas, reportlab, smtplib, JSON, Parquet    |

---

## Setup and Run

1. **Clone the repository & enter the folder:**
git clone <your_repo_url>
cd <repo_dir>

text

2. **(Optional) Create and activate a virtual environment:**
python -m venv .venv

On Windows:
.venv\Scripts\activate

On Linux/Mac:
source .venv/bin/activate

text

3. **Install dependencies:**
pip install -r requirements.txt

text

4. **Set up Hugging Face and Groq API keys:**
- Add them to `.env` in the project root, or set as environment variables.
- Example `.env`:
  ```
  GROQ_API_KEY=your_key_here
  HF_TOKEN=your_hf_token_here
  ```

5. **Run the app:**
streamlit run app.py

text

---

## Folder Structure (Recommended)

project-root/
├── app.py
├── summarization.py
├── summary.py
├── ... (utility scripts)
├── requirements.txt
├── README.md
├── dataset/ # optional, small test audio
├── sessions/ # saved session output
├── Evaluation report/
├── model/ # NOT included in repo; instruct users to download
├── stt_outputs/
├── ...

text

---

## Notes

- Large models and datasets should not be committed—provide links/instructions in README.
- Email integration requires SMTP settings.
- For production, ensure secrets are handled securely (e.g. `st.secrets`).

## Demo

- UI walkthrough, export/download, summary email.
- Example input: AMI corpus snippet, meeting clip, etc.

---

## Citation/Evaluation

| Milestone | Metric          | Target     |
|-----------|-----------------|-----------|
| 1 (STT)   | WER (jiwer)     | < 15%     |
| 2 (Diar/Summ)| ROUGE, DER   | ROUGE > 0.4, DER < 20% |
| 3 (UI)    | Responsiveness  | No lag    |
| 4 (Final) | Export, email   | Works/complete |

---

##📊 Final Summary Report
Total files processed : 16

Average WER (Whisper vs GT)   = 50.71%

Average WER (Vosk vs GT)      = 68.60%

Average WER (Vosk vs Whisper) = 56.25%

Overall Better STT             = Whisper ✅ Better on average

## License

[MIT License](LICENSE) or similar.
