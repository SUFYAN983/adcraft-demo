# AdCraft Demo

AI-powered ad creation from a URL. Built for the Oracle Cloud platform.

## Features

- **URL → Ad**: Paste any website URL → extracts brand name, headline, description, og:image, colors, favicon
- **Image & Video ads**: Square, Landscape, Story, Banner formats
- **Live editor**: Edit text, colors, CTA in real-time with instant preview
- **API-ready**: Drop in Creatomate / fal.ai / OpenAI keys to enable real AI generation

## Deploy to Vercel (demo)

```bash
# 1. Clone / unzip this project
npm install

# 2. Run locally
npm run dev
# → http://localhost:3000

# 3. Deploy to Vercel
npx vercel deploy
```

Or click: [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)

## Enable AI Generation

Copy `.env.example` → `.env.local` and add your API keys:

| Key | Provider | Purpose |
|-----|----------|---------|
| `CREATOMATE_API_KEY` | [Creatomate](https://creatomate.com) | Image + video rendering |
| `FAL_API_KEY` | [fal.ai](https://fal.ai) | Fast video generation |
| `OPENAI_API_KEY` | [OpenAI](https://platform.openai.com) | DALL-E 3 images + copy |
| `GEMINI_API_KEY` | [Google](https://ai.google.dev) | Veo video generation |

## Production: Oracle Cloud Infrastructure

This app is fully deployable to OCI:

1. **OCI Container Registry** – push Docker image
2. **OCI Kubernetes Engine (OKE)** – or deploy as OCI Functions
3. **OCI Media Streams** – for video delivery
4. **Oracle Autonomous Database** – store generated ads and user sessions

```bash
# Build Docker image
docker build -t adcraft .
docker tag adcraft <region>.ocir.io/<tenancy>/adcraft:latest
docker push <region>.ocir.io/<tenancy>/adcraft:latest
```

## Project Structure

```
pages/
  index.js          # Main UI (URL input → brand → editor)
  api/
    scrape.js       # URL scraping + brand extraction
    generate.js     # Ad generation (mock + real API hooks)
components/
  AdCanvas.js       # CSS-based ad preview renderer
  AdEditor.js       # Right-panel layer editor
styles/
  globals.css       # Tailwind + custom animations
```
