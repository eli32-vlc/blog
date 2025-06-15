---
title: "Free VPS with Render"
date: 2025-06-15T08:50:32+1000
description: "Step-by-step guide to creating a free VPS on Render using Docker and a web terminal."
---

![Banner](https://files.catbox.moe/r8gz9i.png)
**Important Notice:**
This is a new hack I discovered, so please **do not share** it publicly to avoid it being patched.

### Why Use Render as a VPS Provider?

Render is an excellent choice because it's **free** and doesn't require a credit card. However, since Render restricts terminal access behind a paywall, we'll need to get creative. Our solution is to run a **Linux Docker container** with a **web terminal**, secured by **HTTP basic authentication**. This method ensures we have some security while still keeping the service free.

### Key Considerations:

- **Data is wiped monthly** because Render is a stateless service.
- If you exceed **10GB of outbound bandwidth** (e.g., downloading files inside your VPS), your data will be wiped, and the instance will be suspended.
- **No SSH access** with port forwarding is available. SSH access can only be achieved using **ngrok**.
- This setup currently supports **Alpine Linux **and** Ubuntu** only.
- You can use **ngrok** for port forwarding to run proxies, remote desktops, and more.
- You can use **screen** to keep apps running in the background.
- Ubuntu currently don't have **ngrok** due to some bugs.

---

### Getting Started

1. **Log in to Render** and click on **"Add New"**.
2. Select **Web Service** from the dropdown menu.
3. Choose **Public Git Repo**.
4. Paste the following URL: [https://github.com/eli32-vlc/web-terminal](https://github.com/eli32-vlc/web-terminal)
5. Set the environment to **Docker**.
6. Choose the region where you'd like your VPS to be hosted.
7. For the **Dockerfile Path**, use:
- For **Ubuntu**: `amd64/ubuntu/Dockerfile`
- For **Alpine**: `amd64/alpine/Dockerfile`

8. For **Instance Type**, select **Free**.
9. Click **Deploy Web Service**.

Under **Environment Variables**, click “**Add from .env**” and paste the following:

    TTYD_USER=myuser
    TTYD_PASS=mypassword
    PORT=7681


Replace `myuser` with your desired username and `mypassword` with a secure password.

---

### After Deployment:

Once your service is deployed, you will receive a URL like:

    https://web-terminal-xxxx.onrender.com


Wait for the build and deployment process to complete.

Next, sign up for **UptimeRobot** and add your newly created URL:

    https://web-terminal-xxxx.onrender.com


Set the check interval to **every 5 minutes** to keep your container alive and prevent data wipes due to inactivity.

---

### You're Ready to Go!

Visit your instance URL, log in with the username and password you set, and enjoy your new, free VPS!

---

**Disclaimer:** While this content has been edited for spelling and grammar by AI, the underlying method and concept are original.
