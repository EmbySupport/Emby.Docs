---
uid: Server-Transcoding-Expert-Fallback
title: "Fallback Paths"
---

Hardware accelerated transcoding with FFmpeg is by a magnitude less reliable than software transcoding.
One reason for that is test coverage. FFmpeg has an extensive suite for automated testing, but the
majority of tests are limited to sw transcoding cases, and there are just a few for hw accelerated operations.
Additional risk factors for successful hardware transcoding are hardware setup, GPU capabilities,
OS support, system/kernel drivers and user mode drivers and framework middleware (like Vulkan, OpenCL,
DX11, VAAPI, et al).
Emby has its own built-in detection of hardware devices, codecs and capabilities, which is unparalleled
in the industry. It allows us to minimize failing attempts to leverage hardware acceleration, but errors
can still happen for a variety of reasons.

## Default Fallback: Software Transcoding

The built-in way in Emby for dealing with hardware transcoding errors has always been (and still is in
case of Basic Mode and Advanced Mode) to fall back to software transcoding in those cases.
As a matter of fact, software transcoding is a kind of safe-haven which is almost always working (unless
there are issues with the source media, in terms of connectivity, invalid container data or corrupted
media streams).

## Alternate Fallback Paths

We understand that the simple - yet effective - hard-coded software fallback is not always desirable.
There are edge cases where users may wish to deviate from that mechanism - for example when the CPU
is so extremely weak that software transcoding is not reasonable to even try it. Or cases where simple
transcoding may work, but more complex operations (like subtitle burn-in or tone mapping) are known to
never work out at a reasonable processing speed.
There may also be cases where you may want to configure a secondary GPU to try as a fallback first, and
only try software transcoding as a 3rd attempt (or no sw attempt at all). Another case might be to try
the same GPU with different configurations, for example using an experimental hardware context like Vulkan
first and try a more mature configuration as a 2nd attempt. Or maybe there's a filter configuration that
you prefer but which does not work in all cases.

## Fallback Paths in Expert Mode

Expert Mode allows to deal with all those cases in an elegant and declarative way. It's quite simple once
understood, but without reading this documentation, it is likely to remain an uncovered mystery.

Before proceeding, let's recap: There are two passes in graph Evaluation. If you haven't read it yet,
please do now: [Two Passes of Evaluation](Expert-Graph-Evaluation.md#two-passes-of-evaluation)

So, as you should have learned, the first pass of graph evaluation determines the GPU/SW configuration
that will be used. Once that has been done, the second pass evaluation starts - and the starting point
for that is the resulting node from the first pass (exclusive).

For the 2nd pass evaluation only certain nodes are considered - all other nodes are ignored, with the
following specifics:

- GPU and SW Config nodes are considered when they are marked as a "Fallback Point"  
  To mark any such node as a Fallback Point, open its properties dialog, scroll down to the bottom and
  enable the "Is Fallback Point" switch
- Failure Point nodes are always considered
- If the selected node is inside a container (Condition Group or Load Balancing Group), evaluation will
  continue inside this container
  but:
- Subsequent containers will NOT be entered during the 2nd pass, irrespective of conditions
- The bottom end of the graph is treated like a (invisible) Failure Point
- For all "considered" nodes, their conditions and applicability are evaluated just like normal
- Additional control regarding fallback/failure point behavior is possible by configuring a condition
  on ErrorCount

Also worth mentioning is that the fallback paths are always calculated up-front, with the ErrorCount
property starting with value 1 and being increased by 1, each time when a matching fallback point is found
and added to the list.

## Max Total Fallbacks

There's a hard maximum of 3 fallbacks. After having encountered and added 3 fallback paths, the 2nd pass
evaluation stops and subsequent fallbacks are ignored.

## Visual Indication of Fallback and Failure Points

There are two clear visual distinctions for easy recognition of nodes relevant for fallback path calculation
from other nodes:

- A thin colored border  
  Independent from focus/selection borders, these nodes have a thin colored border which is always visible:
  - Red for Failure Points
  - Green for nodes marked as Fallback Point
- Colored Arrow  
  The nodes are preceded by a colored arrow in the graph:
  - Red for Failure Points
  - Green for nodes marked as Fallback Point

## Fallback Handling in Basic and Advanced Modes

When looking at the graphs in Basic and Advanced Mode, we can see that the software transcoding node is always
at the bottom (end of the graph) and other nodes cannot be moved further below. It is always marked as fallback
point (which cannot be changed) and no other node can be set as a fallback point. The software transcoding is
always shown with the green border and green arrow (unless there's no other enabled node), marking it as Fallback
point.
With the knowledge from this chapter, it is easy to understand now, that this reflects the usual Emby software
fallback behavior, which is always in place and always the same for Basic and Advanced configurations.
Only Expert Mode allows for custom fallback configurations in the ways described above.
