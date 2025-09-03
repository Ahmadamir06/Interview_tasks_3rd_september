# Task B1: Document-Grounded Chatbot (LLM + File Upload)

## Goal

Build a small **web app** where a user **uploads a document** and asks questions.
Answers must be **grounded only in that uploaded document**; otherwise reply:
**“I couldn’t find that in the document.”**

---

## Requirements

* **UI:** file upload (.txt/.md), chat area, input box + “Ask” button.
* **Upload & index:** split text into chunks (≈150–250 words, small overlap).
* **Answering:** retrieve top-k chunks (k≈3–5), call OpenAI with **only** those chunks as context.
  Enforce grounding via prompt guardrails.
* **Output:** short answer (≤5 sentences) **with at least one citation** (chunk preview or line range).
* **Fallback:** if low similarity/no hit → “I couldn’t find that in the document.”
* **Limits & errors:** cap file size (e.g., 5–10 MB), handle bad files, empty input, API/network errors.

---

## Minimal API

**POST `/upload`** (multipart) →
Response:

```json
{ "docId": "abc123", "filename": "policy.txt", "size": 12345 }
```

**POST `/chat`** (JSON) →
Request:

```json
{ "docId": "abc123", "message": "How long is data retained?" }
```

Response:

```json
{
  "answer": "Data is retained for 90 days after account closure.",
  "citations": [
    { "chunkId": "c3", "preview": "…retained for 90 days after account closure…"}
  ]
}
```

---

## Prompt Guardrail (example)

> “Answer **only** using the provided context snippets.
> If the answer isn’t supported by the context, reply:
> ‘I couldn’t find that in the document.’ Be concise.”

---

## Run (example)

Backend (Python shown; any language is fine):

```bash
pip install fastapi uvicorn scikit-learn openai
export OPENAI_API_KEY=YOUR_KEY
uvicorn app:app --reload
```

Frontend: any (React/Vue/vanilla).
Flow: upload → get `docId` → call `/chat` with `docId` and question → render answer + citations.

---

## Acceptance Checklist

* [ ] Upload works; `.txt/.md` indexed into chunks.
* [ ] LLM answers **only from context**; every answer has a **citation**.
* [ ] Out-of-scope questions return **“I couldn’t find that in the document.”**
* [ ] Clean UI (file upload + chat), clear error messages
