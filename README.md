# TrainerTwin — mock interview voice agent (Pipecat take-home)

Cascaded voice agent for a short mock interview: **Deepgram STT → Groq LLM → Cartesia TTS**, with interview structure in **Pipecat Flows** (`server/interview_flow.py`).

## Configuration

- **Bot Type**: Web
- **Transport(s)**: WebSocket (production client), SmallWebRTC, Daily
- **Pipeline**: Cascade
  - **STT**: Deepgram
  - **LLM**: Groq (`openai/gpt-oss-20b` by default)
  - **TTS**: Cartesia

## Setup

### Server

1. **Navigate to server directory**:

   ```bash
   cd server
   ```

2. **Install dependencies**:

   ```bash
   uv sync
   ```

3. **Configure environment variables**:

   ```bash
   cp .env.example .env
   # Edit .env and add your API keys
   ```

4. **Run the bot**:

   ```bash
   uv run bot.py
   ```

   Local browser UI: **http://localhost:7860** (WebRTC). Use headphones.

   Production-style WebSocket (Vercel client):

   ```bash
   uv run bot.py -t websocket --host 0.0.0.0 --port 10000
   ```

### Web client (`client/`)

```bash
cd client
npm install
npm run dev
```

Point the client at your WebSocket bot URL.

## Project Structure

```
├── client/              # TrainerTwin browser UI (Vercel)
├── server/              # Pipecat bot
│   ├── bot.py
│   ├── interview_flow.py
│   └── ...
└── README.md
```

## Learn More

- [Pipecat Documentation](https://docs.pipecat.ai/)
- [Pipecat GitHub](https://github.com/pipecat-ai/pipecat)
