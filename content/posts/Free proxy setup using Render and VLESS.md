---
title: "Free proxy setup using Render and VLESS"
date: 2025-06-15T08:50:32+1000
description: "Guide to setting up a free, censorship-resistant proxy using Render and the VLESS protocol."
---

![Banner](https://files.catbox.moe/90yuw9.png)

This is based on my censorship bypass guide. You may have heard me mention that I use Render for my VPN. This setup is built on top of the VLESS protocol developed by V2Ray — a highly effective protocol for bypassing censorship.

Each instance has a 10GB limit, but you can delete and redeploy the instance to reset the limit. The code is obfuscated to avoid keyword detection enforced by Render. Since Render is a web hosting platform, governments blocking Render will block all sites hosted on it. However, if only your specific address is blocked, you can simply redeploy your instance to get a new domain name.

Any email address should work, but if you're privacy-conscious, consider using a custom email. This also allows you to register multiple accounts. Make sure to sign up for Render using a **home IP address** — if they detect a datacenter IP, they may ask for a credit card.

> ⚠️ This method is not widely known, so please don't share it publicly to prevent it from being patched.

---

### Steps:

1. Create a [Render](https://render.com) account. No credit card is required, but make sure to sign up using your home IP.
2. Remember this repo URL: [https://github.com/eli32-vlc/scrper](https://github.com/eli32-vlc/scrper)
3. Create a new **Web Application/Service** instance on Render.
4. Choose "Public Git Repository" and paste in the repo URL.
5. Leave everything unchanged **except**:
- Choose a location close to you.
- Change the **Build Command** to: `npm install`
- Set the instance type to **Free**

6. Scroll down and click **"Add from .env"**
7. Paste in the following environment variables:
```
    DISCORD_WEBHOOK_URL=your Discord webhook
    PORT=443
    REFRESH_UUID_INTERVAL=300000
    SPEED_LIMIT_MBPS=200  # (Change if desired)
    UUID_LIST_URL=https://pastebin.com/raw/PASTEBIN_ID
```

1. You’ll need a list of UUIDs, one per line, hosted publicly (e.g., in Pastebin or a raw `.txt` file). Copy the **raw** URL and paste it into `UUID_LIST_URL`.
2. Click **Deploy Web Service**

---

### Set Up the Client

You can use:

- Hiddify
- Nekoray (archived)
- V2RayN

**Configuration:**

- **Address:**`your-app-name.onrender.com`
- **Port:**`443`
- **UUID:** one of the UUIDs from your list
- **Network:**`WS`
- **SNI:** same as address
- **Path:**`/`

---

✅ You’re good to go! Save your `.env` settings in a text file for faster future deployment.

---

**Disclaimer:**
>AI was used to correct grammar and spelling. The original logic and content were created by a human.
