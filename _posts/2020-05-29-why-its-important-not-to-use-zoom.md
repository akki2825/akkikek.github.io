---
title: "Why its important not to use Zoom"
categories: [computer-science]
---

[Zoom](https://zoom.us/) is all over the place. I'm going to talk about why its important to *not* use Zoom.

> Zoom is a closed-source video conferencing service.

Zoom has come a long way with severe privacy and security issues.
Let's start by exploring where it all started..

[First problem](https://www.tenable.com/blog/tenable-research-advisory-zoom-unauthorized-command-execution-cve-2018-1571) was discovered in 2018. Zoom had vulnerability on all of the desktop application on Windows, MacOS and Linux. This would allow someone who isn't a meeting attendee to hijack the meeting and become the _Host_. The Host gets few scary abilities such as remotely enabling participant's microphone or webcam, send keystrokes and can even share their screen. Sounds like trojan?

Just after a few months, in July 2019, [another security flaw](https://www.theverge.com/2019/7/8/20687014/zoom-security-flaw-video-conference-websites-hijack-mac-cameras) was identified and this time the vulnerability allowed websites access to the webcam on Macbooks. The MacOS version of Zoom used to install a webserver that would take requests that the standard browser would not. There was no notice to the user who installed it, that a webserver would be running on their app. Worse is, the webserver would be left behind even after you uninstall Zoom.


In 2020, [what Zoom’s privacy policy says is worse than "You don’t have any privacy here"](https://blogs.harvard.edu/doc/2020/03/27/zoom/). Zoom shares the data that it gathers from the users with several major companies like Facebook and the user cannot opt out of this _data share_ and you don't even know it's happening.

It uses [encryption](https://support.zoom.us/hc/en-us/articles/201362723-Encryption-for-Meetings) that is more similar to [transport layer security](https://en.wikipedia.org/wiki/Transport_Layer_Security) where they encrypt the [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) and [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol) connections with [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) and this is no way an end-to-end encryption because it still has the access to all of the meetings, audios, and anything that you've sent over that connection once it hits their server.

There are many law-suits pending against Zoom. Some are in regards to the privacy policy where they have shared and sold the data about their users to customers without any consent. Other law suits are in some severe security issues like the users being able to access each others email and contact infowithout giving users heads up as to any of this is happening.

[US government has banned the use of Zoom for government officials](https://arstechnica.com/tech-policy/2020/04/us-senate-tells-members-not-to-use-zoom/) because of all these security flaws and its relationship with China.

_Wait what? Relationship with China?_ [Yes](https://theintercept.com/2020/04/03/zooms-encryption-is-not-suited-for-secrets-and-has-surprising-links-to-china-researchers-discover/). Zoom routes many of its calls to Chinese servers even when calling participants are in the US. It doesn't make sense geographically to route a call to China if both of the calling participants are in the USA as it is adding unnecesary latency and overhead.

If you haven't figured it out by now, you shouldn't use Zoom. Start exploring Free and Open source video conferencing services like [Tox (qtox)](https://tox.chat), [Jitsi](https://jitsi.org/) and [Ekiga](http://www.ekiga.org/).
