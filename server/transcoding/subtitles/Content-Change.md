---
uid: Server-Transcoding-Subtitle-Content-Change
title: "Content Change"
longTitle: "Subtitle Content Change"
---

Emby can modify the content of subtitles in several ways. The settings are on the **Content Change** tab of
the **Subtitle Processing** page in the Transcoding section of the dashboard.

The changes apply to [text subtitles](xref:Learn-Subtitle-Text), including
[closed captions](Closed-Captions.md), and to graphical subtitles once
[OCR Conversion](OCR-Conversion.md) has turned them into text.

## Speaker Names

[ASS/SSA](xref:Learn-Subtitle-ASS) subtitles often name the character speaking each line.
**Enable Speaker Name Display** prefixes the lines with those names where they are available, and
**Speaker Prefix Type** chooses the form:

- `[speaker] text` (default)
- `(speaker) text`
- `speaker: text`
- `speaker text`

## Text Modification

Two modifications can be applied, one after the other, each switched on separately. **Modification Mode**
chooses what each one does:

- change to upper case (default) or to lower case
- replace or remove characters
- replace or remove words

Words are separated by semicolons. When replacing, give as many replacement characters or words as there are
characters or words to replace.

## Profanity Filter

**Enable Profanity Filter** obfuscates words that appear in subtitles.

- **Censor Mode** - censor all characters but the first and last (default), all but the first, or all
- **Replacement Character** - the character used instead, `*` by default
- **Word List** - the built-in English word list (default), a list loaded from a text file with the words
  separated by semicolons, or words entered directly for testing, up to 1000 characters

To cover all subtitles, the profanity filter should be used together with
[OCR Conversion](OCR-Conversion.md), which makes graphical subtitles accessible to it, and with client-side
decoding of [closed captions](Closed-Captions.md) disabled. The tab warns when either is not the case.
