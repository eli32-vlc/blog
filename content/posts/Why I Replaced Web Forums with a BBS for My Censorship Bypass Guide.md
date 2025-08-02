---
title: Why I Replaced Web Forums with a BBS for My Censorship Bypass Guide
date: 2025-08-02T19:30:04+1000
description: Lightweight, terminal-based forum system with encryption and minimal resource usage.
---
![Banner](https://files.catbox.moe/oguttb.png)
These days, forums are centralized and heavily moderated. Places like Reddit have heavy restrictions on topics. You might ask, "Why don't I self-host a forum?" Well, the thing is that traditional forums are insecure if you don't set them up correctly. Sometimes they have tracking via JSDelivr or Cloudflare CDN.

Back in the BBS days, none of these things existed—it was just pure content. Also, with a traditional forum, it's resource-heavy and hard to back up. Sure, flat-file forums exist, but they are low-performance and have fewer features.

BBS, on the other hand, supports MRC (multi-relay chat), forum topics, file uploads, etc., all from the comfort of the terminal, so you don't even have to open Firefox or Chrome to use the forum.

With a BBS, it's a lot easier to back up—just write a script to 7zip the entire directory with the SQLite file inside, add encryption, then upload it to some cloud providers. BBS over SSH makes it encrypted from the client to the BBS server, ensuring no one can see in between. BBS is fast, which makes it great for hosting forums due to the low bandwidth requirements.