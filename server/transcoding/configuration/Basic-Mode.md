---
uid: Server-Transcoding-Basic-Mode
title: "Basic Mode"
---

Basic Mode is the default, and for most systems it is all that is needed. It consists of a single choice:
which device should perform hardware accelerated transcoding.

## Hardware Acceleration

The dropdown offers:

**Auto** - Emby uses whichever detected device ranks highest, and keeps that choice in step with the
hardware. If a device is added, removed or replaced, the pick follows automatically rather than pointing at
something that is no longer there. This is the default.

**Off** - no hardware acceleration. Everything is transcoded in software.

**A specific device** - each detected device is listed by name. Choosing one pins the configuration to it.

Changes take effect when you save them.

## Software Fallback

Choosing a device does not disable software transcoding. It stays enabled behind the chosen device, as what
takes over when that device turns out not to be able to handle an operation - which is why the graph shows
it at the end with a green arrow leading into it.

"Off" is the same picture with nothing in front: software is the only node in use.

This behaviour is fixed in Basic Mode and cannot be changed. See
[Fallback Paths](Expert-Fallback-Paths.md#fallback-handling-in-basic-and-advanced-modes) for why the graph
looks the way it does, and what the other modes allow instead.

## The Graph

The graph below the dropdown shows what the choice amounts to: the selected device, then software behind
it. It is there to be read rather than edited - the nodes are not selectable and offer no commands of
their own, because in Basic Mode the dropdown is the whole configuration.

## What Basic Mode Does Not Have

Basic Mode keeps no configuration history, and saving therefore does not ask for a name - there would be
nothing for a name to distinguish. Saving simply applies what the dropdown says.

Everything else is configured automatically: which encoders and decoders are used, which hardware context,
and which filters. If you need to influence any of that, see [Advanced Mode](Advanced-Mode.md).
