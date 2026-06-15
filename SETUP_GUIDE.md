# ⚡ Thunder Bot - Setup Guide (Hindi)

  ## 🔗 Link Kaise Generate Hoga?

  1. Apne Telegram bot ko koi bhi **file bhejo** (video, document, image, audio)
  2. Bot automatically file ko apne **storage channel** mein save karta hai
  3. Bot aapko ek **direct HTTP link** deta hai jaise:
     `https://your-app.onrender.com/watch/HASH12345/filename.mp4`
  4. Yeh link **kisi ko bhi share** karo — wo seedha browser mein stream ya download kar sakta hai

  ---

  ## 📥 Download / Stream Kaise Hoga?

  - **Stream:** Link browser mein kholo — video/audio seedha play hoga
  - **Download:** Link ke baad `?download=1` lagao ya right-click → Save As
  - **Telegram se fast:** Render server directly Telegram se file stream karta hai, browser ke through — koi app ki zaroorat nahi

  ---

  ## 🚀 Step-by-Step Deploy on Render (FREE)

  ### Step 1: Cheezein Tayar Karo

  | Cheez | Kahan Se | Kya Karna Hai |
  |-------|----------|---------------|
  | API_ID & API_HASH | https://my.telegram.org/apps | Login karo, "API Development" pe jao |
  | BOT_TOKEN | @BotFather | /newbot command do |
  | BIN_CHANNEL | Apna Telegram | Ek private channel banao, bot ko admin banao, channel ID lo |
  | OWNER_ID | @userinfobot | Bot ko message karo, apna ID milega |
  | DATABASE_URL | https://mongodb.com/atlas | Free account → Free cluster → Connect → Connection string |

  ### Step 2: GitHub Pe Upload Karo

  1. GitHub pe jao: https://github.com → **New Repository** banao
  2. Yeh ZIP extract karo, saare files upload karo
  3. Ya GitHub Desktop use karo

  ### Step 3: Render Pe Deploy Karo

  1. https://render.com pe jao → Free account banao
  2. **New** → **Web Service** click karo
  3. GitHub repo connect karo
  4. Settings:
     - **Runtime:** Python
     - **Build Command:** `pip install -r requirements.txt`
     - **Start Command:** `python -m Thunder`
  5. **Environment Variables** mein yeh dalo:

  ```
  API_ID          = (my.telegram.org se)
  API_HASH        = (my.telegram.org se)
  BOT_TOKEN       = (BotFather se)
  BIN_CHANNEL     = (channel ID, jaise -1001234567890)
  OWNER_ID        = (apna Telegram ID)
  DATABASE_URL    = (MongoDB Atlas connection string)
  FQDN            = your-app-name.onrender.com
  HAS_SSL         = True
  NO_PORT         = True
  PORT            = 10000
  PING_INTERVAL   = 840
  ```

  6. **Deploy** karo → 5-10 minute wait karo

  ### Step 4: FQDN Update Karo

  Deploy hone ke baad Render aapko URL dega jaise:
  `thunder-bot-abc123.onrender.com`

  Render dashboard mein:
  - **Environment** → `FQDN` ki value update karo apne actual URL se
  - Save karo → bot restart hoga

  ---

  ## 🔄 Bot Ko 24/7 Jagte Rakhna (UptimeRobot - FREE)

  Render free tier mein bot 15 min baad so jaata hai.
  Bot pehle se har 14 min mein khud ko ping karta hai — lekin bahar se bhi ping chahiye.

  ### UptimeRobot Setup:
  1. https://uptimerobot.com pe FREE account banao
  2. **Add New Monitor** click karo
  3. Settings:
     - **Monitor Type:** HTTP(s)
     - **Friendly Name:** Thunder Bot
     - **URL:** `https://your-app.onrender.com/`
     - **Monitoring Interval:** 5 minutes
  4. **Create Monitor** → ho gaya!

  Ab bot kabhi nahi rukega ✅

  ---

  ## 🤖 Bot Commands

  | Command | Kaam |
  |---------|------|
  | Koi bhi file bhejo | Direct link milega |
  | /batch | Multiple files ke links ek saath |
  | /status | Bot ka status dekho |
  | /users | Total users count (owner only) |
  | /broadcast | Sab users ko message bhejo (owner only) |

  ---

  ## ❓ Mushkilaat?

  - **BIN_CHANNEL error:** Channel ID `-100` se shuru hona chahiye
  - **Bot respond nahi karta:** FQDN sahi set hai kya Render URL se?
  - **MongoDB error:** Connection string mein username/password sahi hai?
  - **Bot file forward nahi karta:** Bot channel mein admin hai?
  