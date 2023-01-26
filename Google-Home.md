# Emby with Google Home

1. [What is Google Home?](Google-Home#what-is-google-home)
2. [Get started](Google-Home#get-started)
    * [Why is Emby connect required?](Google-Home#why-is-emby-connect-required)
    * [Google Home account linking](Google-Home#google-home-account-linking)
    * [My server is not available to be selected](Google-Home#my-server-is-not-available-to-be-selected-what-do-i-do)
3. [Commands](Google-Home#commands)
    * [How to use Google Home](Google-Home#how-to-use-google-home)
    * [Select a player](Google-Home#which-player)
    * [Additional users](Google-Home#additional-users)
    * [Navigation](Google-Home#navigation)
    * [Playback](Google-Home#playback)
    * [Media playback](Google-Home#media-playback)
    * [Suggestion to watch](Google-Home#suggestions)
    * [Play random content](Google-Home#play-random-content)
    * [Play random music](Google-Home#play-random-music)
    * [Recently added](Google-Home#recently-added)
    * [Next up](Google-Home#next-up)
    * [Continue playing](Google-Home#continue-playing)
    * [Item modification](Google-Home#item-modification)
    * [Help with commands](Google-Home#help)
4. [Change Emby connect account](Google-Home#change-your-emby-connect-account)
5. [Frequently asked questions](Google-Home#FAQs)

### What is Google Home?  
Google Home is a powerful speaker and voice Assistant. Play your music. Call your friends. Ask it questions. Control your home. It's your own Google, always ready to help.
 
The Emby Skill enables users to get information about and control playback of their media library on any Emby compatible device. Once you have succesfully linked your Emby account to Google Home, you can start playing your favorite movies, TV shows on your devices with your voice.

## Get started  
The first step is to add Emby to your Google Home account by following the [steps here](https://support.google.com/googlehome/answer/7126338?co=GENIE.Platform%3DAndroid&hl=en) and searching for the Emby home app within actions (this is not a home control app). Once this is done, you will need [Emby Connect](Emby-Connect) to link your Emby account to Google Home. Emby home also requires [Emby premiere](https://emby.media/premiere.html). 

Google Home requests are sent from outside your network. You will need to ensure your Emby server is accessible remotely. 

#### Why is Emby connect required?
Emby connect is used to provide your server information to Google Home over a secure connection.

#### Google Home account linking
The first time you invoke Emby Home, you will be asked to link your Emby account. Enter your Emby connect credentials and select your server. This will enable the skill and work across all your Google Home devices linked to your Google Account.

You can link or unlink your Emby account [here](https://assistant.google.com/services/a/uid/000000b6334db7e5?hl=en).
![](https://i.imgur.com/lzbeWj0.png)


#### My server is not available to be selected, what do I do?
If you don't have an Emby account, follow the steps [here](Emby-Connect), otherwise:
1. In your server dashboard, Users > Select the Emby user with Emby connect (green cloud icon)
2. Remove the username or email from the Emby connect field, hit save.
3. Re-add the information to recreate the Emby connect link.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Commands
### How to use Google Home
* Every command needs to start with: **Ask MB Home {insert command}.**
* Alternatively, you can start an Emby session with: **Hey Google Home, talk to MB home.**  
_The benefit of using an Emby session is it allows you to give multiple commands without needing to invoke Emby for as long as the session is active. Sessions are automatically terminated after 8 seconds of inactivity._
* You can stop whatever Google Home is doing with: **Hey Google Home, cancel/nevermind.** Google Home will also abandon your request if you don't reply within 8 seconds.
* **Chromecast is not compatible due to limitation by Google at this time.**
* Not all commands are compatible with every Emby apps. If you encounter an issue, post [here](https://emby.media/community/index.php?/forum/174-amazon-alexa/).  
* To direct a command to a specific player, append **on {player name}** to the end of your command.
* Here is the list of supported media type: episode, movie, show, season, song, album, artist, audiobook, channel, playlist.
* If you are unsure of the active Emby user in Google Home, ask Emby home who's the user.
* **Parts of commands in parenthesis given below are optional**

#### Which player?
You can set a player as default. If a device/player name is not included at the end of your command, it will be automatically directed at your default player.
* change the player (to {player or device name})
* change my player to Living Room TV

#### Additional users
Share the watch status of currently playing content by adding other Emby users to your session.
* who is in the session
* add {user name} to my session
* remove {username} (and {username 2}) from my session

#### Navigation
You can navigate your interface by saying the movement or action related to what you want to do.
* move up/down/left/right
* page up/down
* select
* mute/unmute
* go home
* go to the next/previous letter
* show/display/bring up the context menu/TV guide/search/player menu (osd)/settings

#### Playback
* pause, previous, next, play (the selected content), **stop playback**
* set the volume (to {percent})
* change the audio (to {language})
* change/enable/disable subtitles
* change the subtitles (to {language})
* seek to {time} or start from the beginning
* seek to (plus/minus) {time}
* jump to chapter {number}
* go to the next/previous chapter

#### Media Playback
By default, Google Home is set to search video content when the content type is not specified. This means, for any other types, you need to include the content type to yield proper results.
* play (the movie) {movie}
* player (the show) {series}
* resume the episode from {series}
* play the artist {Artist}
* play the song {song} (from {Album}, by {Artist})
* play the audiobook {title}
* tune in channel {name}
##### Here are a few examples
* put on season 2 of Game of Thrones
* play Supernatural, season 5, episode 12
* play the new episode of Gotham
* watch the next episode of Orange is the new black

#### Suggestions
Reply to the suggestion with a yes or a no.
* give me a suggestion
* suggest me a {content type, i.e. movie} (genre {genre})
* I don't know what ({episode}) to watch
* what's good?

#### Play random content
* play something
* play a movie genre {genre i.e. horror}
* play an episode of {series}
* play **a few** episodes

#### Play random music
* drop the beat
* put on music (genre {genre})
* play songs (genre {genre})
* play songs by {Artist}
* play songs from the album {Album}

#### Recently added
* what's new
* what's been recently added?
* what {content type, i.e. movie} is newly added
* what is on {channel name}?

#### Next Up
* what's next
* what is up next

#### Continue playing
* what can I keep watching?
* what (show/movie/audio book) was I in the middle of?

#### Item modification
* add/remove to/from my favorites  {content type, i.e. movie} {title}
* set/mark as watched/unwatched {media type, i.e. movie} {title}

#### Transfer or Copy playback between devices
Transfer will stop playback first. Copy will simply resume playback where you left off, on the device of your choice. By default, it will fill in the missing information with your default player.
* transfer/copy the stream/playback (from {player}) (to {player})
* switch/copy the stream/playback (to {player}) (from {player})
##### For example
* Transfer the playback from chrome to theater.
* Copy playback to iphone. _omitting the origin of the playback will automatically grab it from your default player_

### Help
If you are ever uncertain what commands the player supports, ask Emby for:
* the available commands
* help

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

***