# Voice Translator

Choose the language you will speak and the language you want to translate to from the dropdowns. Record a sentence, read the translation, and play its audio. Supported languages are Telugu, Hindi, Tamil, and English.

## Run locally

Install Python 3.10 or newer and get an API key from the [Groq Console](https://console.groq.com/keys). Open a terminal in this folder and run the following on macOS or Linux.

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
read -rs GROQ_API_KEY
export GROQ_API_KEY
python -m streamlit run app.py
```

When the terminal reaches the `read` command, paste your Groq API key and press Enter. The key stays hidden as you type. Open the local URL printed by Streamlit and allow microphone access.

## Try it

1. Select **Telugu** as the spoken language and **Hindi** as the target language.
2. Record **మీరు ఎలా ఉన్నారు?** and click **Translate**.
3. Look for **आप कैसे हैं?** and press Play on the audio player.
4. Choose different languages from the dropdowns to translate another sentence.

## Follow the code

- `transcribe()` sends the WAV recording to Whisper on Groq and returns text in the spoken language.
- `translate()` sends the transcript to the Groq chat model and returns text in the target language. Set the optional `GROQ_TRANSLATION_MODEL` environment variable to use another available Groq chat model.
- `speak()` uses gTTS to create MP3 audio in memory.

The app processes one recording at a time. It needs internet access. Groq receives the recording and transcript, and gTTS sends the translated text to Google's service. Use sample sentences when trying the app.
