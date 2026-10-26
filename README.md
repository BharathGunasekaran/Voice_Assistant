# 🎙️ Real-time Voice Assistant (LiveKit Agents)

A friendly general-purpose **voice assistant** that you talk to in real time. It's built with
**LiveKit Agents**, and its prompts are tuned for speech: short answers, no markdown, and
numbers and links spelled out so they sound natural when spoken.

## Features

- 🎙️ Low-latency voice conversation over WebRTC
- ⚡ Preemptive response generation for faster replies
- 🔇 Noise cancellation (BVC), with a telephony-tuned mode for SIP callers
- 🗣️ Multilingual turn detection and Silero voice activity detection
- 🛡️ Built-in guardrails: general information only for medical, legal and financial topics
- 👋 Greets the user as soon as they join

## Voice pipeline

```text
User speech ──▶ AssemblyAI Universal Streaming (STT)
            ──▶ Google Gemini 2.5 Flash (LLM)
            ──▶ Cartesia Sonic-3 (TTS) ──▶ spoken reply
```

## Tech stack

- Python, LiveKit Agents
- LiveKit Inference: AssemblyAI, Gemini 2.5 Flash, Cartesia Sonic-3
- Silero VAD, LiveKit multilingual turn detector, LiveKit noise cancellation

## Getting started

### Prerequisites
- Python 3.10+
- A [LiveKit Cloud](https://cloud.livekit.io/) project

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Configure environment variables
Create a `.env` file:
```env
LIVEKIT_URL=wss://your-project.livekit.cloud
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret
```

### 3. Run the agent
```bash
python agent.py download-files   # first run only: downloads VAD and turn-detector models
python agent.py dev
```
Then talk to it from the [LiveKit Agents Playground](https://agents-playground.livekit.io/).

## Project structure

```text
Voice_Assistant/
├── agent.py          # Agent server, voice pipeline and session setup
├── prompts.py        # Voice-friendly system instructions and guardrails
└── requirements.txt
```
