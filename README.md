# ClearPaper (pilot build)

Static site + one Netlify Function acting as a secure server-side proxy to the Google Gemini API.

ClearPaper helps ordinary citizens understand official notices issued by Indian government authorities by converting complex bureaucratic language into structured, actionable summaries or plain-language translations.

---

## Where This Study Is Taking Place

- **Format:** Fully online (no in-person venue required).
- **Study Location / URL:** Participants access the study directly through this link in their web browser:  
  `https://clearpaperbyadityatiwari.netlify.app/?tab=study&code=YOURCODE`
- **Context & Geographic Focus:** The notices tested in this study come from Indian government and municipal offices. Participants can complete the tasks remotely from any smartphone, tablet, laptop, or desktop computer with an internet connection.
- **Administration & Data Processing:** The researcher interface and baseline output generation run online via `https://clearpaperbyadityatiwari.netlify.app/#researcher`. All study responses are collected securely through Netlify Forms.

---

## Architecture & Privacy

- **Server-Side Proxy:** The browser never directly contacts the AI service; all requests route through the Netlify function to protect the API key.
- **Access Gating:** Prevents unauthorized consumption of API credits using an access code.
- **Privacy First:** The function does not log or store uploaded notices or textual data, protecting personal identifiable information (PII).
- **Multimodal Document Processing:** Reads raw text or natively parses documents (PDFs, images) as inline data.

---

## Step-by-Step: How to Get Your Gemini API Key from Google AI Studio

Follow these exact steps to obtain the API key required for your backend:

1. **Open Google AI Studio:**  
   Navigate to [aistudio.google.com](https://aistudio.google.com/) and sign in with your Google account.
2. **Go to API Keys:**  
   In the left sidebar menu, click on **Get API key** (or go directly to [aistudio.google.com/apikey](https://aistudio.google.com/apikey)).
3. **Generate Key:**  
   - Click the blue **Create API key** button.
   - Choose whether to create the key in a **New Project** or select an existing Google Cloud project.
4. **Copy the Key:**  
   Copy the string displayed (starts with `AIzaSy...`). 
   > **Important:** Never commit this key to GitHub, paste it into frontend HTML/JS files, or share it in client-side code.

---

## Deploy & Netlify Setup

### 1. Repository Setup
Push this folder to a GitHub repository and link it to Netlify, or deploy directly via the Netlify CLI:
```bash
netlify deploy --prod
