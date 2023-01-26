All video files can have external subtitles. The file name must match the video file name, or be suffixed with a language.

```
/Movies
   /Home Alone (1990)
      Home Alone.mkv
      Home Alone.srt
      Home Alone.spa.srt
      Home Alone.spanish.srt
```

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

## Supported formats

* ass
* srt
* ssa
* sub/idx
* vtt

## Plugins that automate subtitle downloading
* [Open Subtitles](Open-Subtitles).
* Podnapisi
* SubDb

See [Plugins](Plugins) for more information on use.