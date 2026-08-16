# 🤖 AI Social Media Agent

An AI-powered social media automation agent with a custom frontend UI. Submit your project details, let AI generate a post, review and edit it, then publish to LinkedIn, Instagram, X and Threads simultaneously — all from one place.

---

## 📸 Screenshots

### Frontend UI
![Frontend](<img width="1536" height="1024" alt="afc4fcf6-5e71-4eb8-a1b7-2b590ce53be2" src="https://github.com/user-attachments/assets/8e4007ce-13a2-49ff-8d2a-aa620d2ad4bf" />
)

### n8n Workflow
![Workflow](<img width="1625" height="730" alt="image" src="https://github.com/user-attachments/assets/20cc98a5-a6c3-41e2-ada9-ee8811e181e4" />
)

---

## ✨ Features

- **Two post creation modes** — AI generation from project details or write your own custom post
- **AI-powered content generation** — Turns raw project info into a ready-to-publish social media post
- **Human review before publishing** — Edit, accept or reject the post before anything goes live
- **Multi-platform publishing** — One approval posts to LinkedIn, Instagram, X and Threads simultaneously
- **Real-time platform status** — See Posted or Error for each platform independently
- **Two-level error handling** — Platform-level errors are reported separately. Workflow-level errors trigger a Gmail notification with full details
- **Custom frontend UI** — No need to touch the n8n editor. Full flow from create to results happens in the UI

---

## 🛠️ Tech Stack

- **n8n** — Workflow automation
- **Groq** — AI post generation (primary)
- **Google Gemini** — AI fallback model
- **upload-post.com** — Instagram, X and Threads publishing API
- **LinkedIn API** — Direct LinkedIn posting via n8n node
- **Gmail** — Error notification delivery

---

## 📁 Project Structure

```
ai-social-media-agent/
│
├── frontend/
│   └── index.html          # Custom frontend UI
│
├── workflows/
│   ├── main-workflow.json          # Main n8n workflow
│   └── error-trigger-workflow.json # Error handling workflow
│
├── assets/
│   ├── workflow-screenshot.png
│   └── frontend-screenshot.png
│
└── README.md
```

---

## ⚙️ Setup Instructions

### Prerequisites
- n8n self-hosted (Docker recommended)
- Groq API key — [console.groq.com](https://console.groq.com)
- Google Gemini API key — [aistudio.google.com](https://aistudio.google.com)
- LinkedIn OAuth credentials — [Linkedin developer](https://developer.linkedin.com)
- upload-post.com account and API key — [upload-post.com](https://upload-post.com)
- Gmail OAuth credentials — via Google Cloud Console

### Step 1 — Import workflows
1. Open your n8n instance
2. Go to **Workflows → Import**
3. Import `main-workflow.json`
4. Import `error-trigger-workflow.json`

### Step 2 — Set up credentials
Add the following credentials in n8n:
- **Ollama** — local Ollama instance URL
- **Google Gemini** — your Gemini API key
- **LinkedIn OAuth2** — client ID and secret from Google Cloud Console
- **Gmail OAuth2** — client ID and secret from Google Cloud Console

### Step 3 — Configure upload-post.com
In the HTTP Request nodes for X, Instagram and Threads:
- Replace `YOUR_UPLOAD_POST_API_KEY` with your API key
- Replace `YOUR_UPLOAD_POST_USERNAME` with your username

### Step 4 — Set up frontend
1. Open `frontend/index.html`
2. Update the webhook URL to match your n8n webhook URL
3. Open the file in your browser

### Step 5 — Activate workflows
1. Activate the error trigger workflow first
2. Activate the main workflow
3. Open the frontend and test

---

## 🔄 How It Works

```
User opens frontend
        ↓
Choose: Generate Post or Custom Post
        ↓
If Generate: Fill project details → AI writes post
If Custom: Write your own post + upload image
        ↓
Review screen — edit if needed → Accept or Reject
        ↓
If Accepted: Posts to LinkedIn + Instagram + X + Threads
        ↓
Real-time status shown per platform
        ↓
If any error: Gmail notification sent automatically
```

---

## ⚠️ Important Notes

- This workflow uses [upload-post.com](https://upload-post.com) for Instagram, X and Threads as these platforms have restricted direct API access
- LinkedIn is posted directly via n8n's LinkedIn node
- Credentials in the workflow JSON have been replaced with placeholders — you must add your own
- Error workflow ID must be updated in main workflow settings after import

---

## 👤 Author

**Anshu** — AI Automation Engineer

- GitHub: [@anshu-ai-automate](https://github.com/anshu-ai-automate)
- LinkedIn: [Anshuman Gupta](https://linkedin.com/in/anshuman-gupta)

---

## 📄 License

MIT License — feel free to use and modify.
