# AI Real-Time Gym Trainer 🏋️‍♂️

**AI Real-Time Gym Trainer** is a computer-vision powered fitness coach that watches you exercise through your webcam, counts your reps, checks your form, and gives you spoken feedback — like having a personal trainer in your browser.

🔗 **Home page (landing site):** [gregarious-cheesecake-781905.netlify.app](https://6a400054659bb413ac7d2147--gregarious-cheesecake-781905.netlify.app/)
🏋️ **Direct app (try it live):** [ayugit51-ai-realtime-gym-trainer.streamlit.app](https://ayugit51-ai-realtime-gym-trainer.streamlit.app/)

---

## ✨ Features

- **Real-time pose detection** using MediaPipe to track body landmarks frame-by-frame from your webcam.
- **Exercise detection & rep counting** — modular detectors (e.g. squats) analyze joint angles to count reps and flag form issues automatically.
- **AI-powered voice feedback** — form corrections and encouragement are generated using the Groq LLM API and spoken aloud with gTTS, so you get coaching without looking away from the screen.
- **Session persistence** — workout history and stats are stored locally in SQLite (`data.db`) so you can track progress over time.
- **Streamlit web interface** — no install needed beyond Python; runs right in the browser.

---

## 🧠 How It Works

1. **Capture** — your webcam feed is streamed into the app frame-by-frame.
2. **Pose estimation** — MediaPipe extracts body landmarks (joints, limbs) from each frame.
3. **Exercise analysis** — a detector (e.g. `SquatDetector`, built on a shared `BaseExercise` class) computes joint angles to determine rep count, depth, and form quality.
4. **Feedback generation** — the Groq API (Llama models) turns form data into natural-language coaching tips.
5. **Voice output** — gTTS converts that feedback into speech, delivered in real time as you train.
6. **Persistence** — session stats are saved to a local SQLite database for tracking over time.

---

## 📁 Project Structure

```
AI-REALTIME-GYM-TRAINER/
├── main.py                 # Streamlit app entry point
├── core/                   # Core app logic — session/state management, orchestration
├── detectors/              # Exercise detectors (e.g. BaseExercise, SquatDetector)
├── ml_models/              # Pose estimation / ML model logic (MediaPipe integration)
├── services/               # External integrations — Groq API calls, gTTS voice feedback, DB repository layer
├── static/                 # Static assets (CSS, images)
├── .streamlit/             # Streamlit configuration
├── .devcontainer/          # Dev container config for consistent local setup
├── data.db                 # SQLite database storing workout/session history
├── packages.txt            # System-level package dependencies (for cloud deployment)
└── requirements.txt        # Python dependencies
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- A webcam
- A [Groq API key](https://console.groq.com/) for AI-generated feedback

### Installation

```bash
git clone https://github.com/Ayushgit51/AI-REALTIME-GYM-TRAINER.git
cd AI-REALTIME-GYM-TRAINER
pip install -r requirements.txt
```

### Configuration

You can provide your Groq API key in either of these ways:

**Option 1 — `.env` file** (recommended for local development)

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your-api-key-here
```

**Option 2 — Streamlit secrets** (recommended for Streamlit Cloud deployment)

Add it to `.streamlit/secrets.toml`:

```toml
GROQ_API_KEY = "your-api-key-here"
```

### Running locally

```bash
streamlit run main.py
```

Then open the local URL Streamlit gives you, allow webcam access, pick an exercise, and start training. Live form feedback and rep counts will appear in real time, with spoken coaching alongside.

---

## 🛠️ Tech Stack

- **Python** — core application logic
- **Streamlit** — web UI and app framework
- **MediaPipe** — real-time pose/landmark detection
- **Groq API** (Llama models) — AI-generated coaching feedback
- **gTTS** — text-to-speech for voice feedback
- **SQLite** — local persistence for workout sessions
- 
---

## 👤 Author

**Ayush** — AI/ML Engineer | Building practical, story-driven AI projects
- GitHub: [@Ayushgit51](https://github.com/Ayushgit51)
