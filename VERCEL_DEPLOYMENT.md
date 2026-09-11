# 🚀 Vercel-ல் Deploy செய்வதற்கான வழிகாட்டி (Deployment Guide)

இந்த ப்ராஜெக்ட்டை உங்கள் **VS Code**-லிருந்து **Vercel**-க்கு எளிதாக Deploy செய்ய அனைத்து configurations (`vercel.json`, `api/index.ts`) தயார் செய்யப்பட்டுள்ளன.

---

## 📌 முறை 1: VS Code Terminal வழியாக நேரடி Deployment (மிகவும் எளிதானது - 2 நிமிடங்கள்)

### படி 1: VS Code-ல் Terminal திறக்கவும்
VS Code-ல் `Ctrl + ~` (அல்லது `Terminal` > `New Terminal`) அழுத்தவும்.

### படி 2: Vercel CLI இயக்கவும்
Terminal-ல் பின்வரும் கட்டளையை (command) உள்ளிடவும்:
```bash
npx vercel
```
- உங்கள் Vercel அக்கவுண்டில் login செய்யக் கேட்கும் (GitHub / Email தேர்வு செய்யலாம்).
- தொடர்ந்து வரும் கேள்விகளுக்கு `y` கொடுத்து Enter அழுத்தவும் (Default settings-ஐ அப்படியே ஏற்றுக்கொள்ளலாம்):
  - *Set up and deploy?* `y`
  - *Which scope do you want to deploy to?* (உங்கள் பெயர் / அக்கவுண்ட் வரும், Enter)
  - *Link to existing project?* `n`
  - *What's your project's name?* (விரும்பிய பெயர் அல்லது Enter)
  - *In which directory is your code located?* `./` (Enter)
  - *Want to modify settings?* `n` (Enter)

### படி 3: Gemini API Key சேர்க்கவும்
AI Chatbot மற்றும் Resume Screening வேலை செய்ய உங்கள் Gemini API Key தேவை:
```bash
npx vercel env add GEMINI_API_KEY
```
- Value கேட்கும் போது உங்கள் Gemini API Key-ஐ பேஸ்ட் செய்யவும்.
- Environment கேட்கும் போது: `Production`, `Preview`, `Development` மூன்றையும் விசைப்பலகை Spacebar அழுத்தி தேர்வு செய்து Enter அழுத்தவும்.

### படி 4: Production-ல் Deploy செய்யவும்
```bash
npx vercel --prod
```
வாழ்த்துகள்! சில விநாடிகளில் உங்கள் நேரடி இணையதள முகவரி (`https://your-app-name.vercel.app`) வந்துவிடும்! 🎉

---

## 📌 முறை 2: GitHub வழியாக Vercel-ல் Deploy செய்தல் (Recommended)

### படி 1: VS Code-ல் இருந்து GitHub-க்கு Push செய்யவும்
VS Code Terminal-ல்:
```bash
git init
git add .
git commit -m "Initial commit for Vercel deployment"
git branch -M main
git remote add origin https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>.git
git push -u origin main
```

### படி 2: Vercel Dashboard-ல் Import செய்யவும்
1. [vercel.com](https://vercel.com) சென்று உங்கள் கணக்கில் லாகின் செய்யவும்.
2. **Add New...** > **Project** கிளிக் செய்யவும்.
3. உங்கள் GitHub repository-ஐக் கண்டுபிடித்து **Import** கொடுக்கவும்.
4. **Environment Variables** பிரிவை விரித்து:
   - Key: `GEMINI_API_KEY`
   - Value: உங்கள் Gemini API Key
   - **Add** பட்டனை கிளிக் செய்யவும்.
5. **Deploy** பட்டனை அழுத்தவும்.

---

## ⚙️ ப்ராஜெக்ட்டில் இணைக்கப்பட்டுள்ள கோப்புகள் (Config Files):

1. **`vercel.json`**:
   - Vercel Serverless Function மற்றும் Vite Single Page Application (SPA) ரூட்டிங்கை தானாக இணைக்கிறது.
   - `/api/*` கோரிக்கைகளை `api/index.ts`-க்கும், மற்ற கோரிக்கைகளை `index.html`-க்கும் வழிநடத்துகிறது.
2. **`api/index.ts`**:
   - Vercel Serverless Function Entry Point.
3. **`src/server/app.ts`**:
   - அனைத்து Backend API Routes (Resume Screening, TF-IDF NLP, Gemini AI Chatbot, Resume Ideas).
4. **`server.ts`**:
   - உங்கள் கணினியில் (`npm run dev`) இயக்கும்போது Port 3000-ல் செயல்படும் Local Development Server.

---

## 💻 உங்கள் கணினியில் (Local) இயக்க:
```bash
npm install
npm run dev
```
உலாவியில் (Browser) `http://localhost:3000` சென்று பார்க்கலாம்.
