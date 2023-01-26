The hardware requirements for the server will depend on a number of factors including the format of your prepared media, the type of client devices used as well as how much bandwidth is available between the client and the server.

If you prepare you media in a format that all devices can use, such as MP4 container, using H.264 video with a stereo AAC audio track then you won't need a powerful server normally because all Emby apps can use that format directly.  If however you don't prepare your media ahead of time like this or if you don't have adequate bandwidth between the client and server to play the media AS IS then the Emby Server will assist you by transcoding (converting) your media on the fly in real-time.  

Transcoding is the process where media is converted from one resolution or format to another (e.g. playing Full HD media on some smartphones requires transcoding). The process is CPU-intensive, so an older/slower PC might not be up to the task.

## Windows, Mac, Linux, or FreeBSD computer
### Minimum Requirements — no transcoding
* Intel Core 2 Duo processor 1.6 GHz or better
* At least 1GB RAM for Windows/Mac OS X
* At least 512MB RAM for Linux
* Windows: Vista or later
* OS X: Snow Leopard 10.6.3 or later
* Ubuntu, Debian, Fedora, CentOS or SuSE Linux

### Recommended Configuration — transcoding HD Content:
* Intel Core 2 Duo processor 2.4 GHz or better
* If transcoding for multiple devices, a faster CPU may be required
* At least 2GB RAM
* Windows: Vista or later
* OS X: Snow Leopard 10.6.3 or later
* Ubuntu, Debian, Fedora, CentOS or SuSE Linux

> [!NOTE]
> Emby also supports Hardware Based Transcoding using a GPU/Video card (if new enough). This can substantially reduce the CPU requirements needed for multiple transcodes in real-time!  This allows the server to support numerous clients at the same time without your computer's CPU being overworked. Some GPUs can support 20+ streams. That's in addition to the streams your Emby server can handle without transcoding!

## Network Requirements
### Minimum requirements
* An ADSL/Cable/WiFi Internet connection for media metadata and software updates
* Uncongested WIFI with a strong signal using 802.11n wireless network OR
* Wired Ethernet network

### Recommended configuration
* An ADSL/Cable/WiFi Internet connection for media metadata and software updates
* 10 Meganit upload bandwidth (minimum) if serving content remotely
* Uncongested, WIFI with strong signal using 802.11AC wireless network
* Wired Gigabit Ethernet network