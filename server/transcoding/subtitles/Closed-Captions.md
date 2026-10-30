---
uid: Server-Transcoding-Subtitle-Closed-Captions
title: "Closed Captions"
---

[Closed captions](xref:Learn-Caption-CTA-608) as used in ATSC broadcasts are not a separate subtitle track
but are [carried inside the video stream](xref:Learn-Subtitle-In-Band). How Emby handles them is set on the
**Closed Captions** tab of the **Subtitle Processing** page in the Transcoding section of the dashboard.

## Settings

- **Disable Incremental Line Display** - captions are often sent letter by letter. With this on, only
  complete lines are shown.
- **Use Traditional Display Style** - shows captions in white on a black box.
- **Disable Client-Side Decoding** - some clients can decode captions from the video themselves, which can
  save a transcode. This turns that off, so that the server handles the captions - which is needed for
  [Content Change](Content-Change.md), including the profanity filter, to apply to them.

## Further Reading

<xref:Learn-Subtitle-SDH>
