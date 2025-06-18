
Jarvis: Your Personal AI Assistant
Project Title
Jarvis: An Advanced Voice-Controlled AI Assistant for Streamlined Daily Tasks and Automation

Abstract
This project, "Jarvis," develops a foundational voice-controlled Artificial Intelligence assistant using Python. Inspired by the intelligent systems from popular media, Jarvis is designed to automate routine tasks, provide information, and facilitate interactions within a desktop environment. It leverages contemporary Speech-to-Text (STT) and Text-to-Speech (TTS) technologies, coupled with basic natural language processing (NLP) and integration with various web services. This README serves as a detailed submission document for the faculty at IITT, outlining the project's current features, technical design, installation procedures, usage instructions, and potential avenues for future development.

Table of Contents
Introduction

Current Features

Technical Architecture

Core Components

Technologies Used

Installation Guide

Prerequisites

Setup Steps

Usage

Activation

Commands

Project Structure

Future Scope

Troubleshooting

Contributing

Acknowledgments

Contact Information

1. Introduction
In an increasingly interconnected world, intelligent personal assistants are becoming indispensable tools for managing information and tasks. Jarvis aims to provide a robust, voice-activated system that simplifies daily digital interactions. This project represents an initial exploration into building such an assistant, focusing on core functionalities and extensibility. Our primary goal is to demonstrate the practical application of AI concepts, specifically in speech processing and API integration, to enhance user productivity and demonstrate efficient human-computer interaction.

2. Current Features
The current iteration of Jarvis implements the following functionalities:

Voice Recognition & Synthesis:

Speech-to-Text (STT): Accurately transcribes spoken commands into text using Google Speech Recognition.

Text-to-Speech (TTS): Responds to user queries and provides information using Google Text-to-Speech (gTTS), offering natural-sounding voice output.

Web Navigation:

Website Opening: Opens frequently used websites like Google, Facebook, YouTube, and LinkedIn directly in the default web browser.

Music Playback:

Song Playback: Plays specific songs by opening their predefined links (stored in a musicLibrary module) in the web browser.

News Updates:

Top Headlines: Fetches and reads out the latest top headlines from India using the News API.

General AI Queries:

Intelligent Responses: For commands not explicitly coded, Jarvis leverages the OpenAI GPT-3.5-turbo model to provide intelligent, short responses based on the query.

3. Technical Architecture
Jarvis is designed with a modular structure, which facilitates easy expansion and maintenance of its capabilities.

3.1. Core Components

Main Control Unit (jarvis.py): Serves as the central orchestrator, initializing speech engines, listening for wake words, processing recognized commands, and routing them to the appropriate handler functions.

Speech Handling: Manages audio input (microphone) for STT and converts text to speech for output.

Command Processing: A series of conditional statements (if/elif) identify predefined commands, while a fallback mechanism routes general queries to the OpenAI API.

API Integrations: Interfaces with external services like Google Speech Recognition, Google Text-to-Speech, News API, and OpenAI.

3.2. Technologies Used

Programming Language: Python 3.x

Speech Recognition: speech_recognition library (utilizes Google Speech Recognition API).

Text-to-Speech: gTTS (Google Text-to-Speech) for high-quality audio output, played using pygame.mixer. (Note: pyttsx3 is also present in the code but gTTS is currently active for speech synthesis).

Web Browsing: webbrowser module for opening URLs.

HTTP Requests: requests library for making API calls (e.g., to News API).

Artificial Intelligence Model: openai library for interacting with the OpenAI GPT-3.5-turbo model.

Audio Playback: pygame for playing generated .mp3 speech files.

Operating System Interaction: os module for file system operations (e.g., deleting temporary audio files).

4. Installation Guide
4.1. Prerequisites

Ensure the following are installed on your system before proceeding:

Python 3.8 or higher: Downloadable from the official Python website.

pip (Python package installer): Typically included with Python installations.

Internet Connection: Essential for accessing Google Speech Recognition, Google Text-to-Speech, News API, and OpenAI services.

Microphone: Required for capturing voice commands.

Speaker/Headphones: For hearing Jarvis's voice responses.

4.2. Setup Steps

Clone the Repository:
If you are provided with a Git repository, clone it:

git clone https://github.com/your-username/Jarvis-AI-Assistant.git
cd Jarvis-AI-Assistant

(Replace your-username/Jarvis-AI-Assistant.git with the actual repository URL if provided.)

Create a Virtual Environment (Highly Recommended):
A virtual environment isolates project dependencies, preventing conflicts with other Python projects.

python -m venv venv

Activate the virtual environment:

On Windows:

.\venv\Scripts\activate

On macOS/Linux:

source venv/bin/activate

Install Required Libraries:
Install all necessary Python packages:

pip install speechrecognition pyttsx3 requests openai gtts pygame

(Note: The comment # pip install pocketsphinx in the code suggests it might be an optional or future dependency for offline speech recognition, but it's not strictly required for the current code's functionality.)

API Key Configuration:
To ensure secure handling of sensitive information and allow for easy modification, create a config.py file in the root directory of your project (the same directory as jarvis.py). Add your API keys to this file.

Create config.py:

# config.py

NEWS_API_KEY = "YOUR_NEWS_API_KEY_HERE"  # Get from https://newsapi.org/
OPENAI_API_KEY = "YOUR_OPENAI_API_KEY_HERE" # Get from https://platform.openai.com/

Modify jarvis.py to import keys:
Open jarvis.py and replace the hardcoded API keys with imports from config.py:

# In jarvis.py
# ... other imports ...
import config # Add this line

# newsapi = "a3336f22243f439bb48bbcadc497f57e" # Remove or comment out this line
newsapi = config.NEWS_API_KEY # Use key from config.py

# ...
def aiProcess(command):
    # client = OpenAI(api_key="<Your Key Here>") # Remove or comment out this line
    client = OpenAI(api_key=config.OPENAI_API_KEY) # Use key from config.py
    # ...

Add config.py to .gitignore:
If using Git, ensure config.py is added to your .gitignore file to prevent sensitive API keys from being committed to your repository. Create/edit .gitignore in the project root:

# .gitignore
venv/
*.pyc
__pycache__/
temp.mp3
config.py # Crucial: Do not commit API keys!

Create musicLibrary.py:
Create a file named musicLibrary.py in the project root to store your music links. This file should contain a dictionary named music.

Example musicLibrary.py:

# musicLibrary.py

music = {
    "kesariya": "https://www.youtube.com/watch?v=videos_url_for_kesariya_song",
    "heeriye": "https://www.youtube.com/watch?v=videos_url_for_heeriye_song",
    "song1": "https://www.youtube.com/watch?v=link_to_song1",
    "song2": "https://www.youtube.com/watch?v=link_to_song2",
    # Add more songs as key-value pairs (song_name: YouTube_URL)
}

5. Usage
5.1. Activation

To start Jarvis, open your terminal or command prompt, navigate to the project's root directory, ensure your virtual environment is active, and execute the main script:

python jarvis.py

Jarvis will announce "Initializing Jarvis...." and then begin listening for the wake word.

5.2. Commands

Once Jarvis is initialized, it will continuously listen. When it detects the wake word "Jarvis," it will respond with "Ya" and then listen for your command.

Here are examples of commands Jarvis currently supports:

Wake Word: "Jarvis"

Web Navigation:

"open Google"

"open Facebook"

"open YouTube" (Navigates to https://www.youtube.com/)

"open LinkedIn"

Music Playback:

"play [song name]" (e.g., "play kesariya" - assuming "kesariya" is a key in musicLibrary.music)

News:

"news" (Reads out top headlines from India)

General Queries (via OpenAI):

"What is the capital of France?"

"Tell me about artificial intelligence."

"What is the time?"

"Tell me a joke."

(Any general question that OpenAI can answer concisely)

6. Project Structure
Jarvis-AI-Assistant/
├── jarvis.py              # Main execution script, contains core logic and command processing
├── requirements.txt       # (Optional, but recommended for future) List of Python dependencies (e.g., speechrecognition, pyttsx3, requests, openai, gtts, pygame)
├── config.py              # Configuration file for API keys (e.g., NEWS_API_KEY, OPENAI_API_KEY). IMPORTANT: Add to .gitignore!
├── musicLibrary.py        # Python module containing a dictionary of song names mapped to their web URLs.
├── .gitignore             # Specifies files/directories to be ignored by Git (e.g., venv/, config.py, temp.mp3)
├── temp.mp3               # Temporary file used by gTTS for speech output (deleted after playback).
└── README.md              # This README file.

7. Future Scope
The Jarvis project serves as a strong foundation, with numerous possibilities for future enhancements:

Expanded Command Set: Implement a wider array of direct commands for system controls (volume, shutdown, restart), application management (opening specific desktop apps, closing apps), and productivity tools (setting reminders, creating notes).

Advanced Natural Language Processing (NLP): Integrate more sophisticated NLP libraries (e.g., NLTK, SpaCy) for better contextual understanding, sentiment analysis, and more flexible command recognition, moving beyond simple keyword matching.

Personalization & Learning: Implement machine learning models to learn user preferences, frequently used commands, and personalized responses over time.

Offline Capabilities: Integrate robust offline Speech-to-Text (e.g., using pocketsphinx more extensively) and Text-to-Speech (using pre-trained models) to reduce reliance on internet connectivity.

GUI Development: Develop an intuitive graphical user interface (GUI) using frameworks like Tkinter, PyQt, or Kivy to provide visual feedback, display information, and offer an alternative interaction method.

Email & Messaging Integration: Implement full email composition and sending functionalities, and integrate with messaging platforms like WhatsApp or Telegram for sending messages directly.

Calendar & Scheduling: Add features for managing personal calendars, scheduling events, and setting alarms.

Smart Home Integration (IoT): Explore integration with smart home ecosystems (e.g., Home Assistant, Google Home API) to control devices via voice commands.

Robust Error Handling & Logging: Implement more comprehensive error handling and detailed logging mechanisms for better debugging and system stability.

8. Troubleshooting
speech_recognition.UnknownValueError: This typically means Jarvis could not understand the audio. Ensure you are speaking clearly, and that there isn't excessive background noise.

speech_recognition.RequestError: Indicates an issue with accessing the Google Speech Recognition service. Check your internet connection.

gTTS Playback Issues (No Sound):

Ensure pygame is correctly installed (pip install pygame).

Check your system's audio output settings.

Verify that temp.mp3 is being created and is not corrupted.

openai.AuthenticationError: Your OpenAI API key is incorrect or expired. Double-check your OPENAI_API_KEY in config.py.

News API / Requests Errors: Check your internet connection and verify that your NEWS_API_KEY in config.py is valid.

musicLibrary Key Errors: Ensure the song name you are speaking (e.g., "kesariya") exactly matches a key in the music dictionary within your musicLibrary.py file.

"Module Not Found" Errors: Ensure all required libraries are installed (pip install speechrecognition pyttsx3 requests openai gtts pygame). If you are using a virtual environment, make sure it is activated.

9. Contributing
While this project is primarily for academic submission, contributions are welcome for further development. If you are interested in extending Jarvis's capabilities, please consider:

Forking the repository.

Creating a new branch for your feature or bug fix.

Implementing your changes with clear, commented code.

Submitting a pull request with a descriptive title and detailed explanation of your modifications.

10. Acknowledgments
My esteemed professor, [Professor's Name], for their invaluable guidance, insights, and continuous encouragement throughout the development of this project. Their expertise has been instrumental in shaping Jarvis.

The developers of the speech_recognition, gTTS, OpenAI, requests, pygame, and webbrowser Python libraries, whose powerful tools made this project feasible.

Online resources and communities that provided crucial information and support during the development process.

11. Contact Information
Student Name: [Your Full Name]
Roll Number: [Your Roll Number]
Department: [Your Department]
Institute: Indian Institute of Technology [City Name] (IITT)
Email: [Your IITT Email Address]
GitHub Profile: [Your GitHub Profile URL (Optional, but highly recommended for academic projects)]

Date of Submission: June 18, 2025

