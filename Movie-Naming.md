This file naming guide applies to movies, home videos and music videos. For tv episode naming, see [TV naming](TV-naming).

### Library Setup

When setting up the library, make sure to select **Movies**, **Home videos**, or **Music videos** as the content type.

Emby supports several different formats and naming conventions such as ISO copies of discs to DVD/Blu-Ray file formatted layouts which are both different types of disc copies. These formats work but are not an ideal way to build your library. Since neither of these are streaming formats they require more work by the server to transcode and stream to client apps. These formats and naming conventions are covered below.

A much better way of building a large Emby library of content is to prepare you media ahead of time using a streaming friendly format such as MP4 or MKV containers featuring H.264 (or H.265) video with at least one 2 Channel AAC default audio track along side any other audio tracks such as Dolby Digital or DTS. Media prepared in this fashion will have the greatest compatibility with all Emby clients. The idea behind preparing your media ahead of time in this fashion is to reduce the need for the Server to have to transcode (convert) media on the fly. This is not a requirement but is strongly encouraged.

## Naming your media

Once you've prepared your media files, it's time to name your media in a way that allows Emby the best chance of determining what it is.  The best way to do this is to use the format: "MovieName (year).extension" such as "Top Gun (1986).mp4" or "Avatar (2009).mkv".  Because Emby allows many other advanced functions that can be used with your media we want to create a folder structure that aids in this use.  The simplest method of doing this is to put all media related to a Movie in the same folder using a name "MovieName (year). It will look like this:

```
\Movies\Avatar (2009)\Avatar (2009).mkv
\Movies\Pulp Fiction (1994)\Pulp Fiction (1994).mp4
\Movies\Reservoir Dogs (1992)\Reservoir Dogs (1992).mp4
\Movies\The Usual Suspects (1995)\The Usual Suspects (1995).mkv
\Movies\Top Gun (1986)\Top Gun (1986).mp4
```
## Complex Folder Structure
If you plan on having thousands of movies in your library you may want to add an additional folder to your hierarchy to aid in navigation.  For example you could create folders for all movies starting with the first letter or number such as:

```
\Movies\A\Avatar (2009)\Avatar (2009).mkv
\Movies\P\Pulp Fiction (1994)\Pulp Fiction (1994).mp4
\Movies\R\Reservoir Dogs (1992)\Reservoir Dogs (1992).mp4
\Movies\T\The Usual Suspects (1995)\The Usual Suspects (1995).mkv
\Movies\T\Top Gun (1986)\Top Gun (1986).mp4
```
When viewing your media outside of Emby using conventional tools such as Windows Explorer this allows you to navigate your library much quicker without having to wait for thousands of folders to load.  It saves you from scrolling through thousands of folders to get to your "W" movies for example. Emby will work just fine with or without this additional folder!

## Multi-version movies
 
Multiple versions of the same content can be stored in a single movie folder.

```
/Movies
  /300 (2006)
    /300 (2006) - 1080p.mkv
    /300 (2006) - 4K.mkv
    /300 (2006) - 720p.mp4
    /300 (2006) - extended edition.mp4
    /300 (2006) - directors cut.mp4
    /300 (2006) - 3D.hsbs.mp4
```

Each version must begin with the folder name, followed by " - ". 

If using the dash method anything following the dash will be what you see in the Emby client app.

**Note**: The above example includes a 3D version, which is discussed in the [3D Video](3D-Videos) naming guide.

## Movie extras

Special features for movies can be stored as video files in an extras folder under movie folders. Nested folders are not supported. 

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
 
```
/Movies
   /Home Alone (1990)
      Home Alone (1990).mkv
      /extras
         deleted-scenes.mkv 
      /behind the scenes
         video1.mkv 
      /interviews
         video1.mkv 
```

**Note**: Be sure the movie file is present before adding these additional "extras" to avoid mis-identification.

## Video images

Images are supported in video folders. Below is a table of the supported image file names. Supported image extensions are **jpg**, **jpeg**, **png**, **gif** and **tbn**.

Several image types support multiple file names. They are listed in the order that they're checked for.

| Image Type | Supported file names  |
| ------------- |---------------|
| Primary      | {name}.ext |
|              | {name}-poster.ext |
|              | {name}-cover.ext |
|              | {name}-default.ext |
|              | {name}-movie.ext |
|              | folder.ext |
|              | poster.ext |
|              | cover.ext |
|              | default.ext |
|              | movie.ext |
| Art      | {name}-clearart.ext      |
|          | clearart.ext      |
| Backdrop  | backdrop.ext, backdropX.ext |
|           | fanart.ext, fanart-X.ext |
|           | background.ext, background-X.ext      |
|           | art.ext, art-X.ext      |
|           | extrafanart (subfolder)/fanartX.ext      |
| Banner   | {name}-banner.ext      |
|          | banner.ext      |
| Disc     | {name}-disc.ext      |
|          | {name}-cdart.ext      |
|          | disc.ext      |
|          | cdart.ext      |
| Logo     | {name}-logo.ext      |
|          | logo.ext      |
| Thumb     | {name}-thumb.ext      |
|           | {name}-landscape.ext      |
|           | thumb.ext      |
|           | landscape.ext      |

{name} represents the video file name, without extension. For videos that are not contained within their own folder, only the conventions using {name} are supported.

For backdrops, X represents a number, and you can have any amount of numbered backdrops. For example:

```
 \Movies
    \300 (2006)
       backdrop.ext
       backdrop1.ext
       backdrop2.ext
       backdrop3.ext

```

### DVD and Blu-ray file formats

Dvd and Blu-ray folder structures are also supported. To be recognized as a dvd structure, the folder must contain either a VIDEO_TS subfolder, or a VIDEO_TS.ifo file. To be recognized as a blu-ray structure, the folder must contain a BDMV subfolder.

```
\Movies\Alien (1979)\VIDEO_TS.IFO
\Movies\Léon (1994)\VIDEO_TS.IFO
\Movies\Scarface (1983)\VIDEO_TS.IFO

Or:

 \Movies\Alien (1979)\VIDEO_TS\VIDEO_TS.IFO
 \Movies\Léon (1994)\VIDEO_TS\VIDEO_TS.IFO
 \Movies\Scarface (1983)\VIDEO_TS\VIDEO_TS.IFO
```

### ISO format

Emby Server has basic support for videos stored in ISO format. This includes the ability to catalog the ISO's within Emby Server, and play them in HTPC-based apps such as Emby for Kodi and Emby for Windows Media Center. Other apps will generally only be able to play them with the use of an external player.

ISOs should be named just like any other video file, with one minor difference. Including ".dvd" or ".bluray" within the file name will allow Emby Server to automatically determine what type of ISO it is. If this is not included, it will be assumed to be DVD.

```
\Movies\Alien (1979)\Alien (1979).dvd.iso
\Movies\Léon (1994)\Léon (1994).bluray.iso
\Movies\Scarface (1983)\Scarface (1983).iso
```

## Split video files (file stacking)

The following are default stacking extensions that can be added to file names. # can be 1 through 9 or A through D. Stacking is supported for video files as well as dvd and blu-ray folder structures.

* ​part#​
* ​cd#​
* ​dvd#​
* ​pt#​
* ​disk#​
* ​disc#​

You can also use:
* moviename#.ext

Where # can be A through D.

Examples:

```
\Movies\Avatar (2009)\Avatar (2009)-cd1.mkv
\Movies\Avatar (2009)\Avatar (2009)-cd2.mkv
```

## 3D videos

3D video files are supported. See [3D videos](3D-Videos).

## Media stubs

Media stubs are supported. See [media stubs](Media-stubs).

## Strm files

Strm files are supported. See [strm files](Strm-files).

## Subtitles

Subtitles are supported. See [subtitles](Subtitles).

## Theme songs & videos

Theme songs & videos are supported. See [theme songs & videos](Theme-songs-&-videos).

## Trailers

Trailers are supported. See [trailers](Trailers).