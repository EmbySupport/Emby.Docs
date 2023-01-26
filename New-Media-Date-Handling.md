When adding new media to Emby there are two ways the date can be configured for newly added media.
The first method is to have Emby use the date the file is scanned into the system.
The second method is to have Emby use the date created time stamp of the media file itself.

As an example if the current date is March 20th and you have media that was created on January 10th then there are two different dates that could be used depending on the setting you have set in Emby.  If you use the date created, then once this new media is scanned into Emby it will be available but likely may not show up as "new" media since it will have a date added of Jan 10th.  If you use the scan date, then Emby will ignore the creation date and will use the date added of the exact day it first sees the media added to the system which would be March 20th.  In this case the media would show up as new.

There are two different ways that people use Emby and half of the users want this to function one way while the other half want it to function the other way.  Emby Server allows you to set this to function exactly how you want it to work.

This can be useful for example if you setup a new library or server pointing to existing media. In this case you would likely want the system to use the media creation date during the initial library build.  You could then change this to use the date scanned into the library after that by changing the option.

You can set this by selecting Library on the left hand administrator menu, then selecting the "Advanced" menu option on the header in the right side up top.

![library-advanced-file-date.png](images/server/library-advanced-file-date.png)

Don't forget to click the "Save" button after making any changes to this setting.

