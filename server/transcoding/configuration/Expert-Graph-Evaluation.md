---
uid: Server-Transcoding-Expert-Graph
title: "Graph Evaluation"
---

# Graph Evaluation

## Two Passes of Evaluation

> [!WARNING]
> This is crucial knowledge for understanding Expert mode Configurations

- PASS 1: GPU/SW Config Selection
- PASS 2: Fallback Paths Calculation

This practically means that the first pass determines which GPU should be used and with which configuration (or SW
transcoding with a certain configuration).

The 2nd pass though, is about deciding what should happen in case when the configuration chosen by the first pass
would result in an error.

## Evaluation Order

Graph evaluation happens in the same order like when reading a book:

- Row after row from top to bottom
- Within each row from left to right

That order is also indicated by the arrows in the graph.

## Exceptions

- Different rules apply inside a Load Balancing container - see [Load Balancing](Expert-Load-Balancing.md)
- For fallback calculation, only fallback point nodes are considered  
  => These are nodes which have a green or red border and are preceded by a green or red arrow

How the second pass uses this is described in [Fallback Paths](Expert-Fallback-Paths.md).
