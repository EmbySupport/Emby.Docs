---
uid: Excluding-Files-Folders
title: Excluding Files & Folders
legacyUrl: /support/solutions/articles/44001159118-excluding-files-folders
---

Media files can be excluded during a library scan. This article shows how this can be done and gives details of the feature update that came in Emby Server version 4.9.

## Emby Server 4.9 and later

Media files can be excluded by adding a file named `.embyignore` containing the filename(s) path and/or pattern(s) to exclude. This can be added in the root folder of a library or within sub-folders.

On Windows. the `.embyignore` file can be created using Notepad with the "Save as type" set to "All files (\*.\*)"

![](images/server/excludes2.png) 

When adding the `.embyignore` to a root folder of a library, the rules would apply to all folders.

### Contents of the `.embyignore` file

- Comment lines can be added by having a \# character at the beginning of the line.
- Blank lines are ignored.
- Multiple patterns / names / paths can be entered on separate lines.
- A wildcard `*` can be used for file name / folder name pattern.
- Use forward slash character `/` for directory separator - even on Windows.
- When a directory separator is used, the pattern is relative to the directory holding the `.embyignore` file. Otherwise, the pattern may also match any level below the folder holding the `.embyignore` file.

### Examples

- To ignore all `.png` files in a photos library, place an `.embyignore` file containing `*.png` in the root folder(s) of a photos library.
- To ignore all files in a folder, place an `.embyignore` file containing a `*` in the folder that is to be ignored.
- To ignore a folder `private-vids` and all files and folders below it, place an `.embyignore` file containing `private_vids/` or `/private-vids/` in the parent folder.
- To ignore a specific file e.g. `private-video.mp4`, place an `.embyignore` containing `private-video.mp4` in the folder and lower sub-folders.
- To ignore files with names starting with `private` in this folder only, place an `.embyignore` containing `private*` in the folder.

The following are specific examples for a Home Videosa and Photos library with two root folders. The names have been chosen to make it easier to see the folder levels and where the files are located. The two root folders for the library identified as Root1 and Root2 with subfolders identified as A, B and C amd lower levels ientified as I, II and III.

We have an `.embyignore` in each of the two library root folders `Root1-Videos` and `Root2-Photos` and an `.embyignore` in folder `Root2-Photos\R2-Folder-A` to ignore a specific photo in that folder. The media files and folders are as follows:
```
My Videos and Photos
├───Root1-Videos
│   │   .embyignore
│   │   R1-Video1.MOV
│   │   R1-Video2.mp4
│   │
│   ├───R1-Folder-A
│   │       Private-Video.MOV
│   │       R1-A-Video1.MOV
│   │       R1-A-Video2.mp4
│   │
│   ├───R1-Folder-B
│   │   │   R1-B-Video1.MOV
│   │   │   R1-B-Video2.mp4
│   │   │
│   │   ├───R1-B-SubFolder-I
│   │   │       R1-B-SubFolder-I-Video1.MOV
│   │   │       R1-B-SubFolder-I-Video2.mp4
│   │   │
│   │   ├───R1-B-SubFolder-II
│   │   │       R1-B-SubFolder-II-Video1.MOV
│   │   │       R1-B-SubFolder-II-Video2.mp4
│   │   │
│   │   └───R1-B-SubFolder-III
│   │           R1-B-SubFolder-III-Video1.MOV
│   │           R1-B-SubFolder-III-Video2.mp4
│   │
│   └───R1-Folder-C
│           R1-C-Video1.MOV
│           R1-C-Video2.mp4
│
└───Root2-Photos
    │   .embyignore
    │   R2-Photo1.jpg
    │   R2-Photo2.jpg
    │   R2-Screenshot1.png
    │   R2-Screenshot2.png
    │
    ├───R2-Folder-A
    │       .embyignore
    │       R2-A-Photo1.jpg
    │       R2-A-Photo2.jpg
    │       R2-A-Screenshot1.png
    │       R2-A-Screenshot2.png
    │
    ├───R2-Folder-B
    │   │   R2-B-Photo1.jpg
    │   │   R2-B-Photo2.jpg
    │   │   R2-B-Screenshot1.png
    │   │   R2-B-Screenshot2.png
    │   │
    │   ├───R2-B-SubFolder-I
    │   │       R2-B-SubFolder-I-Photo1.jpg
    │   │       R2-B-SubFolder-I-Photo2.jpg
    │   │       R2-B-SubFolder-I-Screenshot1.png
    │   │       R2-B-SubFolder-I-Screenshot2.png
    │   │
    │   ├───R2-B-SubFolder-II
    │   │       R2-B-SubFolder-II-Photo1.jpg
    │   │       R2-B-SubFolder-II-Photo2.jpg
    │   │       R2-B-SubFolder-II-Screenshot1.png
    │   │       R2-B-SubFolder-II-Screenshot2.png
    │   │
    │   └───R2-B-SubFolder-III
    │           R2-B-SubFolder-III-Photo1.jpg
    │           R2-B-SubFolder-III-Photo2.jpg
    │           R2-B-SubFolder-III-Screenshot1.png
    │           R2-B-SubFolder-III-Screenshot2.png
    │
    └───R2-Folder-C
            Private-Photo.jpg
            R2-C-Photo1.jpg
            R2-C-Photo2.jpg
            R2-C-Screenshot1.png
            R2-C-Screenshot2.png
```

The `.embygnore` in `Root1-Videos` has the following content:
```
# This is the .embyignore file stored in the library root folder: Root1-Videos

# ignore all files and folders with names starting with "private-"
private-*

# ignore lower sub-directory R1-B-SubFolder-I
/R1-Folder-B/R1-B-SubFolder-I/
```
The `.embyignore` in `Root2-Photos` has the following content:
```
# This is the .embyignore file stored in the library root folder: Root2-Photos

# ignore all files and folders with names starting with "private-"
private-*

# ignore folder R2-Folder-B and all contents and children. the R2-Folder-B is directly below Root2-Photos
/R2-Folder-B

# ignore all images saved as *.png files 
*.png
```
These will result in all media or folders with names starting with "private-" getting ignored. All screenshots which would be png files get excluded from the photos folders. A specific photo folder and all its content excluded `R2-Folder-B`. A specific video folder `R1-B-SubFolder-I` getting excluded.

The 3rd `.embyignore` file is in photo folder `Root2-Photos\R2-Folder-A` to exclude a specific photo. The `.embyignore` content is:
```
# This is the .embyignore file stored in folder Root2-Photos\R2-Folder-A

# ignore a specific photo in this folder
/R2-A-Photo2.jpg
```

### Support for .plexignore

For your convenience, Emby Server now also supports `.plexignore`. An option has been added to Library settings for enabling this.

![](images/server/excludes3.png)

> [!NOTE]
> There may be some differences in outcomes between our support of this feature and Plex. The Emby behavior would not match any that are defects in Plex.



## Emby Server 4.8

To exclude a folder from the library scan, place a file named .ignore inside the folder.

This will cause Emby to ignore all sub-folders as well.

On Windows. the .ignore file can be created using Notepad with the "Save as type" set to "All types (\*.\*)" 

![](images/server/excludes1.png)
