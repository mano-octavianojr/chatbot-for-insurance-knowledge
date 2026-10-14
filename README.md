# Chatbot for Insurance Knowledge

A beginner-friendly, hands-on tutorial for building insurance education chatbots with Python and Jupyter notebooks. Start with a text-based chatbot using only built-in Python, then progress to the Gemini API, retrieval-augmented generation (RAG), structured outputs, and tool calling.

Each lesson is a standalone notebook with explanations, runnable examples, checks, and exercises. Run them in Google Colab without configuring a local development environment. All insurance policies and calculations are fictional educational examples; they do not establish actual coverage or claim eligibility.

## Lessons

| Notebook | Python / AI focus | Run online |
| --- | --- | --- |
| [01 — Quick Text-Based Chatbot](notebooks/01_rule_based_chatbot.ipynb) | Dictionaries, strings, keyword matching, functions, loops | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mano-octavianojr/chatbot-for-insurance-knowledge/blob/main/notebooks/01_rule_based_chatbot.ipynb) |
| [02 — Gemini API Chatbot](notebooks/02_gemini_api_chatbot.ipynb) | API requests, system instructions, conversation history | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mano-octavianojr/chatbot-for-insurance-knowledge/blob/main/notebooks/02_gemini_api_chatbot.ipynb) |
| [03 — RAG Insurance Chatbot](notebooks/03_rag_insurance_chatbot.ipynb) | Document chunks, embeddings, cosine similarity, retrieval, citations | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mano-octavianojr/chatbot-for-insurance-knowledge/blob/main/notebooks/03_rag_insurance_chatbot.ipynb) |
| [04 — Structured Outputs and Tools](notebooks/04_structured_outputs_and_tools.ipynb) | JSON schemas, validation, function calling, deterministic calculations | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mano-octavianojr/chatbot-for-insurance-knowledge/blob/main/notebooks/04_structured_outputs_and_tools.ipynb) |

The badges use Google's Colab logo and open the corresponding GitHub notebook. **They will work once these files are pushed to this repository's `main` branch.** Colab edits are made in your session; save a copy to Google Drive if you want to retain your work.

## Get started

1. Open lesson 1 using its Colab badge and connect to a Python runtime. No GPU is needed.
2. Run cells from top to bottom. Interactive chat loops are opt-in: uncomment `chat()` when ready, then type `exit` to stop.
3. For lessons 2–4, create a Gemini API key in [Google AI Studio](https://aistudio.google.com/apikey).
4. In Colab, open **Secrets** (the key icon), add a secret named `GEMINI_API_KEY`, and enable notebook access. Never paste a key into a notebook or commit it to Git.
5. Run the SDK installation and connection cells, then the examples. Each AI example sends requests to Google.

Gemini has a free tier for eligible models, accounts, and regions, but it is not unlimited or guaranteed for every model. Check [current pricing](https://ai.google.dev/gemini-api/docs/pricing), [rate limits](https://ai.google.dev/gemini-api/docs/rate-limits), and the API's data-use terms. Do not send personal, medical, confidential, or real policy information in these exercises.

The notebooks use `gemini-flash-latest` for generation and `gemini-embedding-001` for RAG embeddings. The generation alias follows Google’s latest Flash model and may change behavior, quotas, or pricing over time. Change the model constants if these models are unavailable for your account. The alias does not guarantee free-tier access. Lesson 1 needs no libraries; lessons 2–4 install the official `google-genai` SDK. RAG uses built-in Python math and an in-memory index, with the sample document included directly in the notebook.

## Learning path

- **Lesson 1:** Build predictable rules and observe their limits with unfamiliar wording.
- **Lesson 2:** Generate flexible answers and remember conversation context. Discuss hallucinations and token usage.
- **Lesson 3:** Retrieve policy passages before answering, cite sources, and recognize missing information. RAG still uses an AI API; it adds a document-grounding step.
- **Lesson 4:** Produce machine-readable answers and delegate calculations to Python. Explore hybrid retrieval, local models, and fine-tuning as optional follow-on topics rather than implemented lessons.

## Run locally (optional)

Use Python 3.10 or newer. From the repository directory:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install jupyterlab 'google-genai>=2.0,<3.0'
jupyter lab
```

On Windows, activate with `.venv\Scripts\activate`. Set `GEMINI_API_KEY` through your shell or development environment's secure secret handling before launching Jupyter. The notebooks read it from the environment outside Colab.

## Checks and troubleshooting

Lesson 1 includes four rule-behavior checks. Lesson 3 checks that retrieval finds the claim-deadline section; manually inspect generated answers and citations too. Lesson 4 includes three offline calculator checks, JSON type checks, and an assertion that the model actually called the calculator.

API outputs vary, and a valid JSON response or citation is not proof that an answer is correct. Compare answers against the fictional source text and Python calculation.

- **Missing key:** check the secret name and notebook access toggle.
- **Authentication error:** verify that your key has access to the Gemini API.
- **Model unavailable:** choose a supported model and update the notebook constant.
- **Quota error (429):** wait or reduce requests; review your account's limits.
- **After restarting a runtime:** rerun installation, connection, and data/index cells in order.

## Validation status

Notebook JSON, Python syntax, lesson 1 behavior checks, and lesson 4 offline calculator checks were validated during creation. Live Gemini requests, embedding retrieval, structured responses, and automatic tool calling require a key and have not been executed during creation. Google Colab runtime execution has not been independently verified.

## SDK and model references

The tutorials require `google-genai>=2.0,<3.0` and use `gemini-flash-latest`, following [Google’s official Python SDK examples](https://github.com/googleapis/python-genai#readme). Consult the [model catalog](https://ai.google.dev/gemini-api/docs/models) and [deprecation schedule](https://ai.google.dev/gemini-api/docs/deprecations) when selecting a fixed model version.
