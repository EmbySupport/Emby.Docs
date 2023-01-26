To make sure we get the best out of both Synology and XPEnology based Emby Server installations, we optimise the packages for the hardware on which they will run. This presents a challenge when it comes to XPEnology, which is discussed in more detail in the post '[XPEnology Users Read Me](https://emby.media/community/index.php?/topic/40411-xpenology-users-read-me/)'.

The default package source that should be used for XPEnology is:-

    https://synology.emby.media/?package_repository=360efc6e-de72-4073-b603-2bfbd7001586

However, if you find that Emby Server does not start after the install completes, it is likely you will need to use an alternate package architecture for your system.

__Alternate Architectures__

The following alternate package architectures are currently available:-

| Name | Description | Examples |
| :---- | :----------- | :------- |
| xpen-core2-sse41 | Intel(R) Core(TM)2 Duo + SSE41 | Intel Core2 Duo CPU E7200 @ 2.53GHz |
| xpen-core2 | Baseline Intel(R) Core(TM)2 Duo | Intel Pentium Dual-Core CPU T4500 @ 2.30GHz |
| xpen-sandybridge | Intel Sandy Bridge based Processors | Intel Core i5-4570S CPU @ 2.90GHz |
| xpen-barcelona | AMD Family 10h (or K10) based Processors | AMD Phenom(tm) II X6 1090T Processor |
| xpen-westmere | Intel Westmere based Processors | Intel Xeon X5690 @ 3.46GHz Processor |
| xpen-haswell| Intel Haswell based Processors | [See Wikipedia](https://en.wikipedia.org/wiki/Haswell_(microarchitecture)#List_of_Haswell_processors)|
|xpen-silvermont | Intel Silvermont based Processors | [See Wikipedia](https://en.wikipedia.org/wiki/Silvermont#List_of_Silvermont_processors)|

To use the alternate package architecture, you simply need to add it to the package source you configure in Package Center. Here's an example:-

    https://synology.emby.media/?package_repository=360efc6e-de72-4073-b603-2bfbd7001586&package_architecture=xpen-core2-sse41

__Need Help?__

Don't worry if you don't know what type of processor you have or don't see your processor architecture listed, take a look at the forum post above and drop us a line on the forum.

[>> Back to Synology : Help and Support <<](https://github.com/MediaBrowser/Wiki/wiki/Synology-:-Help-and-Support)