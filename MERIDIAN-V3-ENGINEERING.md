# Meridian V3: Native MS200 / Sooloos playback breakthrough

**Brimstone Core R1 · Engineering update · 8 November 2026**

> **Native Meridian V3 playback is working on real hardware.** After a difficult period of stuttering, premature stops and dropped playback, the V3 engine is now the forward development path for Brimstone Core.

![Brimstone Core R1 now playing, with music queue and output selection](https://core-audio.uk/assets/showcase/core-now-playing.jpg)

**Read the full announcement:** [Meridian V3 — A Playback Breakthrough](https://core-audio.uk/meridian-v3-breakthrough-20261108.html)  
**Project:** [Brimstone Core](https://core-audio.uk/) · [Meridian integration](https://core-audio.uk/meridian.html) · [Downloads](https://core-audio.uk/downloads.html)

## What changed?

Until very recently, the experimental Meridian V3 engine could stutter, stop prematurely, drop playback and fail unpredictably when advancing between tracks. Working through repeated forward/backward skipping made the next-track failure reproducible enough to investigate.

The developer isolated and corrected a small **floating-point-related numerical error** behind the intermittent next-track failure. Combined with the other recent transport fixes, this has transformed native playback reliability in testing.

That is a real engineering milestone: a numerically small error can become a very audible failure when it affects an audio transport's timing or track boundaries.

**Important technical distinction:** the exact corrected expression has not been published here. We are **not claiming an FFmpeg defect**, nor do we have evidence that Roon or any other player's engine contains the same bug.

## Meridian V3 status

| Area | Reported result / engineering status |
| --- | --- |
| Native Meridian V3 playback | **Working** in the live development environment |
| Original Meridian MS200 | **Real-hardware playback demonstrated** |
| Earlier stuttering and stops | **Major playback problems resolved** in recent tests |
| Random failure on next-track transition | **Numerical fault identified and corrected** |
| Repeated previous/next track operations | Used to reproduce and diagnose the fault; further regression tests remain useful |
| Meridian V2 | **Being retired** from the active implementation in favour of V3 |
| Cold boot, IP changes and receiver reboot recovery | Targeted for explicit hardware acceptance testing |
| Long-duration / mixed-sample-rate qualification | Continuing before wider release approval |
| Other Meridian models, including MS600 and ID40/ID41 | Model-by-model qualification; do not infer identical results from MS200 testing |

## What makes old Meridian hardware interesting?

Original Sooloos and Meridian endpoints have their own discovery, control-session and packet-delivery characteristics. A modern music player cannot assume that two control connections, a restarted receiver, a different IP address or a fresh track boundary are interchangeable events.

Our Meridian engineering programme emphasises:

- **Persistent hardware identity** rather than treating an IP address as the device identity.
- **Non-intrusive discovery** so routine presence checks do not seize or interrupt an active MS200 streaming-control session.
- **A single playback owner** per physical receiver.
- **Bounded buffering and retransmission behaviour** rather than unbounded recovery work.
- **Reliable track boundaries** and clear error reporting.
- **Automatic recovery** after Core, network or receiver restarts, without making the listener run discovery manually.

These are design and qualification requirements, not claims that every recovery case has passed on every physical device.

## The bigger picture: Meridian, Roon and a new music platform

Brimstone Core is also being tested with **music from Roon-managed libraries**, alongside Meridian V3, Sonos and other network audio transports. See [our Roon library interoperability note](ROON-LIBRARY-COMPATIBILITY.md).

This matters to owners of classic equipment: the goal is to keep useful DACs, streamers, processors and speakers in service while enjoying a modern, browsable music collection.

Brimstone is an **independent project**, not an official Meridian Audio or Roon Labs product. **No Roon Ready certification or Meridian endorsement is claimed.**

## Help test it

If you own an MS200, MS600, ID40/ID41, Control 15, MD600 or another Meridian/Sooloos device, we're especially interested in reproducible reports covering discovery, gapless transitions, unusual sample rates and receiver restarts.

[Join the Brimstone Discord](https://discord.gg/XyNm7ZXsj) · [See the actual Core interface](https://core-audio.uk/core.html) · [Installation guide](https://core-audio.uk/install.html)

**Six years from the first paper design. Still finding ways to make old hardware sing.**
