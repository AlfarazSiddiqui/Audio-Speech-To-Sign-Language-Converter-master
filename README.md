🤟 Audio Speech to Sign Language Converter
📌 Project Overview

The Audio Speech to Sign Language Converter is a Django-based web application that converts live speech or typed text into Indian Sign Language (ISL) animations.

The system uses speech recognition and Natural Language Processing (NLP) techniques to process the spoken sentence, extract its key words, and play the matching sign language video clips one after another. It demonstrates how Artificial Intelligence and web technologies can be applied to improve accessibility and communication for the hearing-impaired community.

Note: This project is intended for educational purposes. Sign language output is produced from a limited set of pre-recorded animations and may not represent complete, grammatically accurate ISL.

🎯 Objectives
Convert live audio speech into text using the browser's speech recognition.
Apply NLP techniques to simplify sentences into sign-language-friendly key words.
Display relevant ISL animations for the processed words.
Support manual text input along with voice input.
Provide secure access through user sign-up and login.
Demonstrate the use of AI and NLP for accessibility and social good.
✨ Features
Speech Input: Records speech with a mic button using the Web Speech API (en-IN).
Text Input: Allows typing a sentence manually instead of speaking.
NLP-Based Processing: Tokenizes, tags, filters, and lemmatizes the sentence using NLTK.
Tense Handling: Detects past, present continuous, and future tense and adds the signs Before, Now, or Will accordingly.
ISL Animation Playback: Plays matching word-level animations in sequence with Play/Pause control.
Fingerspelling Fallback: If a word has no animation, it is split into letters and shown letter by letter (A–Z).
Key Word Highlighting: Highlights the word currently being signed.
User Authentication: Sign Up, Log In, and Log Out using Django's built-in authentication.
SQLite Database: Stores user account data.
Multi-Page Interface: Home, Animation, About, and Contact pages.
🛠️ Technologies Used
Python
Django
Natural Language Toolkit (NLTK)
JavaScript (Web Speech API – webkitSpeechRecognition)
HTML and CSS
SQLite
Blender 3D (used to create the 3D character animations)
⚙️ System Workflow
The user signs up or logs in to the application.
The user speaks using the mic button or types a sentence.
The speech is converted into text by the browser.
The text is tokenized and tagged with parts of speech (POS).
Stop words are removed and the remaining words are lemmatized.
The tense of the sentence is detected and a tense word (Before / Now / Will) is added.
Each word is checked against the animation library; unavailable words are split into letters.
The ISL videos play one after another in the animation panel.
 Speech / Text  →  Speech-to-Text  →  NLP Processing  →  Tense Detection
                                                              ↓
              ISL Animation Output  ←  Video Mapping  ←  Word / Letter Match
🧠 NLP Methodology

The text processing pipeline in A2SL/views.py follows these steps:

Tokenization: Splits the sentence into individual words.
POS Tagging: Labels each word as a noun, verb, adjective, and so on.
Stop Word Removal: Removes words such as is, am, are, the, a, an that are not signed in ISL.
Lemmatization: Reduces words to their base form (for example, running → run).
Pronoun Mapping: Converts I to Me to match the available sign.
Tense Marking: Adds a time-indicating word at the beginning of the sentence.
Animation Mapping: Matches each processed word to its .mp4 file, or falls back to letters.
📂 Project Structure
Audio-Speech-To-Sign-Language-Converter/
│
├── A2SL/                  # Django project (settings, urls, views, wsgi, asgi)
├── assets/                # ISL animation videos (A–Z, 0–9, common words) and mic icon
├── templates/             # HTML templates (base, home, animation, login, signup, about, contact)
├── db.sqlite3             # SQLite database
├── manage.py              # Django management script
├── requirements.txt       # Python dependencies
├── setup.py               # Package setup file
├── LICENSE                # MIT License
└── README.md              # Project documentation
🚀 Installation and Setup
Prerequisites
Python 3.7 or higher
A browser that supports the Web Speech API (such as Google Chrome)
Internet connection (required for browser speech recognition and NLTK downloads)
Steps
Clone or download the project and open it in a terminal.
bash
   cd Audio-Speech-To-Sign-Language-Converter
Install the dependencies.
bash
   pip install -r requirements.txt
Download the required NLTK data (some are downloaded automatically on startup).
python
   import nltk
   nltk.download('punkt')
   nltk.download('averaged_perceptron_tagger')
   nltk.download('wordnet')
   nltk.download('omw-1.4')
Run the development server.
bash
   python manage.py runserver
Open http://127.0.0.1:8000/ in your browser.
Sign up, log in, click the mic button (or type text), submit, and press Play/Pause to watch the sign language animation.
🔮 Future Enhancements
Expand the animation library with more words and phrases.
Improve ISL grammar handling beyond simple word-by-word mapping.
Add support for regional languages such as Hindi and Marathi.
Improve the NLP pipeline for better sentence understanding.
Add automatic playback after submitting text.
Add a speed control and a full-screen mode for animations.
Provide a sign-language-to-text feature using computer vision.
Improve the user interface and mobile responsiveness.
Deploy the application on a cloud platform.
🔒 Privacy and Safety
Do not commit the Django SECRET_KEY to public repositories; load it from an environment variable instead.
Set DEBUG = False and configure ALLOWED_HOSTS before any public deployment.
Avoid committing db.sqlite3 with real user accounts and passwords.
Remove personal contact details from public pages before sharing the project.
Speech recognition is handled by the browser, so audio may be processed by the browser vendor's service.
Treat the output as an assistive aid, not as a replacement for a certified sign language interpreter.
📄 License

This project is licensed under the MIT License. See the LICENSE file for details.

Original project by Jigar Gajjar, Nilkanth Patadiya, Ashish Bavaliya, and Dhairya Gadani.
