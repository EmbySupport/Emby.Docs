---
uid: TV-Naming
title: TV Naming
legacyUrl: /support/solutions/articles/44001159110-tv-naming
---

For a simple TV folder structure, the recommended folder layout is Series (year)\Season #\Episode. The Episode name itself should contain the show name,  the season and the episode episode number which is covered below.

When setting up the library, make sure to select **TV** as the content type.  It is mandatory for each TV show to have its own folder under the library folder path(s).

Having the year in the series name is not strictly mandatory as Emby can usually match a series without it but it helps tremendously with rebooted series and those that have broadcast in different years such as Battlestar Galactica (1978) and Battlestar Galactica (2003).  The year is also very helpful for some series such as Africa (2013) which could potentially match to a few different shows without the year.

For example:

```
 \TV
    \Glee (2009)
       \Season 1
          Glee S01E01.mp4
          Glee S01E02.mp4

 \TV
    \Seinfeld (1989)
       Seinfeld S01E01.mp4
       Seinfeld S01E02.mp4

```


## ID Tags in Folder & File Names
Emby can also read a Meta-Data ID from the name.

Supported Formats:
* Name (Year) [tvdbid=xxxx]
* Name (Year) [tvdbid-xxxx]
* Name (Year) [tvdb=xxxx]
* Name (Year) [tvdb-xxxx]
* Name (Year) {tvdbid=xxxx}
* Name (Year) {tvdbid-xxxx}
* Name (Year) {tvdb=xxxx}
* Name (Year) {tvdb-xxxx}

Supported ID's:
* tvdb
* tmdb (Moviedb)
* imdb

Example:
```
The Vampire Diaries (2009) [tvdbid=95491]
```

Emby supports the following tags with the host website for lookup.

- tmdbid  (https://www.themoviedb.org/)

- imdbid  (https://www.imdb.com/)

- tvdbid  (https://thetvdb.com/)



## Complex Folder Structure

In more complex situations where your top-level directory is further sub-divided before the show folders, the recommended option is to create a TV media folder and add the sub-folder locations instead of the top level folder. 

For example:

```
 \TV
     \A-M
       \Glee (2009)
          \Season 1
             Glee S01E01.mp4
     \N-Z
       \Seinfeld (1989)
          \Season 1
             Seinfeld S01E01.mp4

```

In the above example, the recommended setup is to create a TV media folder, and then add the **A-M** and **N-Z** library paths. 

For more information on setting up the library, see [Library Setup](Library-Setup.md).

### DVD and Blu-ray episodes

Dvd and Blu-ray folder structures are also supported. The folders can have any name, but using episode numbers will improve the ability to download and display metadata. 

To be recognized as a dvd structure, the folder must contain either a VIDEO_TS subfolder, or a VIDEO_TS.ifo file. To be recognized as a blu-ray structure, the folder must contain a BDMV subfolder.

```
 \TV
    \Glee (2009)
       \Season 1
          \Glee S01E01-E04
              \VIDEO_TS
          \Glee S01E05-E08
              VIDEO_TS.IFO
          \Glee S01E09-E10
              \BDMV

```

## TV extras

Special features for TV series can be stored as video files in an extras folder under TV Series folders. It is also possible to add these extras folders at the season or episode level.

In addition to extras, several other sub-folder names are supported:
* extras
* specials
* shorts
* scenes
* featurettes
* behind the scenes
* deleted scenes
* interviews
* trailers

The following examples show extras at the TV series level.

```
\TV
   \Fawlty Towers
      \Season 1
         Fawlty Towers s01e01.mp4
         Fawlty Towers s01e02.mp4
      \interviews
         Interview with Andrew Sachs.mp4
         Interview with John Cleese.mp4
         Interview with Prunella Scales.mp4
   \The Blue Planet
      \Season 1
         The Blue Planet s01e01.mkv
         The Blue Planet s01e02.mkv
         The Blue Planet s01e03.mkv
         The Blue Planet s01e04.mkv
      \Specials
         The Blue Planet s00e01 Making Waves.mkv
         The Blue Planet s00e02 Deep Trouble.mkv
         The Blue Planet s00e03 The Abyss.mkv
         The Blue Planet s00e04 Dive to Shark Volcano.mkv
         The Blue Planet s00e05 Amazon Abyss.mkv
   \The Bridge (2011)
      \Season 1
         The Bridge S01E01.mkv
         The Bridge S01E02.mkv
      \behind the scenes
         Behind The Bridge.mkv
      \interviews
         An Audience with Sofia Helin.mkv
```

The following examples demonstrate season and episode level extras:

```
\TV
   \Seinfeld
      \Specials
         Seinfeld S00E02 How It Began (Documentary).mkv
      \Season 2
         \Specials
            Master of His Domain (Season 2 unused standup scenes).mkv
         Seinfeld S02E01 The Ex-Girlfriend.mkv
         Seinfeld S02E02 The Pony Remark.mkv
         Seinfeld S02E02 The Pony Remark-behindthescenes.mkv
         Seinfeld S02E02 The Pony Remark-deleted.mkv
         Seinfeld S02E03 The Busboy.mkv
         Seinfeld S02E04 The Baby Shower.mkv
         \S02E05
            Seinfeld S02E05 The Jacket.mkv
            \behind the scenes
               Inside Look - The Jacket.mkv
            \deleted scenes
               The Jacket - deleted scene.mkv
```

> [!NOTE]
> It is not recommended to have folders for individual episodes unless you also have subfolders for extras related to those episodes.

It is also possible to add the type of extra as filename suffix extensions, as for the following:

* -behindthescenes
* -deleted
* -featurette
* -interview
* -other
* -scene
* -short
* -trailer

Examples:
The examples below are not real extras but just given as examples of the syntax used.

```
\TV
   \Anne with an E (2017)
      \Season 1
         Anne With An E S01E01 You Will Shall Decide Your Destiny.mp4
         Anne With An E S01E01 You Will Shall Decide Your Destiny-short.mp4
         Anne With An E S01E02 I Am No Bird, And No Net Ensnares Me.mp4
         Anne With An E S01E02 I Am No Bird, And No Net Ensnares Me-scene.mp4
         Anne With An E S01E03 But What Is So Headstrong As Youth.mp4
         Anne With An E S01E03 But What Is So Headstrong As Youth-featurette.mp4
         Anne With An E S01E04 An Inward Treasure Born.mp4
         Anne With An E S01E04 An Inward Treasure Born-behindthescenes.mp4
         Anne With An E S01E05 Tightly Knotted To A Similar String.mp4
         Anne With An E S01E05 Tightly Knotted To A Similar String-deleted.mp4
         Anne With An E S01E06 Remorse Is The Poison Of Life.mp4
         Anne With An E S01E06 Remorse Is The Poison Of Life-interview.mp4
         Anne With An E S01E07 Wherever You Are Is My Home.mp4
         Anne With An E S01E07 Wherever You Are Is My Home-trailer.mp4
```

> [!NOTE]
> Emby will not look for external metadata provider (e.g. TVDB) matches for episode-level extras; to potentially match, the extras need to be at the series or season level.

> [!NOTE]
> All the different types of extras shown above will appear together in the "Extras" row in the item detail view.


## Mixed Content Libraries

TV series are supported in mixed content libraries using the Unset content type, but season sub-folders are required in this scenario.

## Episode naming conventions

A number of naming conventions are supported:

* show name - S01E01 - Episode Name.ext
* show name S01E01 Episode Name.ext
* anything_s01e02.ext
* anything_s1e2.ext
* anything_s01.e02.ext
* anything_s01_e02.ext
* anything_1x02.ext
* anything_102.ext
* anything_1x02.ext
* 02 Episode Name.ext
* s01e02.ext
* 1x02.ext

### By date

Common for long-running daily shows, you can also use the date the episode aired.

* anything_1996.11.14.ext
* anything_1996-11-14.ext
* anything_14.11.1996.ext

## Multi-Version Episodes

Multi-Version Episodes are best using the following format:

* show name - S01E01 - Display Name 1.ext
* show name - S01E01 - Display Name 2.ext

For example:
Star Trek, The Next Generation - S01E01 - Original Broadcast.mkv
Star Trek, The Next Generation - S01E01 - Digital Remix.mkv

anything following the "-" (dash) up to the file extension will be used in the drop down version selector in your Emby client. In this case the two versions show in the interface will be "Original Broadcast" & "Digital Remix".

> [!NOTE]
> There is a limit on the number of different versions for a media item. Up to 8 different versions will appear in a list of an episode versions.

## Multi-Episode files

All multi-episode files must be part of the same season.

The following conventions are supported:

* 01x02x03 episode name.ext
* S01x02x03 episode name.ext
* S01E02E03 episode name.ext
* S01xE02xE03 episode name.ext
* S01E02-E03 episode name.ext
* S01E02-X03 episode name.ext
* 01x02 01x03 episode name.ext
* 01x02 - 01x03 episode name.ext
* 01x02 - 01x05 episode name.ext (includes episodes 2,3,4 and 5)
* 01x02 - x03 episode name.ext
* 01x02 - x05 episode name.ext
* S01x02.S01x03 episode name.ext
* S01x02 - S01x03 episode name.ext
* show name 01x02x03 episode name.ext
* show name S01x02x03 episode name.ext
* show name S01E02E03 episode name.ext
* show name S01xE02xE03 episode name.ext
* show name S01E02-E03 episode name.ext
* show name S01E02-X03 episode name.ext
* show name 01x02 01x03 episode name.ext
* show name 01x02 - 01x03 episode name.ext
* show name 01x02 - x03 episode name.ext
* show name S01x02.S01x03 episode name.ext
* show name S01x02 - S01x03 episode name.ext

## Specials

Specials should be named using one of the following season folder names:

* Season 0
* Season 00
* Specials

For example:

```
 \TV
    \Glee (2009)
       \Season 0
          Glee S00E01.mp4

```

> [!TIP]
> Please see [Ordering TV Show Special/Extras](Ordering-TV-Specials.md) to learn how to place these specials in the proper timeline.

## Series & Season Images

Images are supported in both series and season folders. Below is a table of the supported image file names. Supported image extensions are **jpg**, **jpeg**, **png** and **tbn**.

Several image types support multiple file names. They are listed in the order that they're checked for.

| Image Type | Supported file names                                 |
|------------|------------------------------------------------------|
| Primary    | folder.ext                                           |
|            | poster.ext                                           |
|            | cover.ext                                            |
|            | default.ext                                          |
|            | show.ext (in series folder only)                     |
|            | seasonXX-poster.ext (in series folder only)          |
|            | season-specials-poster.ext (in series folder only)   |
| Art        | clearart.ext                                         |
| Backdrop   | backdrop.ext, backdropX.ext                          |
|            | fanart.ext, fanart-X.ext                             |
|            | background.ext, background-X.ext                     |
|            | art.ext, art-X.ext                                   |
|            | extrafanart (subfolder)/fanartX.ext                  |
|            | seasonXX-fanart.ext  (in series folder only)         |
|            | season-specials-fanart.ext (in series folder only)   |
| Banner     | banner.ext                                           |
|            | seasonXX-banner.ext (in series folder only)          |
|            | season-specials-banner.ext (in series folder only)   |
| Disc       | disc.ext                                             |
|            | cdart.ext                                            |
| Logo       | clearlogo.ext                                        |
|            | logo.ext                                             |
| Thumb      | thumb.ext                                            |
|            | landscape.ext                                        |
|            | seasonXX-landscape.ext (in series folder only)       |
|            | season-specials-landscape.ext (in series folder only)|

For backdrops, X represents a number, and you can have any amount of numbered backdrops. For example:

```
 \TV
    \Glee (2009)
       backdrop.ext
       backdrop1.ext
       backdrop2.ext
       backdrop3.ext

```


## Season images without season folder

If season folders are not used, season images can still be supplied directly in the series folder, using a naming convention to indicate the season.

| Image Type | Supported file names                                 |
|------------|------------------------------------------------------|
| Primary    | seasonXX-poster.ext                                  |
|            | season-specials-poster.ext                           |
| Backdrop   | seasonXX-fanart.ext                                  |
|            | season-specials-fanart.ext                           |
| Banner     | seasonXX-banner.ext                                  |
|            | season-specials-banner.ext                           |
| Thumb      | seasonXX-landscape.ext                               |
|            | season-specials-landscape.ext                        |

For example:

```
 \TV
    \Glee (2009)
       season01-poster.jpg
       season-specials-poster.jpg
       season01-fanart.jpg
       season-specials-fanart.jpg
       season01-banner.jpg
       season-specials-banner.jpg
       season01-landscape.jpg
       season-specials-landscape.jpg

```

## Episode Images

The following naming conventions are supported for episode images:

* {name}-thumb.ext (in same folder)
* {name}.ext (in metadata sub-folder)

Supported image extensions are **jpg**, **jpeg**, **png** and **tbn**.

For example:

```
 \TV
    \Glee (2009)
       \Season 1
          Glee S01E01.mp4
          Glee S01E01-thumb.jpg
       \Season 2
          Glee S02E01.mp4

```

## 3D episodes

3D episodes files are supported. See [3D videos](3D-Videos.md).

## Media stubs

Media stubs are supported as episodes. See [media stubs](Media-Stubs.md).

## Strm files

Strm files are supported as episodes. See [strm files](Strm-Files.md).

## Subtitles

Subtitles for episode files are supported. See [subtitles](Subtitles.md).
