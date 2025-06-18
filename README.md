
# 🔊 JARVIS: A Voice-Controlled Virtual Assistant in Python

## 📌 Project Overview

**JARVIS** is a voice-controlled AI-based desktop assistant built using Python. Inspired by Iron Man’s J.A.R.V.I.S, this assistant performs real-time voice recognition, executes web-based commands, speaks results aloud using TTS, fetches live news, plays songs via voice commands, and integrates with OpenAI's GPT model to provide intelligent conversational capabilities.

---

## 🧠 Features

- 🎤 **Voice Wake Word Detection** – Listens for “Jarvis” to activate.
- 🌐 **Web Automation** – Opens Google, YouTube, Facebook, LinkedIn via command.
- 📰 **Live News Updates** – Fetches and speaks top headlines from NewsAPI.
- 🎵 **Play Music** – Plays songs using pre-defined music dictionary.
- 💬 **Chat with GPT-3.5 Turbo** – Handles intelligent queries via OpenAI API.
- 🔊 **Text-to-Speech** – Responds using Google TTS and Pyttsx3.
- 🎮 **Multimedia Playback** – Uses Pygame mixer for MP3 audio handling.

---

## 🛠️ Tech Stack

| Module            | Purpose                          |
|-------------------|----------------------------------|
| `speech_recognition` | Voice input and recognition |
| `pyttsx3`         | Text-to-speech (offline)         |
| `gTTS`            | Google Text-to-Speech (online)   |
| `pygame`          | Audio playback of MP3            |
| `webbrowser`      | Browser automation               |
| `requests`        | API requests (News API, etc.)    |
| `openai`          | GPT-3.5 chat interface           |
| `pyaudio`         | Microphone access (via PortAudio)|

---

## 📂 Project Structure

```bash
jarvis/
├── main.py               # Main program file
├── musicLibrary.py       # Contains music dictionary
├── client.py             # (Optional) OpenAI helper script
├── requirements.txt      # Dependencies
└── README.md             # Project overview (this file)
````

---

## 🚀 Setup Instructions

### 1. 🖥️ System Requirements

* OS: macOS / Windows / Linux
* Python ≥ 3.8
* Working microphone
* Internet connection (for TTS and API calls)

### 2. 📦 Install Dependencies

Install using pip:

```bash
pip install -r requirements.txt
```

If `pyaudio` fails on macOS, run:

```bash
brew install portaudio
pip install pyaudio
```

### 3. 🔑 Configure API Keys

Replace placeholder values with your actual keys in `main.py`:

```python
newsapi = "<Your News API Key>"
client = OpenAI(api_key="<Your OpenAI API Key>")
```

Sign up for keys from:

* NewsAPI: [https://newsapi.org/](https://newsapi.org/)
* OpenAI: [https://platform.openai.com/](https://platform.openai.com/)

---

## 🔊 How to Run

```bash
python main.py
```

Then say **"Jarvis"** to activate, and speak your command after the response.

---

## 🧪 Example Commands

* “Jarvis → open google”
* “Jarvis → play despacito”
* “Jarvis → tell me the latest news”
* “Jarvis → what is the capital of Japan?”
* “Jarvis → open YouTube”

---

## 🧠 Limitations

* Works best in a quiet environment.
* Internet required for APIs (News, OpenAI, gTTS).
* Wake-word detection is primitive (basic string match).
* No deep NLP understanding without GPT API.

---

## 📚 Academic Purpose

This project was built as an **academic showcase of practical voice-based AI integration** using Python libraries and APIs. It demonstrates:

* Use of AI/ML APIs (OpenAI GPT)
* Real-time audio processing
* API integration and error handling
* Voice user interface (VUI) design

---

## 🙏 Acknowledgements

* OpenAI for GPT-3.5 Turbo
* Google for gTTS
* NewsAPI.org for real-time news access
* SpeechRecognition contributors
* Python Community for rich open-source support

---

## 🧑‍💻 Developed By

**\Ekaagra gupta**
B.Tech CSE (AI & ML)
Manipal University Jaipur
Email work: \ekaagra.2427010368@muj.manipal.edu
Email personal: \ekaagrag2006@gmail.com
GitHub:\https://github.com/ekaagragupta

---

## 📄 License

This project is for **educational and academic use only**. Not for commercial deployment.

