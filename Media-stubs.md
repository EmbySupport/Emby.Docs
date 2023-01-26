Emby has support for offline media stub files. These are files that represent a media outside of the online digital infrastructure and allow Emby's library to index your "offline" media collection, as well as ask for the media when selected for playback.

A stub file is an empty file with a ".disc" extension.

For example:

``` 
/Movies
     /Home Alone (1990)
         /Home Alone (1990).dvd.disc

``` 

## Media flags

You can optionally add media source flags to the filename before ".stub". This can be used to indicate the type of media (DVD, BLURAY, VHS, etc) that the movie resides on, which can be used for display purposes.

* DVD, if the filename contains DVD.
* Bluray, if the filename contains BLURAY, BRRIP, BD25, or BD50.
* HDDVD, if the filename contains HDDVD.
* TV, if the filename contains HDTV, PDTV, or DSR.
* VHS, if the filename contains VHS.

Examples:

``` 
/Movies
     Movie1.dvd.disc
     Movie2.bluray.disc
     Movie3.hdtv.disc
     Movie4.vhs.disc
     Movie1.hddvd.disc

``` 