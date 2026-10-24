# 🤟 Audio Speech To Sign Language Converter

A Django web application that converts **live speech or typed text** into **Indian Sign Language (ISL) animations**. Speak into the mic, and the app transcribes your words, processes the sentence with NLP, and plays the matching sign videos one after another.

> Built to help bridge the communication gap between hearing and hearing-impaired people.



---

## ✨ Features

- 🎙️ **Speech-to-text** using the browser's Web Speech API (`en-IN`)
- ⌨️ **Manual text input** as an alternative to the mic
- 🧠 **NLP preprocessing** with NLTK: tokenization, POS tagging, stopword removal, lemmatization
- ⏱️ **Tense detection**: adds ISL tense markers (`Before`, `Will`, `Now`) to the sentence
- 🔤 **Fingerspelling fallback**: words with no sign video are spelled letter by letter
- 🎬 **Sequential video playback** with word highlighting and a Play/Pause control
- 🔐 **User authentication**: sign up, log in and log out (Django auth)
- 📚 **150+ sign videos** for words, letters (A–Z) and digits (0–9)

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python, Django |
| NLP | NLTK |
| Frontend | HTML, CSS, JavaScript |
| Speech recognition | Web Speech API (`webkitSpeechRecognition`) |
| Animations | 3D character animated in Blender, exported as MP4 |
| Database | SQLite |

---

## ⚙️ How It Works

```
 Speech / Text
      │
      ▼
 Web Speech API  ──►  Text sentence
      │
      ▼
 Django view (animation_view)
   1. Tokenize the sentence
   2. POS-tag words and detect tense
   3. Remove stopwords (is, am, are, the, a ...)
   4. Lemmatize remaining words
   5. Add tense word (Before / Will / Now)
   6. Check each word for a matching <word>.mp4
        ├─ found      → use the word video
        └─ not found  → split into letters (fingerspelling)
      │
      ▼
 Browser plays the videos in order
```

**Example:** *"I will go to college"* → `Will` `Me` `Go` `College`

---

## 📁 Project Structure

```
Audio-Speech-To-Sign-Language-Converter/
├── A2SL/                 # Django project package
│   ├── settings.py
│   ├── urls.py
│   └── views.py          # NLP pipeline + auth views
├── assets/               # Sign language videos (words, A-Z, 0-9) and mic icon
├── templates/            # base, home, about, contact, login, signup, animation
├── manage.py
├── requirements.txt
├── setup.py
├── db.sqlite3
├── LICENSE
└── README.md
```

---

## 📋 Prerequisites

- Python **3.7+**
- **Google Chrome** or another browser that supports the Web Speech API (Firefox does not support speech recognition)
- Internet connection (the Web Speech API and the first-time NLTK downloads need it)

---



Open **http://127.0.0.1:8000/** in your browser. To use another port: `python manage.py runserver 8080`.

> **Note:** On first run, `settings.py` automatically downloads the required NLTK data (`averaged_perceptron_tagger`, `wordnet`, `omw-1.4`). If you get a tokenizer error (`punkt`), run:
> ```bash
> python -m nltk.downloader punkt
> ```

---

## 📖 Usage

1. Open the app and **Sign up** (or log in).
2. Go to the **Animation** page.
3. Click the **mic button** and speak, or type a sentence in the text box.
4. Press **Submit**.
5. View the extracted key words and watch the sign animations play. Use **Play/Pause** to control playback.

---

## 🔗 Routes

| URL | Description |
|-----|-------------|
| `/` | Home page |
| `/about/` | About page |
| `/contact/` | Contact page |
| `/signup/` | Create an account |
| `/login/` | Log in |
| `/logout/` | Log out |
| `/animation/` | Speech/text to sign converter (login required) |
| `/admin/` | Django admin |

---

## ➕ Adding New Signs

1. Add a video named exactly like the word (for example `Hospital.mp4`) to the `assets/` folder.
2. Restart the server. The pipeline will automatically use it instead of fingerspelling.

---

## ⚠️ Limitations

- Supports **English input** only (`en-IN` recognition).
- Vocabulary is limited to the available videos; other words are fingerspelled.
- Sentence handling is rule-based and does not follow the full grammar of ISL.
- Speech recognition depends on browser support and an internet connection.

---

## 🔮 Future Scope

- Larger ISL vocabulary and better grammar mapping
- Support for more input languages (Hindi, Marathi, etc.)
- Mobile app version
- Reverse conversion: sign language to text/speech

---



