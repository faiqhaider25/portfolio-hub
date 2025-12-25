# 🚀 Automated Portfolio Hub

Welcome to the **Portfolio Hub**! This repository serves as the deployment target for an automated "Prompt-to-Live-App" workflow.

## 🤖 How It Works

1.  **Input:** Users submit their resume via a web form.
2.  **Processing:** An n8n workflow parses the PDF and uses an LLM to generate a custom, single-page portfolio.
3.  **Deployment:** The generated `index.html` is automatically pushed to a unique folder in this repository.
4.  **Live:** GitHub Pages serves the content instantly.

## 📂 Directory Structure

Each user gets a dedicated directory based on a sanitized version of their email:

```text
/
├── README.md           <-- You are here
├── index.html          <-- Main landing page for the hub
├── john-doe-gmail-com/
│   └── index.html      <-- John's Portfolio
└── jane-smith-gmail-com/
	└── index.html      <-- Jane's Portfolio
```

## 🛠️ Tech Stack

- **Workflow Automation:** n8n
- **AI Model:** OpenAI GPT-4o
- **Styling:** Tailwind CSS (CDN)
- **Hosting:** GitHub Pages

This repository is managed by an automated bot. Manual edits to user folders may be overwritten.
