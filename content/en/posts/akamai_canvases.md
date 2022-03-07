---
title: "Akamai's canvases"
description: Akamai uses two canvases. What are their purpose?
date: 2022-03-07T21:51:36+01:00
draft: false
---

Did anyone else notice that Akamai generated two canvases? One of them is large, and the other is pretty small.

The big canvas they use looks like this: https://arh.antoinevastel.com/assets/media/sneakers/anon_canvas1_footlocker.png. It is of course used for [canvas fingerprinting](https://en.wikipedia.org/wiki/Canvas_fingerprinting).
The small (16x16) canvas they use looks like this: https://arh.antoinevastel.com/assets/media/sneakers/anon_canvas2_footlocker.png.

My intuition is that the checksum of the small canvas will be the same on every GPU and OS.
They use the first canvas for fingerprinting and the second one to check that the user did not apply noise to their canvases.
(anti-canvas-fingerprinting extension will indiscriminately apply noise to all canvases)

This intuition coincides with a 2014 research paper I recently skimmed through where you can read:

> Enforcing a 16x16 pixel size limit allowed us to filter out scripts that read too few pixels to efficiently extract the canvas fingerprint. Although there are 28192 possible color combinations for a 16x16 pixel image, operating systems or font libraries only apply anti-aliasing (Which is an important source of diversity for canvas fingerprinting) to text larger than a minimum font size.

Source: https://github.com/prescience-data/dark-knowledge/blob/main/library/2014%20-%20The%20Web%20Never%20Forgets%20-%20Persistent%20Tracking%20Mechanisms%20in%20The%20Wild.pdf

E.g. Akamai could catch people adding noise to ALL their canvases this way.

:point_up_2: on the importance of reading research papers AND writing your evasions instead of using black box extensions
