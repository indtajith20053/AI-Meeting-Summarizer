# 🎙️ AI Meeting Summarizer

Upload a meeting audio recording and get back a full transcript plus an AI-generated summary — all powered by open-source Hugging Face models, with a simple Gradio web UI.

## How it works

1. Upload an audio file (e.g. a recorded meeting) through the UI.
1. The audio is loaded and resampled to 16kHz mono if needed.
1. **Whisper (small)** transcribes the audio to text.
1. **BART (facebook/bart-large-cnn)** summarizes the transcript.
1. Both the full **transcript** and the **summary** are displayed in the UI.

## Tech stack

|Component                                               |Purpose                           |
|--------------------------------------------------------|----------------------------------|
|[Gradio](https://www.gradio.app/)                       |Web UI (`gr.Blocks`)              |
|[Transformers](https://huggingface.co/docs/transformers)|Model pipelines                   |
|`openai/whisper-small`                                  |Speech-to-text transcription      |
|`facebook/bart-large-cnn`                               |Abstractive summarization         |
|torch / torchaudio                                      |Model inference + audio resampling|
|soundfile                                               |Audio file loading                |

## Prerequisites

- Python 3.9+
- (Recommended) a GPU for faster transcription/summarization — CPU also works, just slower

## Installation

```bash
git clone https://github.com/indtajith20053/AI-Meeting-Summarizer.git
cd AI-Meeting-Summarizer
pip install gradio transformers torch torchaudio sentencepiece accelerate ffmpeg-python soundfile
```

## Usage

The app currently lives in the notebook `AI_Meeting_Summarizer.ipynb`. Open and run it:

```bash
jupyter notebook AI_Meeting_Summarizer.ipynb
```

Run all cells — the Whisper and BART models will download on first run. The last cell launches the Gradio app (`demo.launch(share=True)`), which opens a local URL (and a public shareable link) in your browser. From there:

1. Upload an audio file of the meeting.
1. Click **Generate Summary**.
1. Read the full **Transcript** and the AI-generated **Meeting Summary**.

## Project structure

```
AI-Meeting-Summarizer/
├── AI_Meeting_Summarizer.ipynb   # Whisper transcription + BART summarization + Gradio UI
├── Screenshot *.png               # App screenshots
└── README.md
```

## Roadmap ideas

- [ ] Move notebook logic into a standalone `main.py` script
- [ ] Add speaker diarization (who said what)
- [ ] Extract action items / key decisions, not just a summary
- [ ] Add a `requirements.txt`
- [ ] Support longer meetings with chunked summarization

## License

Add a license of your choice (e.g. MIT) if you plan to share this publicly.

