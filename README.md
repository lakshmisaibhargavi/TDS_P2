# Update README with detailed project overview and steps used
readme_content = """# TDS Solver - IITM Project 2 (Final Version)

This project is a complete solution to **Project 2 - TDS Solver** for the **Tools in Data Science** course from the **IIT Madras Online BSc in Data Science** program.

It provides a FastAPI backend deployed via Vercel that can:
- Accept assignment questions
- Accept a ZIP file containing a CSV
- Automatically extract the answer from the CSV
- Use an LLM (GPT-3.5) via **AIProxy** (provided by IITM) to answer general questions

---

## 📦 Tech Stack Used

- **FastAPI** for building the backend API
- **Uvicorn** for local development server
- **pandas** for handling CSVs
- **Python `zipfile` and `tempfile`** for file handling
- **OpenAI GPT-3.5** via `https://api.aiproxy.io` using IITM-issued API token
- **Dotenv** for securely loading API keys
- **Vercel** for deployment

---

## ⚙️ How It Works

1. If the question includes a ZIP file:
   - The server extracts the file
   - Reads the CSV inside
   - Returns the value from the `answer` column

2. If no file is included:
   - The question is sent to GPT-3.5 via AIProxy
   - The response is returned as the answer

---

## 🔐 Authentication

The API uses a secret `AIPROXY_TOKEN` provided by IITM, stored in `.env`.

Example `.env`:


---

## 🚀 Run Locally

1. Clone this repo and unzip if downloaded
2. Install dependencies:

bash
pip3 install -r requirements.txt

Start the server:

uvicorn app.main:app --reload

Test the API:

curl -X POST "http://127.0.0.1:8000/" \
  -H "Content-Type: multipart/form-data" \
  -F "question=Download and unzip q-extract-csv-zip.zip. What is the value in the 'answer' column?" \
  -F "file=@tests/q-extract-csv-zip.zip"

{"answer":"e70d8"}
