# LFM2 Offline Chat

A fully offline AI chat interface running in the browser via WebAssembly (wllama).

## Features
- 🧠 **3 LiquidAI LFM2 models** — 350M, 700M, 1.2B (Q4_K_M quantized)
- 💾 **Offline model caching** — download once, use forever
- 📖 **Wikipedia search** — inject real knowledge into context
- 🌐 **DuckDuckGo web search** — instant answers + related topics
- 🤖 **Agent mode** — auto-searches before generating responses
- 💬 **Conversation history** — stored in localStorage
- ⚡ **Streams tokens** — see responses as they generate
- 🎨 **Modern dark UI** — ChatGPT-style interface

## Deploy to GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to **Deploy from branch → main → / (root)**
4. Visit `https://YOUR_USERNAME.github.io/REPO_NAME`

## Local Development

Just open `index.html` in a browser. For multi-thread (faster inference), serve via HTTPS or localhost:

```bash
npx serve .
# or
python3 -m http.server 8080
```

## Model URLs

Models are loaded from Hugging Face (bartowski's GGUF quantizations):

| Model | Size | URL |
|-------|------|-----|
| LFM2-350M | ~230 MB | bartowski/LFM2-350M-GGUF |
| LFM2-700M | ~430 MB | bartowski/LFM2-700M-GGUF |
| LFM2-1.2B | ~740 MB | bartowski/LFM2-1.2B-GGUF |

If model URLs change, update the `MODELS` config in `index.html`.

## Technical Notes

- Uses [wllama](https://github.com/ngxson/wllama) for in-browser WASM inference
- `coi-serviceworker.js` enables SharedArrayBuffer for multi-thread mode
- Models are cached via the browser Cache API — no re-download needed
- All inference runs client-side — no data leaves your browser
