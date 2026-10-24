Audio Speech to Sign Language Converter
A Django-based web application that converts spoken audio or manually
entered text into text tokens and displays matching Indian Sign Language
(ISL) animation clips.

The project is designed as an accessibility-focused demonstration to
help users explore speech/text-to-sign animation.
Features
- Speech input: Uses the browser's Web Speech API to capture
  speech, where supported.
- Text input: Allows users to enter a sentence manually.
- Text preprocessing: Uses NLTK tokenization, part-of-speech
  tagging, stop-word filtering, and lemmatization.
- Tense handling: Adds simple time-related sign tokens for some
  past, future, and present-continuous sentences.
- Sign animations: Matches processed words to MP4 clips in the
  assets/ directory. If a word clip is unavailable, the application
  attempts to spell the word character by character.
- User accounts: Includes sign-up, login, and logout pages.
- Django pages: Includes Home, About, Contact, and Animation
  pages.
Important: This is a word/clip-matching demonstration, not a
complete or certified Indian Sign Language translation system. The
output depends on the animation clips included with the project and
may not preserve the full grammar or meaning of a spoken sentence.

Technologies Used
- Python
- Django
- HTML, CSS, and JavaScript
- Browser Web Speech API
- Natural Language Toolkit (NLTK)
- SQLite
- MP4 sign-animation assets
Project Structure
Audio-Speech-To-Sign-Language-Converter/
├── A2SL/
│   ├── settings.py
│   ├── urls.py
│   ├── views.py
│   ├── asgi.py
│   └── wsgi.py
├── assets/
│   └── Word and letter sign-animation clips (.mp4)
├── templates/
│   ├── home.html
│   ├── animation.html
│   ├── login.html
│   ├── signup.html
│   ├── about.html
│   ├── contact.html
│   └── base.html
├── manage.py
├── requirements.txt
├── setup.py
└── README.md
Requirements
- Python 3.9 or a compatible Python version
- A modern browser with Web Speech API support for microphone input
- Internet access may be needed on the first run for NLTK resources or
  package installation
- Microphone permission enabled in the browser to use speech input
The project uses Django and NLTK. If installation fails with a newer
Python version, try a Python version supported by the installed
dependency versions.

How It Works
1. The user speaks into the browser microphone or types a sentence.
2. The application receives the text.
3. NLTK tokenizes the sentence and applies basic language
   preprocessing.
4. The application checks whether each processed word has a matching
   animation clip.
5. Available word clips are displayed; otherwise, the application
   attempts to use letter clips.
6. The animation page presents the resulting sequence of clips.
Browser and Microphone Notes
- Speech recognition support depends on the browser and operating
  system.
- Allow microphone access when the browser asks for permission.
- If microphone input is unavailable, use the manual text input.
- Try short, clear sentences first. Not every word or sentence will
  have a corresponding clip.

  License
See the LICENSE file for license details.
