---
title: "Self-Host IP Logger Using Render"
date: 2025-06-15T08:50:32+1000
description: "How to self-host an IP logger on Render with Discord integration and a simple web UI."
---

![Banner](https://files.catbox.moe/wi79f7.png)
## Important Considerations

1. Your URL will stop working after 5 minutes if you host other services on the same account. My suggestion is to create multiple accounts for each service, as Render has an instance time limit per month.
2. You need to have a Discord account and a Discord server.
3. You can't deactivate URLs after they have been sent.
4. There is a web UI to help you set up links.
5. Feel free to disguise this as an image hosting site.

---

### How to Set Up

1. Create a new web service.
2. Click on **"Build and deploy from a Git repository."**
3. Click **"Next."**
4. Scroll down until you see **"Public Git repository."**
5. Paste in this URL: `https://github.com/eli32-vlc/ip-logger.git`
6. Click on **"Continue."**
7. Change **"Instance Type"** to **"Free."**
8. Scroll to **"Environment Variables."**
9. Log in to Discord, create a new server, and generate a webhook for that server.
10. Click **"Add from .env"** and paste the following:

    URL_SHORTENER_USERNAME='Admin Username'
    URL_SHORTENER_PASSWORD='Admin Password'
    DISCORD_WEBHOOK_URL='WEBHOOK'


1. Replace `'Admin Username'` with your own username.
2. Replace `'Admin Password'` with your own password.
3. Replace `'WEBHOOK'` with your Discord webhook URL.
4. Click on **"Deploy Web Service."**
5. Click the link and log in.

---

### License

**Non-Commercial License (CC BY-NC 4.0)**

This project is licensed under the [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/) license.

You are free to:

- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material

**Under the following terms:**

- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
- **Non-Commercial** — You may not use the material for commercial purposes.

For the full license, see [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).

---

### Commercial License

For commercial use of this software, you must obtain a commercial license.
Please contact **Zenith Rifle** at first@sharecrypt.uk to discuss licensing terms and fees.

---

**Note:** You can attach a custom domain in Render.

> Used AI for formatting and spelling. The original concept remains unchanged.
