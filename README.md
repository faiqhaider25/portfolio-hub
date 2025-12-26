# 🚀 Automated Portfolio Hub

Welcome to the **Portfolio Hub**! This repository serves as the deployment target for an automated "Prompt-to-Live-App" workflow.

**Project Developers:**

- **Syed Faiq Haider Naqvi** (2022562)
- **Hasan Abbas** (2022204)

---

## 📖 About The Project

This project leverages Low-Code automation and Generative AI to eliminate the manual coding required for personal portfolios. Users simply upload their resume and a design prompt via a web form, and the system autonomously architects, codes, and deploys a live website in under 2 minutes.

## 🤖 System Architecture & Workflow

The pipeline runs on a local **Dockerized n8n** instance exposed to the public internet via **ngrok**.

1.  **Ingestion (ngrok Tunnel):**

    - Users submit a form (Resume PDF + Style Prompt) via a public URL provided by ngrok.
    - This tunnels the data securely to our local n8n container running on port `5678`.

2.  **AI Processing (RAG-Lite):**

    - **Extraction:** The workflow parses text from the uploaded PDF.
    - **Generation:** Google Gemini (PaLM), orchestrated via LangChain, generates a single-file HTML website using Tailwind CSS based on the user's stylistic prompt.

3.  **Deployment (GitOps):**

    - The system creates a unique "slug" from the user's email (e.g., `user@gmail.com` -> `user-gmail-com`).
    - The generated code is automatically committed and pushed to a new folder in this repository via the GitHub API.

4.  **Delivery:**
    - **Wait Node:** The workflow pauses for 60 seconds to allow GitHub Pages to build the site.
    - **Notification:** The user receives an email containing their live link (e.g., `https://faiqhaider25.github.io/portfolio-hub/user-slug/`).

## 📂 Directory Structure

To support multi-tenancy, each user gets a dedicated directory based on a sanitized version of their email:

```text
/
├── README.md           <-- Project Documentation
├── index.html          <-- Main landing page for the hub
├── john-doe-gmail-com/
│   └── index.html      <-- John's generated Portfolio
└── jane-smith-gmail-com/
    └── index.html      <-- Jane's generated Portfolio
```

## 🛠️ Tech Stack

- **Orchestration:** n8n (Docker Container)
- **Network Tunneling:** ngrok (Exposing localhost webhook)
- **AI Model:** Google Gemini (PaLM) via LangChain
- **Styling:** Tailwind CSS (CDN)
- **Hosting:** GitHub Pages
- **Notification:** SMTP (Gmail)

## 🐳 Local Deployment Command

The core workflow engine is hosted using the following Docker configuration:

```bash
docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -v ~/.n8n:/home/node/.n8n \
 docker.n8n.io/n8nio/n8n
```

## ⚠️ Important Notes

This repository is managed by an automated bot. Manual edits to user folders may be overwritten by the deployment pipeline.

```

```
