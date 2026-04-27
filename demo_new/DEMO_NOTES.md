# Demo notes (presenter-friendly)

## Demo 1 — FGSM adversarial example (`demo_fgsm_adversarial.ipynb`)

- **Goal**: show that a tiny, often imperceptible perturbation can flip a classifier’s prediction.
- **Setup**: run on **GPU** for speed (Colab or local).
- **Default image**: a **traffic sign** photo (self-driving analogy).

## Demo 2 — Indirect prompt injection via poisoned PDF (`demo_indirect_injection.pdf`)

### What it demonstrates

The PDF contains **normal visible text** plus **hidden machine-extractable instructions** (white-on-white at tiny font size). When an LLM ingests the PDF, it may follow the hidden instructions as if they were legitimate.

### How to run it (safe classroom flow)

1. **Show the PDF normally** in a viewer (looks like a boring internal safety report).
2. Upload the PDF to an LLM and ask something benign, e.g.:
   - “Please summarize this safety report.”
3. Point out that the model may inject an **emergency recall + link** that is *not* in the visible content.
4. Discuss why this is dangerous in real workflows (RAG, email copilots, ticket summarizers, document search).

### Safety framing / disclaimer

- This is for **education and defense** (prompt-injection awareness).
- Do **not** use real phishing links; the demo uses an `example.com`-style domain.
- Treat retrieved content as **untrusted input**; apply tool allowlists, least privilege, and human confirmation for high-impact actions.

### Quick verification (optional)

If you want to confirm the hidden text is extractable, open the PDF and copy/paste the text or run a text extraction tool; you should see the hidden `[SYSTEM] ...` instruction appear in extracted text even though it’s not visible.

