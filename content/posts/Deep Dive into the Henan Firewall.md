---
title: Deep Dive into the Henan Firewall
date: 2025-06-16T09:34:00:z
description: Henan has its own internet firewall now, blocking more sites than China’s national system, the GFW.
---
![Banner](https://files.catbox.moe/g6ujml.png)

For decades, censorship in China has been enforced through the Great Firewall (GFW), developed by the Cyberspace Administration of China. The GFW commonly uses DNS poisoning, TCP RST packets to block websites, and Deep Packet Inspection (DPI) to analyze network traffic. However, a recent research paper published in May 2025 revealed that the Chinese province of Henan has deployed its own regional censorship firewall. Since August 2023, the Henan firewall has been analyzing network packets originating from the province and has blocked over five times as many websites as the GFW, generally targeting generic second-level domains such as .com.au. Unlike the GFW, which may inject multiple packets to disrupt connections, the Henan firewall uses a distinctive TCP RST+ACK packet. Notably, a full TCP handshake is not required for a website or traffic to be blocked, meaning it can send the RST+ACK packet during the initial traffic pattern. Similar to the GFW, it monitors all TCP ports for TLS traffic, which is commonly used for HTTPS, leaving no ports safe.

The Henan firewall only censors outbound traffic—connections originating from inside the province—and shows about a 9% overlap in its block list with the GFW. The motivation behind this firewall appears unusual, as it mainly targets domains related to "Business," "Economy," "Computer," and "Internet Information," possibly indicating local economic concerns in Henan. While it blocks more domains than the GFW, researchers have discovered a potential client-side bypass, possibly similar to tools like GoodbyeDPI, which fragment or alter data packets to evade detection by censorship systems. Nevertheless, this development marks a significant shift in censorship within China, potentially signaling a move from a centralized model to a decentralized one that could be replicated in other regions.

Research Paper: [Link](https://gfw.report/publications/sp25/en/)

> AI used to fix spelling and grammar issues. Original text was written by Zenith as a human.
