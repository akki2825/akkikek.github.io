---
title: "Enhancing Privacy and Security of Mozilla Firefox (Draft)"
categories: [computer-science, personal-config]
---

This post highlights a few ways to enhance privacy and security of Mozilla Firefox without using any addons. It is mostly a textual version of [Mental Outlaw's video](https://www.youtube.com/watch?v=xxWXLlfqNAo).

> Recommend: Use a new profile to prevent accidental breakage to your existing profile. Create new profile by typing in `about:profiles`

Start configuring by typing in `about:config`

**Disable WebRTC**

media.peerconnection.enabled = false

**Enable fingerprint resistance**

privacy.resistfingerprinting = true

**Disable 3DES Cypher**

security.ssl3.rsa_des_ede3_sha = false

**Optimize SSL**

security.ssl.require_safe_negotiation = true

**Disable TLS 1.0, 1.1**

security.tls.version.min = 3

tls.version.max = 4

**Disable Zero round trip time**

security.tls.enable_0rtt_data = false

**Disable Automatic Formfill**

browser.formfil.enable = false

**Disable disk caching**

browser.cache.disk.enable = false

browser.cache.disk_cache_ssl = false

browser.cache.memory.enable = false

browser.cache.offline.enable = false

browser.cache.insecure.enable = false

**Disable geolocation services**

geo.enabled = false

**Disable ALL telemetery**

browser.newtabpage.activity-stream.feeds.telemetry = false

browser.pingcentre.telemetry = false

devtools.onboarding.telemetry-logged = false

media.wmf.deblacklisting-for-telemetry-in-gpu-process = false

toolkit.telemetry.archive.enabled = false

toolkit.telemetry.bhrping.enabled = false

toolkit.telemetry.firstshutdownping.enabled = false

toolkit.telemetry.hybridcontent.enabled = false

toolkit.telemetry.newprofileping.enabled = false

toolkit.telemetry.unified = false

toolkit.telemetry.updateping.enabled = false

toolkit.telemetry.shutdownpingsender.enabled = false

**Disable WebGL**

webgl.disabled = true

**Enable first-party isolation**

privacy.firstparty.isolate = true

**Disable TLS false start**

security.ssl.enable_false_start = false

Check the safety of your browser against tracking on [Panopticlick](https://panopticlick.eff.org).
