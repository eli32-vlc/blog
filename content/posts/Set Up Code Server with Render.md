---
title: "Set Up Code Server with Render"
date: 2025-06-15T08:50:32+1000
---

![Banner](https://files.catbox.moe/reyiel.png)
### What is Code Server?

It's just VS Code in a browser, but with a terminal and environment to run your code.

### Important Considerations:

1. **Data Loss Warning**: You will lose all your data and dependencies if you don't keep the tab open for more than 5 seconds—unless you use UptimeRobot, which can keep your instance alive and preserve data for up to a month. If using UptimeRobot, set it up on a new account without any other monitored services.
2. **Bandwidth Limit**: Render has a 10GB outbound bandwidth limit. You must not exceed this. "Outbound" means traffic going out—for example, downloading packages or files. Once the limit is exceeded, you can simply redeploy the instance, but **your data will be lost**.
3. **System Resources**: The free tier includes 512MB of RAM and 0.1 CPU.

---

### How to Deploy It:

1. Open your [Render Dashboard](https://dashboard.render.com/).
2. Click **"Add New"**.
3. Select **"Web Service"**.
4. Click **"Public Git Repository"**.
5. Paste in:
`https://github.com/eli32-vlc/code-server-dockefile`
6. (Optional) Choose your preferred region.
7. For **Instance Type**, select **Free**.
8. Click **"Deploy Web Service"**.

Scroll down to **Environment Variables**, click **"Add from .env"**, and paste:

    PASSWORD=YOURCUSTOMPASSWORD


> Replace `YOURCUSTOMPASSWORD` with your own custom password.

---

### Set Up UptimeRobot

1. Go to [UptimeRobot](https://uptimerobot.com/) and log in.
2. Add a new monitor and paste in your instance URL.
3. Set the check interval to **5 minutes**.

---

Now you can visit your instance URL and start working.

---

> Spelling and grammar corrected by AI. Original concept remains the same.
