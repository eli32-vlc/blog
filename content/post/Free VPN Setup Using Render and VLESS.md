![VLESS Banner](https://files.catbox.moe/90yuw9.png)

Free VPN Setup Using Render and v2Ray

This guide outlines a method for setting up a free VPN using Render, v2Ray, and a related script.  It's based on techniques used for censorship bypassing.

**Understanding the Approach:** This method leverages Render’s free tier and v2Ray's protocol to create a VPN instance.  The script provided is designed to help evade keyword detection used by services like Render to block access to VPN services. Do not use torrent or doing anything illegal on it.

**Prerequisites:**

1.  **Render Account:** You'll need a Render account. While credit cards aren’t always required, be aware that Render may monitor activity and could suspend your account if they detect suspicious behavior.

2.  **Script:** You'll need the script from this GitHub repository: [https://github.com/eli32-vlc/scrper](https://github.com/eli32-vlc/scrper)

**Setup Instructions:**

1.  **Create a New Instance on Render:** Launch a new instance within your Render account.

2.  **Configure the Instance:**
    *   **Repository:** Select “Public Git” and paste the repository URL into the field.
    *   **Location:** Set the location to a server geographically close to you.
    *   **Building Command:** Change the building command to `npm install`.
    *   **Instance Type:** Select “Free.”

3.  **Add .env Variables:** Scroll down to the `.env` section and click “Add from .env”.

4.  **Paste Variables:** Paste the following variables into the `.env` file:

    ```
    DISCORD_WEBHOOK_URL=YOUR_DISCORD_WEBHOOK_URL  # Replace with your Discord webhook URL
    PORT=443
    REFRESH_UUID_INTERVAL=300000
    SPEED_LIMIT_MBPS=200 (Adjust as needed)
    UUID_LIST_URL=https://pastebin.com/raw/PASTEBIN ID  # Replace with your Pastebin URL
    ```

5. **UUID List:** You'll need a list of UUIDs, formatted with one UUID per line in a text file or Pastebin.  Copy the raw Pastebin URL and paste it into the `UUID_LIST_URL` variable.

6.  **Deploy Web Service:** Click “Deploy Web Service” to initiate the deployment process.

7.  **Client Setup:** Use clients like Hiddify, NeKoray (archived), or v2RayN to connect to your VPN.

8. **Connection Settings:** Configure the client with these settings:
    *   **Address:** `sm.onrender.com` (or your specific Render domain)
    *   **Port:** 443
    *   **Network:** WS (WebSocket)
    *   **SNI:**  Set to the same as your address.
    *   **Path:** /

9. **Activate VPN:** Activate the VPN connection through your chosen client.

#### Used AI for fixing spelling grammar.
