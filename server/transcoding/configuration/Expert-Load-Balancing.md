---
uid: Server-Transcoding-Expert-LoadBalancing
title: "Load Balancing"
---

A Load Balancing Group distributes transcoding work across the nodes it contains, rather than trying them
in order until one applies. It is inserted like any other container - see
[Node Types](Expert-Node-Types.md).

The container itself decides how work is assigned to the nodes below it. The nodes decide how much work
they will accept.

## Distribution

**Overflow** uses the nodes in order, each until its own limit is reached, then the next one. The graph
draws these as an ordered, left-to-right row, because the order is what determines which node is used
first.

**Balance** uses whichever node is currently least loaded. The graph draws these as an unordered row,
since position carries no meaning here.

> [!IMPORTANT]
> Overflow only does something if the nodes have limits. Without a limit a node never becomes full, so
> nothing ever overflows to the next one - see [Limits](#limits).

## Comparing Load

These two only apply to **Balance**, since Overflow never compares one node against another.

**Compare load by** decides what makes one node busier than another:

- **Absolute** compares the raw number of operations
- **Relative** compares each node's share of its own limit, so a node with a smaller limit is not simply
  favoured for having a smaller number of operations on it

**Count load per** decides what a node's load is counted over:

- **Local** counts the operations running through that node
- **Global** counts the operations running through the device behind it, across the whole graph

The difference between the two only matters when the same device appears more than once in the graph -
which Expert Mode allows, and which is one of the reasons this setting exists.

## Limits

Each node inside a load-balancing container has its own **Limits**, reachable from the node's own command
menu. Two limits are edited together there, because neither reads sensibly on its own:

**This node** - how many operations may run through this particular node at once. Leave it empty for no
limit. Once the limit is reached, the container passes work to another node instead, which is what makes
Overflow possible at all.

**This device, everywhere in the graph** - how many operations the device behind the node may run at once
in total, counted across every node in the graph that refers to it. Leave it empty for no limit.

Only operations routed through a load-balancing container are counted, since nothing elsewhere in the graph
would cause a device to be passed over for being busy.

## Evaluation Inside a Load Balancing Group

The ordinary top-to-bottom, left-to-right reading order does not apply inside these containers - which
node is used is a matter of load rather than of position. This is one of the exceptions noted in
[Graph Evaluation](Expert-Graph-Evaluation.md#exceptions).
