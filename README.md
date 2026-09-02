# Izabela Next – Piper Custom Server

Small tray app that connects **Izabela Next** to a local **Piper** TTS server.

```
Izabela  →  this app (:6789)  →  Piper (:5000)
```

## Requirements

1. [Piper](https://github.com/OHF-Voice/piper1-gpl) running as an HTTP server
2. This app (portable `.exe` or `npm run dev`)
3. [Izabela Next](https://github.com/nature-heart-software/izabela) with the Custom speech engine

## Setup

### 1. Start Piper

```bash
pip install piper-tts[http]
python -m piper.download_voices en_US-lessac-medium
python -m piper.http_server -m en_US-lessac-medium
```

Piper listens on `http://127.0.0.1:5000` by default.

### 2. Start this app

Run the portable `.exe`, or from source:

```bash
npm install
npm run dev
```

It sits in the system tray and starts an API on **port 6789**.

Open the window from the tray and set:

| Setting | Example |
|---|---|
| Piper API URL | `http://127.0.0.1:5000` |
| Default Voice | `en_US-lessac-medium.onnx` (optional) |

### 3. Connect Izabela

1. Open **Izabela → Settings → Speech Engine**
2. Select **Custom**
3. Set API endpoint to `http://127.0.0.1:6789`
4. Pick a voice and speak

## Notes

- Piper and this app must both be running while you use Izabela
- Closing the window hides it; quit from the tray menu
- Settings are saved in `%APPDATA%\izabela-custom-server\config.json`
