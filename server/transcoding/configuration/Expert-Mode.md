---
uid: Server-Transcoding-Expert-Mode
title: "Expert Mode"
---

Expert Mode turns the configuration into a freely composed decision graph. Where Advanced Mode gives you an
ordered list of devices with simple conditions, Expert Mode lets you build the whole decision: containers,
load balancing, deliberate failure points, the same device appearing more than once under different
configurations, and fallback behaviour of your own choosing.

That last point is the one to understand before starting. In Basic and Advanced Mode, falling back to
software transcoding when hardware fails is built in and cannot be changed. In Expert Mode it becomes your
responsibility - see [Fallback Paths](Expert-Fallback-Paths.md).

The graph and how it is read are covered in [Graph Evaluation](Expert-Graph-Evaluation.md), the things you
can put in it in [Node Types](Expert-Node-Types.md), what makes a node apply in
[Node Conditions](Expert-Conditions.md), and spreading work across devices in
[Load Balancing](Expert-Load-Balancing.md).

## Differences from Advanced to Expert Mode

- Multiple nodes for the same GPU and multiple software nodes can be inserted
- Additional node types can be inserted
  - Condition Group
  - Load Balancing Group
  - Failure Point
- Node Conditions  
  A different conditions dialog is shown with a filter-builder that allows to create complex conditions
  based on a variety of input values.
  Advanced mode provides a simple dialog with operation conditions only
- Filter Parameters  
  In Advanced, only tone mapping can be configured in the Filtering section. Expert mode allows configuring
  details for additional types of filters like deinterlacing, scaling and overlay
- Disabled nodes remain in the graph  
  In Advanced mode, disabling a GPU configuration moves it out of the graph to the bottom.
  In Expert mode, disabled nodes keep their position
- GPU Configurations for unavailable devices are retained  
  In Advanced mode, previously saved configurations for devices which have become unavailable are still shown,
  but when the configuration is saved again, those devices are automatically removed.
  Expert mode tolerates and retains those configurations even when saving and it is the user's responsibility
  to remove them when they are no longer needed.
- Fallback behavior becomes a responsibility of the user
