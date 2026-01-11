# BanglaLearn: Automated Video & Audio Lesson Generator
**A data-driven pipeline to convert Excel-based vocabulary lists into complete multimedia learning units.**

##  How it Works
The system follows a 4-stage processing architecture:

### 1. Audio Synthesis (gTTS & Pydub)
- Reads word/example pairs from Excel.
- Generates speech with a 3x repetition cycle for better retention.
- Tracks exact start/end timestamps for every word to enable sub-second video synchronization.

### 2. Visual Rendering (PIL & MoviePy)
- Dynamically renders Noto Sans Bengali fonts onto HD canvas (1280x720).
- Supports multiple layouts: Topic-header, Center-focus (word), and Bottom-context (examples).
- Automatically handles multiline text wrapping for long translations.

### 3. Media Assembly
- Merges generated slides with synthesized audio.
- Maps `clip_duration` directly from the TTS timing metadata, ensuring the visual slide changes exactly when the audio for that word finishes.

### 4. Micro-Learning Distribution (FFmpeg)
- Automatically splits long videos into 5-minute chunks ("Units").
- Generates a `metadata.json` and a filtered `exercises.csv` for each unit.


##  Tech Stack
- **Language:** Python
- **AI/Audio:** Google Text-to-Speech (gTTS), Pydub
- **Video/Graphics:** MoviePy, PIL (Pillow), FFmpeg
- **Data:** Pandas, OpenPyXL
