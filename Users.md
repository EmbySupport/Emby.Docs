---
uid: Users
title: Users
legacyUrl: /support/solutions/articles/44001160237-users
---

Most operations within Emby are based around users. Users can have their own personalized media libraries, user data, recommendations, security settings, and more.

Users are managed within the server dashboard by navigating to **Users**. 

## Local Users

Local users are displayed under the user heading. These are users that you've created in the server dashboard, and are privately managed within your personal Emby Server.

The Emby Server setup wizard will create a user with administrative access. This screen allows administrators to add, edit and remove additional users.

![](images/server/users1.png)

A local user will be displayed with a cloud if it is linked to [Emby Connect](Emby-Connect.md).

![](images/server/users6.png)

Linking a user to Emby Connect will enable an easier sign in process that doesn't require the user to know your server's ip address. For more information, see [Emby Connect](Emby-Connect.md).

## Adding a User

To add a user, click the + button within the Users heading:

![](images/server/users7.png)

You'll then be taken to the new user page page. Any user can be granted administrative access which will allow them to utilize the server dashboard. The only required field is a user name:

![](images/server/users8.png)

Before saving, you can configure library and channel access, and this can easily be changed later. Deselect **All** to select specific libraries and channels:

![](images/server/users9.png)

![](images/server/users36.png)

After saving, you will then be able to do more customization for this user account.

You can link the local user account to an Emby Connect e-mail address. See [Emby Connect](Emby-Connect.md).

![](images/server/users37.png)

You can control remote connections to the server at the user level.

![](images/server/users18.png)

To manage user feature access, you can do this now or later by visiting the Users page and clicking on a user account. 

## Feature Access

Features can be granted or denied, such as the ability to delete media, download media, view live tv, manage live tv, etc. The "Allow media playback" option determines if the user is able to play media or not. This option is handy if you'd like to setup a user who can browse the library but not play anything.

![](images/server/users38.png)

![](images/server/users39.png)

You can set a limit on the number of concurrent video streaming sessions for the user. Note that this requires [Emby Premiere](Emby-Premiere.md) for it to be enforced. 

![](images/server/users40.png)

You can also limit the bandwidth per video streaming for devices away from the local network.

![](images/server/users41.png)

If you want to allow media deletions by the user, you cam select from the list of libraries and channels.

![](images/server/users42.png)

You can also decide how they can remote control shared devices. Remote controlling another user allows them to send content to devices for playback while another user is signed in. Remote controlling shared devices, such as Dlna devices, allows them to send content to those as well. These can be set now or later.

![](images/server/users19.png)

Other features can also be configured now or later. These cover Downloads, Subtitles, Camera Upload, Media Conversion, Sharing playlists and some limited media information sharing on social media.

![](images/server/users35.png)

![](images/server/users43.png)

![](images/server/users44.png)

![](images/server/users45.png)

![](images/server/users46.png)

![](images/server/users47.png)

Lastly, you can disable or hide a user, as well as lock them from changing their user profile settings.

Disabling a user will do just that. All existing sessions from that user will be abruptly terminated.

![](images/server/users33.png)

 Hiding a user will simply remove them from visual login screens. They will need to enter their username and password manually.

![](images/server/users28.png)

Disabling user preference access will prevent a user from changing their profile settings, such as their image, password, view preferences, language preferences, and more. This is useful for administrators who prefer to dictate these terms to their users.

![](images/server/users20.png)

## User Profile and Preferences

These can be set now or later, through the link "Edit this user's profile, image and personal preferences@.

![](images/server/users48.png)

The link takes you to the following screen which is the same screen that the user gets on selecting App Settings, if granted permission to edit the profile and preferences.

![](images/server/users49.png)

Clicking on the Profile button would allow upload of a profile image.

![](images/server/users50.png)

## Content Access

See [Content Access](Content-Access.md).

## Device Access

See [Device Access](Device-Access.md).

## Parental Controls

See [Parental Controls](Parental-Controls.md).

## User Password

See [Passwords](Passwords.md).


## Deleting a User

To delete a user, simply click the dot menu button and select Delete:

![](images/server/users5.png)