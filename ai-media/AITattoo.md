# LeTa — The Minimalist Ink Studio

> **"Less Ink. More Meaning."**

LeTa is an AI-powered web application dedicated to the art of minimalist tattoos. It bridges the gap between conceptualization and skin, offering tools for design generation, placement visualization, and dermatological aftercare support.

## 🌟 Project Overview

This project serves as a digital studio where users can design bespoke tattoos using Generative AI, visualize pain levels based on body placement, and receive professional-grade aftercare advice from an AI "Ink Guardian."

The application focuses on high-contrast, blackwork, and fine-line aesthetics, using specific prompting engineering to ensure designs are "stencil-ready" for tattoo artists.

## 🚀 Key Features

### 1. AI Design Studio (`NewTattooTool`)
- **Multi-Modal Creation:**
  - **Quote Mode:** Generates typography-based tattoos in various languages (Latin, Sanskrit, Kanji) and fonts (Typewriter, Gothic, Script).
  - **Pet Portrait Mode:** Uses Image-to-Image generation to convert user-uploaded pet photos into minimalist line art or geometric styles.
  - **Icon Mode:** Text-to-Image generation for small, symbolic concepts.
- **Stencil Generation:** Automatically optimizes outputs for high contrast (black ink on white background), making them ready for thermal printers.

### 2. Interactive Pain Guide (`PainMap`)
- A visual interface allowing users to select body zones (Ribs, Spine, Forearm, etc.).
- Displays a dynamic pain level meter (1-10) with descriptive sensations (e.g., "Sharp pain, vibrating sensation on the bone").

### 3. Ink Guardian — AI Aftercare & Maintenance (`OldTattooTool`)
- **Visual Healing Analysis:** Users can upload photos of healing tattoos. The AI (Gemini 2.5 Flash) analyzes redness and discharge to detect potential infections, triggering specific **Medical Alerts**.
- **Cover-Up Assessment:** Analyzes ink density of old tattoos to suggest feasible cover-up styles (e.g., Blast over vs. Blackwork).
- **Empathetic Chat:** A fine-tuned persona providing emotional support for "tattoo regret" and structured care routines.

---

## 🗺️ User Journeys

### Journey A: The Creator (New Ink)
1. **Inspiration:** User lands on the Hero page and scrolls through curated galleries of Quotes, Pets, or Icons.
2. **Configuration:** User selects "Pet Portrait," uploads a photo of their dog, and selects "Geometric" style.
3. **Generation:** The app calls the image generation API.
4. **Finalize:** User views the result, downloads the design, and downloads a separate "Stencil" version for their artist.
5. **Preparation:** User checks the "Pain Map" to decide where to place the tattoo.

### Journey B: The Healer (Aftercare)
1. **Concern:** User has a 3-day old tattoo that feels hot.
2. **Consultation:** User enters the "Maintenance" tab and selects "My tattoo looks concerning."
3. **Analysis:** User uploads a photo. The AI analyzes the image data.
4. **Response:** The AI identifies signs of inflammation, advises a specific cleaning routine, and flags if a doctor visit is needed.

---

## 🏗️ Technical Architecture & Data Workflow

### Tech Stack
- **Frontend:** React 18, TypeScript, Tailwind CSS.
- **AI Logic (LLM & Vision):** Google Gemini API (`gemini-2.5-flash`).
- **Image Generation:** Runware API (Fast Stable Diffusion inference via WebSocket).

### Data Flow Diagrams

#### 1. Image Generation Pipeline
```mermaid
[User Input] -> [Frontend Prompt Engineering] -> [Runware WebSocket]
                                                      |
                                              [RealVisXL Model]
                                                      |
[User Display] <- [Image URL] <-----------------------+
```

#### 2. Ink Guardian Analysis Pipeline
```mermaid
[User Image/Text] -> [Frontend Service] -> [Google Gemini API]
                                                 |
                                         (Multimodal Analysis)
                                         1. Check Safety/Medical
                                         2. Generate Empathetic Response
                                                 |
[Chat Interface] <- [Structured Text] <----------+
```

---

## 🛠️ Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/leta-ink-studio.git
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Variables**
   Create a `.env` file in the root directory. You need keys for Google Gemini and Runware.
   ```env
   # Google Gemini API (For Chat, Vision, Text generation)
   API_KEY=your_google_genai_key
   
   # Runware API (For Image Generation)
   RUNWARE_API_KEY=your_runware_api_key
   ```

4. **Start the application**
   ```bash
   npm start
   ```

## 📂 Project Structure

```
/
├── public/              # Static assets
├── src/
│   ├── components/      # UI Components
│   │   ├── Hero.tsx     # Horizontal scroll galleries
│   │   ├── NewTattooTool.tsx # Generation Logic
│   │   ├── OldTattooTool.tsx # Chat & Analysis Logic
│   │   └── PainMap.tsx  # Interactive Visualization
│   ├── services/
│   │   └── geminiService.ts # API Wrappers (Gemini & Runware)
│   ├── types.ts         # TypeScript Interfaces
│   ├── App.tsx          # Main Router/Layout
│   └── index.tsx        # Entry point
└── README.md
```

## 🛡️ Disclaimer
This application uses AI for health-related suggestions (tattoo healing). It is **not** a substitute for professional medical advice. The "Medical Alert" feature is heuristic-based and should be treated as guidance, not a diagnosis.
