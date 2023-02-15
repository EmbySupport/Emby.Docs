---
uid: Subtitles
title: Subtitles
legacyUrl: /support/solutions/articles/44001159160-subtitles
---

External subtitles should use the same file name as the movie/show except for the extension(s) as shown below.

```
/Movies
   /Home Alone (1990)
      Home Alone.mkv
      Home Alone.srt
      Home Alone.spa.srt
      Home Alone.spanish.srt
```

> [!NOTE]
> If you need spaces in the subtitle to show up hold down the ALT key and punch in the ASCII code of 255 for a "space" character in the file name itself.

## Default Subtitles

External subtitles can be marked as default using either ".default".
```
/Movies
   /Home Alone (1990)
      Home Alone.mkv
      Home Alone.srt
      Home Alone.spa.default.srt
```

## Forced Subtitles

External subtitles can be marked as forced using either ".forced" or ".foreign".
```
/Movies
   /Home Alone (1990)
      Home Alone.mkv
      Home Alone.srt
      Home Alone.spa.forced.srt
      Home Alone.spa.foreign.srt
```

## Other Names
It is sometimes useful to have other "names" in the subtitle to help identify it from the client.  This can be useful for directory or comment

```
/Movies
   /Home Alone (1990)
      Home Alone.mkv
      Home Alone.English(Commentary).srt
      Home Alone.Spanish(Commentary).srt
```

## Supported formats

* ass
* srt
* ssa
* sub/idx
* vtt

## Plugins that automate subtitle downloading

* [Open Subtitles](Open-Subtitles.md).
* Podnapisi
* SubDb

##### See also
- [Open Subtitles](Open-Subtitles.md)
- [Plugins](Plugins.md) for more information on use
- [Automatic Subtitle Downloads](Automatic-Subtitle-Downloads.md)
- [Manual Subtitle Downloads](Manual-Subtitle-Downloads.md)

## ISO and Country codes used together

Sometimes you may need to use a country code in addition to the ISO code.  This might be the case when a country name is associated with different dialects.  For example written "Chinese" could be Simplified or Traditional Chinese.

Using both the ISO and Country code allows you to specify this. zh is the ISO code for Chinese. To distinguish simplified vs traditional in the naming of your subtitle files you would follow the following format:

|       |                                     |
|-------|-------------------------------------|
| zh-CN | ext for mainland China (simplified) |
| zh-SG | ext for Singapore (simplified)      |
| zh-TW | ext for Taiwan (traditional)        |
| zh-HK | ext for Hong Kong (traditional)     |

##### Reference
- [ISO Codes for the Representation of Names of Languages](https://www.loc.gov/standards/iso639-2/php/code_list.php)