Emby has native support for Silicon Dust HDHomeRun Network Tuners. Unlike other brands of tuners, HDHomeRun tuners run as standalone devices connected to your network. No need to have open PCI slots available in your server or free USB ports. Being a standalone device allows you to install these in close proximity to your OTA antenna or cable drop. As long as you can connect the device to your home Ethernet network you can install them anywhere in your home. Silicon Dust makes both OTA (Over the Air) models as well as Cable Tuners (using Cable Cards) to Receive DRM free digital cable subscription channels.

In most cases, Emby can automatically discover your HDHomerun devices on your network with no configuration required. You can also manually setup a tuner as well. 

The following guide assumes you have already setup your HDHomeRun on your network and have connected it to your cable or antenna.

Note: If you have an older HDHomeRun model that does not support DLNA or have a built in web server please perform these steps before continuing.
* [Older HDHomeRun Support](Older-HDHomeRun-Support)

Open the server dashboard and click the Live TV menu option on the left.  If you haven't setup any part of Live TV yet you should have a page that looks like this:

![hdhomerun1.png](images/server/hdhomerun1.png)

Click the plus sign next to TV Source in order to add our first tuner. We will then be presented with a screen that allows us to choose the type of tuner to add.  Select HD HomeRun from the drop down list of choices and then click the save button.

![hdhomerun2.png](images/server/hdhomerun2.png)

Emby will search your network and present all HDHomeRun devices it finds on your network.  Here is a example showing two Primes and one Quatro automatically found.

![hdhomerun3.png](images/server/hdhomerun3.png)

In this example we are going to setup OTA (Over the Air) using the HDHomeRun Quatro. Click the Quatro (3rd on this list). 

Emby will start the setup of this tuner and will provide you with the ability to set a couple of options including:
The ability to import all channels or only FAVORITE channels (already configured on the tuner itself).  See configuration of HDHomeRun favorites below for more information on using favorites.

The ability to use hardware transcoding on your tuner.  Note: this is only supported on HDHomeRun EXTEND models.

![hdhomerun4.png](images/server/hdhomerun4.png)

For this example using a Quatro we will enable the restriction of favorite channels and disable the hardware transcoding option. Once we’ve set our options the click save button and we will have added our first tuner. 

![hdhomerun5.png](images/server/hdhomerun5.png)

## HDHomeRun Favorite Setup

In order to make use of favorites with your HDHomeRun tuner you need to set this up outside of Emby.  You do this by opening the built in web app on your tuner in a web brower and then selecting the Channel Lineup menu option.  You can also just type the URL into your brower which will look similar to this:

http://192.168.100.23/lineup.html

Note this is the IP of the tuner as configure above in the example.  Once in the channel lineup screen it will look similar to this with your channels listed.

![hdhomerun-favorites.png.png](images/server/hdhomerun-favorites.png)

In this picture anything with the yellow star is marked as a favorite and used by the channel import above.  You can use the other two options which are unselected (blank) or X as status for your own use.  X would be disabled channels.  Blank could be channels you haven’t decided yet.  This is a really useful way to filter your channel list.  Many cable providers deliver both HD and SD versions of the same channels.  Using this method you can only favorite the HD channels.  You can easily ignore (not favorite) channels in foreign languages, shopping channels, infomercial channels or any other channel you wish to not have Emby load.