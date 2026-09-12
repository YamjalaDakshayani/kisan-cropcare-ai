# 🌾 Kisan CropCare AI (కిసాన్ క్రాప్‌కేర్ AI)

> **AI-Powered Crop Condition Checking Assistant for Indian Farmers**  
> Complete Hackathon-Ready Web Application with Mobile-First Camera Detection, Live Stream Analysis, Multi-Lingual Support (7 Indian Languages), and Voice Assistant.

---

## 🚀 Key Features

1. **📸 Mode 1 — Check Crop by Photo**:
   - Capture directly with smartphone camera or upload leaf images.
   - Diagnoses: Crop type, disease, pest infestation, nutrient deficiency, leaf discoloration, and overall health.
   - Instant farmer-friendly report with symptoms, safe organic remedies, confidence rating, and advisory.
   - Built-in **1-tap Demo Sample Leaves** (Tomato Blight, Rice Blast, Chilli Leaf Curl, Healthy Leaf) for instant hackathon demonstrations without needing a live field or plant!

2. **📹 Mode 2 — Live Crop Check**:
   - Direct access to smartphone rear/environment camera (`navigator.mediaDevices.getUserMedia`).
   - Periodic frame capture (every 3.5 seconds) to avoid API quota waste.
   - Real-time overlay status banner directly over the camera feed:
     - 🟢 *Crop looks healthy*
     - 🟡 *Possible nutrient deficiency detected*
     - 🔴 *Possible disease detected*
   - Mini information panel displaying Crop, Condition, Health Status, and Confidence.
   - "Capture Result" converts the live scan into a full shareable report.

3. **🌐 7 Indian Languages Localization**:
   - **English**, **Telugu (తెలుగు)**, **Hindi (हिन्दी)**, **Tamil (தமிழ்)**, **Kannada (ಕನ್ನಡ)**, **Marathi (मराठी)**, **Bengali (বাংলা)**.
   - Full translation of all UI elements, diagnosis reports, symptoms, actions, and speech output.

4. **🗣️ Voice Assistant (STT & TTS)**:
   - **Voice Input**: Farmer can speak questions using the microphone button in their native language (Telugu, Hindi, Tamil, etc.).
   - **Voice Output (🔊 Listen)**: Audio readout of any diagnosis or chat response in the selected language using Web Speech API with graceful fallback.

5. **🤖 Ask Kisan AI (Agri Advisory Chatbot)**:
   - Interactive farm chatbot for questions regarding pest control, fertilizers, watering schedules, and soil care.
   - Quick prompt chips for fast access to frequent questions.

6. **📊 Farmer Dashboard & History**:
   - Recent Scans history saved in `localStorage` with detailed past inspection modal.
   - Live Farm Weather & Agricultural Spray Advisory (humidity, wind, safe spraying hours).
   - Emergency Kisan Call Centre Hotline: Toll-Free **1800-180-1551**.

7. **🛡️ Safety & Reliability**:
   - Safety disclaimers on every report advising preliminary assessment and expert consultation.
   - Automatic **Demo / Mock Mode** when no `AI_API_KEY` is provided, ensuring 100% reliable hackathon presentation.

---

## 📁 Project Structure

```
Kisan crop care/
├── client/                     # Frontend (React + Vite + Tailwind CSS)
│   ├── src/
│   │   ├── components/
│   │   │   ├── Header.jsx           # Top bar & navigation
│   │   │   ├── LanguageSelector.jsx # 7 Indian languages dropdown
│   │   │   ├── DisclaimerBanner.jsx # Agricultural safety disclaimer
│   │   │   ├── PhotoScanner.jsx     # Mode 1: Photo capture & upload
│   │   │   ├── LiveScanner.jsx      # Mode 2: Live camera scanner
│   │   │   ├── CropResult.jsx       # Diagnostic card & audio readout
│   │   │   ├── FarmerChat.jsx       # Ask Kisan AI chatbot with voice
│   │   │   ├── ScanHistory.jsx      # Scan logs & detail modal
│   │   │   └── WeatherWidget.jsx    # Agricultural spray advisory
│   │   ├── constants/
│   │   │   └── translations.js      # Complete 7-language dictionary
│   │   ├── pages/
│   │   │   ├── Home.jsx             # Hero landing page
│   │   │   └── Dashboard.jsx        # Farmer stats & saved reports
│   │   ├── services/
│   │   │   ├── apiService.js        # Backend HTTP client
│   │   │   ├── voiceService.js      # Speech-to-Text & Text-to-Speech
│   │   │   └── storageService.js    # LocalStorage manager
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── index.html
│   ├── vite.config.js          # Configured with proxy to port 5000
│   └── tailwind.config.js
│
├── server/                     # Backend API (Node.js + Express)
│   ├── routes/
│   │   ├── analyze.js          # /api/analyze/photo & /api/analyze/live-frame
│   │   ├── chat.js             # /api/chat
│   │   └── weather.js          # /api/weather
│   ├── services/
│   │   ├── visionService.js    # Google Gemini Vision integration
│   │   ├── mockDataService.js  # Rich multi-lingual fallback engine
│   │   └── aiChatService.js    # Agri advice AI service
│   ├── index.js                # Express entry point
│   └── .env.example
│
├── .env.example
├── package.json                # Root orchestration scripts
└── README.md
```

---

## 🛠️ Step-by-Step Installation & Setup

### Prerequisites
- [Node.js](https://nodejs.org/) (version 18+ recommended, tested on Node v24)
- npm

### 1. Install Dependencies

You can install all dependencies across the server and client with one command:
```bash
# In the root directory:
npm run install:all
```
Or install separately:
```bash
# 1. Install root dependencies
npm install

# 2. Install server dependencies
cd server
npm install

# 3. Install client dependencies
cd ../client
npm install
```

---

## 🔑 Configure AI API Key (Google Gemini)

The application works **immediately out-of-the-box in Demo Mode** even without an API key!

To enable real-time Gemini Vision AI:
1. Open `server/.env` (or copy from `server/.env.example`):
   ```bash
   cp server/.env.example server/.env
   ```
2. Paste your Google Gemini API key:
   ```env
   PORT=5000
   AI_API_KEY=AIzaSy...your_gemini_api_key_here...
   GEMINI_MODEL=gemini-1.5-flash
   ```

*Note: The frontend never exposes secret API keys. All calls route securely through the Express backend.*

---

## 🏃 Running the Application

### Option A: Run Both Together (Recommended)
From the root directory:
```bash
npm run dev
```
This runs the backend on `http://localhost:5000` and the frontend on `http://localhost:3000` concurrently.

### Option B: Run Separately
**Terminal 1 (Backend):**
```bash
cd server
npm run dev
```
*(Server listens on `http://localhost:5000`)*

**Terminal 2 (Frontend):**
```bash
cd client
npm run dev
```
*(Vite dev server starts on `http://localhost:3000`)*

Open your browser and navigate to: **`http://localhost:3000`**

---

## 🧪 Testing Guide for Hackathon Demos

### 1. Testing Multi-Language Switch
- Click the language badge at the top-right (e.g. **తెలుగు**, **हिन्दी**, **English**, etc.).
- Switch between Telugu, Hindi, Tamil, Kannada, Marathi, Bengali, and English.
- Notice that all buttons, diagnosis labels, symptoms, and voice readouts instantly update.

### 2. Testing Mode 1: Check Crop by Photo
- On the Home page, click **“📸 CHECK CROP BY PHOTO”**.
- **Option A (Camera)**: Click **“Open Camera”**, grant permission, aim at a plant, and click the capture circle.
- **Option B (File Upload)**: Click **“Upload from Gallery”** and choose any crop leaf photo.
- **Option C (Instant Demo Sample)**: Under the photo card, click any of the preset sample leaves (*Tomato Blight*, *Rice Blast*, *Chilli Leaf Curl*, or *Healthy Crop*).
- Click **“Analyze Crop Health”**.
- Watch the AI laser scanning animation beam across the photo.
- Examine the generated report: Crop, Condition, Health Status, Confidence %, Observed Symptoms, and Actionable Recommendations.
- Click **🔊 “Listen in [Language]”** to test native voice playback!
- Click **“Save Report”** to add to your permanent Dashboard.

### 3. Testing Mode 2: Live Crop Check
- On the Home page, click **“📹 LIVE CROP CHECK”**.
- Click **“Open Camera”**.
- Click **“Start AI Scan”**.
- Notice the live streaming video feed and the periodic scanning pulse.
- Observe the real-time overlay badge floating directly over the camera feed (e.g. 🟢 *Crop looks healthy* / 🟡 *Possible nutrient deficiency* / 🔴 *Possible disease detected*).
- Observe the live mini info panel below the camera updating with Crop, Condition, and Confidence.
- Click **“Capture Full Report”** to open the full detailed advisory.

### 4. Testing Voice Input & Ask Kisan AI
- On the Home page or navigation bar, click **“🎙️ ASK KISAN AI”**.
- Click the **🎙️ Microphone button**.
- Speak a farming question in your chosen language (e.g. *"My paddy leaves are turning yellow. What should I do?"* or in Telugu/Hindi).
- View the real-time transcribed text.
- Hit **Send** and receive practical, farmer-friendly agricultural advice.
- Click the **🔊 Listen** button on the AI response to hear the audio readout.

### 5. Testing Dashboard & History
- Click **“Dashboard”** in the navigation bar.
- View total scans, healthy crop counters, and attention alerts.
- Check the **Farm Weather & Spray Advisory** widget (safe spraying hours, humidity, rain chance).
- In the **Recent Crop Scans** list, click on any past scan to inspect its full diagnosis modal.

---

## 🌐 Production Deployment

### Backend Deployment (Render / Railway / Heroku / AWS EC2)
1. Set the root directory to `server/`.
2. Add Environment Variables:
   - `PORT=5000`
   - `AI_API_KEY=your_gemini_key`
   - `GEMINI_MODEL=gemini-1.5-flash`
3. Build & start command: `npm start`.

### Frontend Deployment (Vercel / Netlify)
1. Set root directory to `client/`.
2. Build command: `npm run build`.
3. Output directory: `dist`.
4. In `vite.config.js` or through environment variable `VITE_API_URL`, point the API requests to your deployed backend URL.
