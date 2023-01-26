The recommended folder structure for audio books is Author\Book Name\Chapter

```
 \AudioBooks
    \Author
       \Book Name
          1- Chapter 1.mp3
          2- Chapter 2.mp3
```

This is not a requirement and other structures will also work, but this is the most common method. Some other examples of supported structures are Book Name\Chapter:

```
 \AudioBooks
    \Book Name
       1- Chapter 1.mp3
       2- Chapter 2.mp3
```

Or even a flat library of chapter files:

```
 \AudioBooks
     1- Book Name - Chapter 1.mp3
     2- Book Name - Chapter 2.mp3
```

Track/Chapter numbers are retrieved using embedded ID3 tag information if present.

## Multi-Disc Audio Books

You can store you media in the following format for convenience but Emby will not pick up the "disk #".  In order to use this folder structure you will need to use an external tag editor such as MP3Tag.  Using MP3Tag you would highlight all files in each folder and assign a single tag for the disc # and save.  Emby will then read the tag and show as well as sort your audio chapters by disc.

```
 \AudioBooks
    \Author
       \Book Name
         \Disc 1
            1- Chapter 1.mp3
            2- Chapter 2.mp3
         \Disc 2
            1- Chapter 1.mp3
            2- Chapter 2.mp3
```

## Audio Book Images

Images are supported in both artist and album folders, as well as images embedded within audio files. Below is a table of the supported image file names:

Supported image extensions are **jpg**, **jpeg**, **png** and **tbn**.

Several image types support multiple file names. They are listed in the order that they're checked for.

| Image Type | Supported file names  |
| ------------- |---------------|
| Primary      | folder.ext |
|              | poster.ext |
|              | cover.ext |
|              | default.ext |
| Art      | clearart.ext      |
| Backdrop  | backdrop.ext, backdropX.ext |
|           | fanart.ext, fanart-X.ext |
|           | background.ext, background-X.ext      |
|           | art.ext, art-X.ext      |
|           | extrafanart (subfolder)/fanartX.ext      |
| Banner   | banner.ext      |
| Disc      | disc.ext      |
|           | cdart.ext      |
| Logo     | logo.ext      |
| Thumb     | thumb.ext      |
|           | landscape.ext      |

For backdrops, X represents a number, and you can have any amount of numbered backdrops. For example:

```
 \AudioBook
    \Author
       backdrop.ext
       backdrop1.ext
       backdrop2.ext
       backdrop3.ext

```
