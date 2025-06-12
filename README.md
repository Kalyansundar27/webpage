# Europe Trip Planner Webpage

This repository contains `europe_trip.html`, an interactive itinerary planner that uses the Google Gemini API for optional AI features.

## Serving the Page
Use a local web server so the scripts can load correctly. Two easy options are:

1. **npx serve** (requires Node.js)
   ```bash
   npx serve .
   ```
   Then open `http://localhost:3000/europe_trip.html` in your browser (the port shown in the command output may differ).

2. **VS Code Live Server**
   Install the "Live Server" extension, right‑click `europe_trip.html`, and choose **Open with Live Server**.

## Supplying the Gemini API Key
`europe_trip.html` expects a Gemini API key for the AI-powered features. Do **not** commit your key to version control. One approach is:

1. Create a `config.js` file **outside of version control** (add it to `.gitignore` if necessary).
2. Inside `config.js`, define:
   ```js
   const geminiApiKey = 'YOUR_GEMINI_API_KEY';
   ```
3. Include `config.js` in `europe_trip.html` with a `<script src="config.js"></script>` tag before the script that calls the API.
4. Modify the `callGemini` function in the HTML to reference `geminiApiKey` instead of a hard‑coded string.

Alternatively, you could store the key in an environment variable and have a small server script inject it or prompt for it at runtime. The key should never be committed to the repository.

### Using `server.js` and an Environment Variable

1. Set the environment variable `GEMINI_API_KEY` with your key:
   ```bash
   export GEMINI_API_KEY=YOUR_GEMINI_API_KEY
   ```
2. Start the provided server:
   ```bash
   node server.js
   ```
   This serves `europe_trip.html` at `http://localhost:3000` and exposes the key via `config.js`.
3. Open the page in your browser and the AI features will use the key automatically.
