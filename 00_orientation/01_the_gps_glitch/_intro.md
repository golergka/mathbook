# Chapter 0.1 – The GPS Glitch

Welcome to the opening chapter of our Orientation. If you've ever watched your phone insist that you're parked in the ocean when you're clearly at home, you already know what it means to have tech betray you. We'll explore how a tiny bit of noise in a GPS signal can send your navigation app spiraling into confusion. It's the perfect reminder that math isn't just abstract theory—it bites you in real life when things go wrong.

Throughout this chapter we'll use a short sequence of GPS logs sampled once per second (10 data points total) as our working dataset. We'll treat **x(t)** as the true position of a walker and **z(t)** as what the gadget actually reports. Because these logs are stored in `/datasets/`, you can pull them up later if you want to follow along or test your own ideas.

Our two upcoming sections set the tone for the rest of the book. First we see why naïvely computing derivatives from this noisy data leads to weird, jittery results. Then we hint at how clever filtering can tame the chaos. Along the way we'll point out how these ideas crop up in unexpected corners of mathematics.

Let's dive in and figure out why that GPS trace looks so jumpy—and how math can help us smooth out the mess.
