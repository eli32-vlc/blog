---
date: 2025-06-18T19:58:43+1000
title: Moving on from VLESS to VMESS
description: School Wi-Fi intercepts TLS; switched to VMESS for encryption.
---
![Banner](https://files.catbox.moe/b1feka.png)

Recently I moved from VLESS to VMESS due to a couple of reasons. First things first, we need to understand how TLS works.

## How TLS Works

1. Client says hello and offers encryption options  
2. Server replies with chosen options and its certificate  
3. Client checks the certificate  
4. Client and server agree on a secret key  
5. Client switches to encrypted mode  
6. Server switches to encrypted mode  
7. Secure communication starts  

From ChatGPT btw, TLS is the successor to SSL. But people often refer to SSL as TLS—it works, but let you know it's not the same.

## School Wi-Fi and WPA2-Enterprise

Let’s get into the story. My school's Wi-Fi network uses something called WPA2-Enterprise. It’s an enterprise version of WPA2, as the name suggests. It uses a username and password instead of a pure password. This is better for logging purposes than a pure password, which is something I do not like because I value **PRIVACY**. Okay, it's fine if they log my connection, I could use something like VLESS to protect myself, right?

## Custom CA Certificate Warning

The first time I connected to the school Wi-Fi network, a warning popped up asking me if I wanted to install a custom CA certificate. I clicked yes and didn’t think much of it. When I started to use VLESS with TLS and WebSockets, some major thoughts popped up. Can my school see what I am doing through an encrypted proxy? And even worse, save my traffic and decrypt it later?

## Why Schools Install Custom CA Certs

First things first, why do schools or companies make you install a custom CA cert? A certificate like `firewall.schoolname.com` (that’s like my certificate btw). This certificate basically tells your device to trust `firewall.schoolname.com`—says it's legit.

Okay, it’s fine I guess, maybe it’s just for Wi-Fi authentication?

## Discovery of TLS Interception

When I dug deeper, I noticed something concerning. Let’s say I opened `https://duckduckgo.com`. When I checked my browser certificate information, instead of DuckDuckGo's own certificate, it was my `firewall.schoolname.com` certificate. So I tried uninstalling the certificate. When I uninstalled it, I got an HSTS error.

At this point, I knew I was **COOKED**.

## Man-in-the-Middle Attack in Action

**How it works fully:**

1. I go to `https://duckduckgo.com`  
2. My school's "firewall" (which is actually a powerful Next-Generation Firewall acting as an intercepting proxy) grabs my request.  
3. It then makes its own secure connection to the real DuckDuckGo  
4. Then, it generates a brand new, fake certificate for `https://duckduckgo.com` (signed by `firewall.schoolname.com`) and sends that back to my device.  
5. Since I've installed their custom CA certificate, my device trusts this fake certificate, thinks everything is fine, and encrypts my data to the school's proxy.  
6. The proxy then decrypts my data, inspects it, re-encrypts it, and sends it to the real `https://duckduckgo.com`. And it does the same thing in reverse for the response.  

They are sitting in front of every single **encrypted** connection, seeing EVERYTHING and passing it through.

## Why This Matters

**Why is this important?**

This is very important because VLESS has no built-in encryption. Instead, it relies on TLS, which is already compromised in this scenario.

You mfs already telling me how I selected “trust insecure certificates”? Well, the thing is that they are trusting it without “trust insecure certificates” because the fake certificate is stored in the Keychain Access. I also didn’t know this was happening because everything was connecting successfully without any problem.

Oh, you don’t have PFS??? **DONT MATTER**—they are actively decrypting it, so you are cooked. Womp womp.

## Solving This Problem

**Solving this problem**

Easy—switch to VMESS. It has a layer of custom encryption on top using AES-128-GCM or ChaCha20-Poly1305, which is the gold standard and good enough. So we are wrapping the WS connection inside TLS. Inside that WS connection is the VMESS payload. Inside the VMESS payload, we have the destination site, which also uses its own TLS encryption.

A quick reminder that there is an unknown exploit in your privacy setup, and you should look out for them. Custom CAs are very powerful—please look out for them. In my scenario, it means that without the CA = no internet. Also, my school uses a custom DNS server which does not allow us to change to Cloudflare. If you try, the internet wouldn’t work after changing. Please correct me if I am wrong in any part of this article.

## Final Thoughts

**Stay safe out there.** 

> Grammar and spelling fixed by AI. Original text written by Zenith which is a human.
