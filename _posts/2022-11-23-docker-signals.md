---
layout: post
title: "The ellusive SIGTERM in Docker"
date: 2020-07-14 18:37:37 +0100
---

To catch SIGTERM in Docker, do:

- Don't run tail in foreground! Run tail in background and call `wait` on it.
- Apparently, `wait` works but tail does not.
