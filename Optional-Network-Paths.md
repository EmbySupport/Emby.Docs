By allowing Emby apps direct access to media folders on the server, they may be able to play them directly over the network and avoid using server resources to stream and transcode. Optional Network Paths (formerly Path substitution) can help achieve this by mapping a path on the server to a network path that can be accessed by other devices.

Network Paths are entered when you define the locations for your individual libraries.  Below the area where you indicate the local path to the location, there is an Optional Network Path field.  Enter the network share or UNC path for that same location into this field.

### Example:

You have a Movies library on the server as **D:\Movies**. This folder is also shared on the network as **\\\\Server\Movies**. You'd like to allow an Emby app on another machine direct access to the shared folder.

To do this, create the location pointing to D:\Movies and fill in the optional Network Path as \\\\Server\Movies

This will allow some Emby apps to access the media directly and avoid having to stream or transcode using Emby Server.