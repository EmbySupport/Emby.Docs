---
uid: Server-Transcoding-Expert-Conditions
title: "Node Conditions"
---

Every node in the graph can carry conditions, which decide whether that node applies to the operation being
evaluated. A node whose conditions do not match is passed over, and evaluation carries on as if it were not
there.

Expert Mode shows a filter builder here, in place of the short list of operation kinds that
[Advanced Mode](Advanced-Mode.md#conditions) offers. The filter builder can combine several fields, with
and/or groups, rather than only saying which kinds of operation a node applies to.

Conditions apply to containers as well as to device nodes. A condition on a Condition Group applies to
everything inside it - which is the entire purpose of that container, see
[Node Types](Expert-Node-Types.md#condition-group). Nodes inside the container can carry their own
conditions on top.

## Available Fields

| Field | What it matches |
|---|---|
| Operation | The kind of operation: Conversions, LiveTV, Playback, HlsPlayback |
| Source Codec | The video codec of the source |
| Output Codec | The video codec being produced - AV1, H.264 or HEVC |
| Processing | A processing step the operation involves: Closed Captions, Tone Mapping, Subtitle Burn-In, Subtitle Overlay |
| User | The user the playback or conversion belongs to |
| Library | The library the item comes from |
| Error Count | How many failed attempts precede this node being used - see below |

An operation can involve more than one processing step at once - tone mapping and subtitle burn-in
together, for instance.

## Building a Condition

TBA - working with the filter builder itself: adding criteria and nesting groups.

Two things about what a filter can express are worth knowing while you do.

Criteria compare a field against a value using `=`, `<>`, `>`, `>=`, `<` or `<=`, and text fields
additionally support matching on part of a value. Which of these the builder offers depends on the type of
the field you picked.

Criteria are combined with **and** or **or**, but not both within one group. To express a mixture, nest a
group inside another - the inner group's combination is independent of the outer one's.

## Conditions on Fallback and Failure Points

Conditions on nodes that take part in fallback calculation are evaluated in the second pass just as they
are in the first - see [Fallback Paths](Expert-Fallback-Paths.md#fallback-paths-in-expert-mode).

<!-- REVIEW: ErrorCount is documented here as an available condition field. Confirm the field name and the
     values it takes once it is implemented. -->

What makes the two passes distinguishable from inside a condition is **Error Count**: the number of failed
attempts that precede this node being used.

- During the first pass nothing has failed yet, so it is **0**
- During the second pass it starts at **1** and increases by one for each fallback point already found and
  added to the list - so the first fallback is evaluated with 1, the second with 2, the third with 3

That gives you a way to state when a node applies at all:

| Condition | Effect |
|---|---|
| `Error Count = 0` | Effectively disables the node for fallback use - the equivalent of not marking it as a fallback point |
| `Error Count > 0` | Applies only as a fallback, never during initial selection |
| `Error Count = 1` | Applies only as a fallback when no previous fallback attempt has been made |

The most common use is on a Failure Point. By default a Failure Point applies in both passes, which stops
evaluation outright. Giving it `Error Count > 0` leaves the first attempt alone while stopping any further
ones - "try this, but do not keep trying if it fails" - see
[Failure Point](Expert-Node-Types.md#failure-point).

The same applies to a device entry marked as a fallback point: a condition on Error Count decides whether
that entry is used as a fallback at all, and whether only as the first one.
