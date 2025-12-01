<!-- ===================================================================== -->
<!--                           PROJECT BANNER                               -->
<!-- ===================================================================== -->
<p align="center">
	<img src="https://i.imgur.com/lCqFZ8M.jpeg" width="100%" alt="ChronoKen Banner">
</p>

<h1 align="center">⏳⚡ ChronoKen — AI Study & Productivity Agent</h1>

<p align="center">
	<i>Your personal AI that organizes your day, builds your study plan, manages tasks, and syncs everything with Google Calendar.</i>
</p>

<p align="center">
	<img src="https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge" />
	<img src="https://img.shields.io/badge/Made%20With-Love❤️-blueviolet?style=for-the-badge" />
	<img src="https://img.shields.io/badge/PRs-Welcome-orange?style=for-the-badge" />
</p>

---

<!-- ===================================================================== -->
# 📌 Table of Contents
<!-- ===================================================================== -->

- [✨ Features](#-features)
- [🧠 Tech Stack](#-tech-stack)
- [📁 Project Structure](#-project-structure)
- [🔧 Installation](#-installation)
- [🔑 Environment Variables](#-environment-variables)
- [🔐 Google OAuth Setup](#-google-oauth-setup)
- [🚀 Running the App](#-running-the-app)
- [📅 Google Calendar Sync](#-google-calendar-sync)
- [💬 Ken AI Chat](#-ken-ai-chat)
- [🏗️ CLI Agent](#️-cli-agent)
- [🖼️ Screenshots](#️-screenshots)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)

---

# ✨ Features

### **🧠 AI Agent (Ken)**
- Natural language understanding  
- Create tasks using text  
- Generate personalized study plans  
- Real-time chat using WebSockets  
- Plan in 3–7 days with hours  

### **📅 Google Calendar Integration**
- Secure OAuth 2.0 login  
- Automatically create study events  
- Daily sync support  
- Add tasks → Google Calendar instantly  

### **📊 Dashboard**
- Missions manager  
- Notes → convert to tasks  
- Timeline view  
- Focus Timer (Pomodoro)  
- Analytics overview  
- Floating chat with Ken  

### **🖥️ CLI Mode**
- Same AI engine  
- Create tasks, list tasks, generate plans  
- Great for terminal users  

---

# 🧠 Tech Stack

## **Backend**
| Technology | Purpose |
|-----------|---------|
| 🐍 **Python 3** | Core backend |
| ⚙️ **Flask** | Web server + API |
| 🔌 **WebSockets** | Real-time AI chat |
| 🔐 **Google OAuth 2.0** | Login + Calendar access |
| 📅 **Google Calendar API** | Sync events |
| 🤖 **Google AI Studio (Gemini API)** | AI reasoning & planning |
| 🧠 **OpenAI API** (optional) | Alternative AI model |
| 🗄️ **SQLite** | Local database |
| 🔑 **dotenv** | Environment variables |

## **Frontend**
| Tech | Purpose |
|------|---------|
| 🟧 **JavaScript (ES6)** | Logic, WebSocket client, UI |
| 🎨 **CSS3** | Styling |
| 🧱 **HTML5** | UI structure |
| 🪟 **Modals + Floating UI** | Ken chat, Profile editor, Timetable |

## **Tools**
- 🟥 Streamlit (optional UI)
- 🟦 Git & GitHub
- 🧪 VS Code

---

## 📁 Project Structure

High-level overview:

- `app.py` — Flask server and API endpoints (calendar OAuth, sync endpoints)
- `web/` — static frontend (`dashboard.html`, `dashboard.js`, `dashboard.css`, auth pages)
- `data/chronoken.db` — SQLite storage for users and tasks
- `agent.py` / `tools.py` — agent logic and helper functions
- `requirements.txt` — Python dependencies
- `.env.template` — environment variable template

---

## 🔧 Installation

1. Create and activate a virtual environment (project root):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install -r requirements.txt
```

3. Copy `.env.template` to `.env` and fill the values (API keys, client ids, SECRET_KEY).

---

## 🔑 Environment Variables

Key variables (use `.env.template` as a starting point):

- `GOOGLE_API_KEY` — API key for Google Generative Language API (if used)
- `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET` — OAuth client credentials (or place `client_secret.json` in project root)
- `GOOGLE_OAUTH_REDIRECT` — OAuth callback (default: `http://127.0.0.1:8000/api/calendar/oauth2callback`)
- `OPENAI_API_KEY` — optional fallback
- `SECRET_KEY` — Flask session secret
- `DATABASE_URL` — SQLite path (default: `sqlite:///data/chronoken.db`)

---

## 🔐 Google OAuth Setup

1. In Google Cloud Console create an OAuth 2.0 Client ID (Web application) and add the redirect URI:

```
http://127.0.0.1:8000/api/calendar/oauth2callback
```

2. Download `client_secret.json` and place it at the project root, or set `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` in `.env`.
3. If the consent screen is in Testing, add your Google account as a Test User.

---

## 🚀 Running the App

```powershell
.venv\Scripts\Activate.ps1
python app.py
```

Open `http://127.0.0.1:8000/` to access the dashboard UI.

---

## 📅 Google Calendar Sync

- Click `Sync Calendar` in the dashboard to launch the OAuth popup.
- After granting access the app will persist short-lived credentials (stored in the SQLite `users.calendar_tokens`) to refresh tokens for the user.

---

## 💬 Ken AI Chat

- Summon Ken from the dashboard to chat and generate plans.
- The agent uses configured model keys (`GOOGLE_API_KEY` or `OPENAI_API_KEY`) to call the LLM.

---

## 🏗️ CLI Agent

- Run `python main.py` for a small CLI interface to create/list tasks and generate plans.

---

## 🤝 Contributing

- PRs welcome. Please open issues for bugs or feature requests.

---

## 📜 License

- MIT (replace as appropriate)

## Prerequisites

- Python 3.10+ (3.11 recommended)
- Git
- A Google Cloud project with the Google Calendar API and Generative Language API enabled (if you plan to use both features)

## Quick setup (development)
1. Create and activate a virtual environment in the project root:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```
2. Install Python dependencies:

```powershell
pip install -r requirements.txt
```
3. Copy `.env.template` to `.env` and fill in your keys and values.

4. (Google Calendar OAuth) Create OAuth client credentials in Google Cloud Console and download `client_secret.json` to the project root. Make sure the OAuth redirect URI includes:

```
http://127.0.0.1:8000/api/calendar/oauth2callback
```
Add any test users on the OAuth consent screen if the app is in Testing.

5. Start the server from the project root:

```powershell
.venv\Scripts\Activate.ps1
python app.py
```
Open `http://127.0.0.1:8000/` in your browser to view the dashboard.

---

## Environment variables (.env)
Use the provided `.env.template` as a starting point. Important variables include:

- `GOOGLE_API_KEY` — API key for Google Generative Language API (if used)
- `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` — optional; if not provided, the app will try to load `client_secret.json` from the project root
- `GOOGLE_OAUTH_REDIRECT` — callback URL (default: `http://127.0.0.1:8000/api/calendar/oauth2callback`)
- `OPENAI_API_KEY` — optional; included if you want to use OpenAI fallbacks
- `SECRET_KEY` — Flask session secret (set to a random string in production)
- `DATABASE_URL` — optional DB path (default: `sqlite:///data/chronoken.db`)

Do NOT commit `.env` to source control.

---

## Google setup notes
- Enable the **Google Calendar API** and the **Generative Language API** (if you use the LLM features).
- For Calendar OAuth during development, set the redirect URI to the callback path in the app (`/api/calendar/oauth2callback`) and add any test users to the OAuth consent screen.
- Put `client_secret.json` (OAuth credentials) at the project root, or set `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` in `.env`.

If you see `API key not valid` from the Generative Language API: check that the `GOOGLE_API_KEY` belongs to the same project where the API is enabled and verify API restrictions (key restrictions may block access).

---

## Running & development tips
- Run the server: `python app.py` from the project root.
- The web UI is served from `web/` (static files). The dashboard front-end calls backend endpoints like `/api/calendar/oauth_start` and `/api/calendar/sync-today`.
- The app persists simple user/task data in `data/chronoken.db` (SQLite).

---

## Troubleshooting
- Missing Python packages: ensure your venv is active and run `pip install -r requirements.txt`.
- OAuth errors (401/invalid_client or 403/access_denied): verify `client_secret.json`, `GOOGLE_CLIENT_ID`, redirect URIs, and add your test account to the OAuth consent screen if in Testing.
- Generative API key errors: ensure the Generative Language API is enabled for the project and the API key has the correct restrictions (or none for quick local testing).
# Concierge-Agents
Capstone

## Overview

`Concierge-Agents` is a small CLI Smart Study & Productivity Concierge Agent that helps
students manage tasks and generate short study plans. It uses Google's Generative AI
client to parse natural language commands and map them to task actions.

## Quick Setup

- Create and activate a Python virtual environment in the project root:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

- Install dependencies:

```powershell
pip install -r requirements.txt
```

- Copy or create a `.env` file at the project root with the following keys:

```dotenv
GOOGLE_API_KEY=your_api_key_here
MODEL_NAME=models/gemini-2.5-pro   # optional; any supported model from the list_models script
```

## Running the app

Start the interactive CLI:

```powershell
.\.venv\Scripts\Activate.ps1
python main.py
```

Type messages like:

- `I have a DBMS assignment due on 2025-11-25, it will take around 3 hours. Please add it.`
- `Show me all my tasks.`
- `I will study for 2 hours today, make a plan.`

The assistant will respond and may create/list/update tasks in the local storage.

## Model selection & troubleshooting

- If you see errors mentioning `models/... not found` or `unexpected model name format`, run the included
	script to list available models for your API key:

```powershell
python list_models_lowlevel.py
```

- Pick a model name from the output (it will look like `models/gemini-2.5-pro`) and set it in your `.env` as
	`MODEL_NAME=`.

- If Python raises `ModuleNotFoundError` for `google` imports, ensure your venv is activated and required
	packages are installed. You can install the main packages with:

```powershell
.\.venv\Scripts\python.exe -m pip install google-generativeai google-ai-generativelanguage google-api-core
```

## Development notes

- `agent.py` contains the LLM integration and maps model responses into JSON actions.
- `tools.py` implements `create_task`, `list_tasks`, `update_task_status`, and `generate_plan` used by the agent.
- `list_models_lowlevel.py` enumerates models available to your API key.

## Security

- Do not commit `.env` with secret API keys to public repositories. Keep the `.env` listed in `.gitignore`.

**Important:** If an API key was ever committed, a history-rewrite was prepared and a backup of the pre-purge state was pushed to
`origin/backup-before-purge-20251123-175400`. Do **not** share keys — rotate/revoke any exposed keys in the Cloud Console.

## Streamlit UI (optional)

A small Streamlit prototype UI is included at `ui_streamlit.py` to chat with the local agent implementation. There are three recommended ways to run it on Windows:

- Recommended (easiest on Windows): use Conda/Miniconda and install Streamlit from `conda-forge` (prebuilt `pyarrow` wheels):

```powershell
# Install Miniconda/Miniforge if you don't have it, then:
conda create -n concierge python=3.10 -c conda-forge streamlit
conda activate concierge
cd 'C:\Users\Aditya\OneDrive\Desktop\Capstone\Concierge-Agents'
streamlit run ui_streamlit.py
```

- If you prefer the project's venv (pip): installing `streamlit` with pip on Windows may trigger a `pyarrow` source build which
	requires CMake + Visual Studio Build Tools. If you want to use the venv, install the native build tools first, then:

```powershell
.\.venv\Scripts\Activate.ps1
.venv\Scripts\python.exe -m pip install --upgrade pip setuptools wheel
.venv\Scripts\python.exe -m pip install streamlit
.venv\Scripts\python.exe -m streamlit run ui_streamlit.py
```

- Quick local test (uses system `streamlit` if installed):

```powershell
streamlit run ui_streamlit.py
```

Notes about the included UI
- The UI calls the same `handle_user_message` function in `agent.py` so it uses the same `.env` keys (`GOOGLE_API_KEY` and `MODEL_NAME`).
- If Streamlit isn't available in your project venv, the editor may show a missing-import diagnostic; this repo includes a temporary
	Pylance ignore on the `streamlit` import to avoid a distracting editor error while you install Streamlit in a chosen environment.
- A now-removed call to `st.experimental_rerun()` caused an AttributeError on some Streamlit versions; `ui_streamlit.py` was patched
	to be compatible across common Streamlit releases.

## Troubleshooting Streamlit install (pyarrow errors)

- If `pip install streamlit` fails building `pyarrow` with errors mentioning `cmake` or Visual Studio, prefer the Conda approach above.
- Alternatively install Visual Studio Build Tools (select C++ workload) and install CMake before retrying pip.

## Final notes

- Always keep secrets out of source control. Use `.env.template` to document required variables and instruct collaborators to create their own `.env` files.
- If you want, I can help create a small Dockerfile or a `requirements-conda.txt` to make reproducible installs on Windows.

## Troubleshooting quick checklist

- Activate the project's venv before running scripts.
- Verify `.env` contains `GOOGLE_API_KEY` and optional `MODEL_NAME`.
- If the model request fails, run `list_models_lowlevel.py` and set a supported `MODEL_NAME`.



