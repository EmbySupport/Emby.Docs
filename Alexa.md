# Emby with Amazon Alexa
[Emby skill](https://skills-store.amazon.com/deeplink/dp/B07F8VC9F9?deviceType=app&share&refSuffix=ss_copy) Available in English US, UK, Canada, Australia, India  
_The skill in German and French is being worked on. This page will be updated when the skill will be available in the Amazon Skills Store._


1. [What is Alexa?](Alexa#what-is-alexa)
2. [Get started](Alexa#get-started)
    * [Why is Emby connect required?](Alexa#why-is-emby-connect-required)
    * [Amazon Alexa account linking](Alexa#amazon-alexa-account-linking)
    * [My server is not available to be selected](Alexa#my-server-is-not-available-to-be-selected-what-do-i-do)
3. [Training Alexa](Alexa#training-alexa)
3. [Commands](Alexa#commands)
    * [How to use Alexa](Alexa#how-to-use-alexa)
    * [Playback on Alexa](Alexa#using-alexa-as-a-player)
    * [Select a player](Alexa#which-player)
    * [Select an Emby user](Alexa#which-emby-user)
    * [Additional users](Alexa#additional-users)
    * [Navigation](Alexa#navigation)
    * [Playback](Alexa#playback)
    * [Media playback](Alexa#media-playback)
    * [Suggestion to watch](Alexa#suggestions)
    * [Play random content](Alexa#play-random-content)
    * [Play random music](Alexa#play-random-music)
    * [Recently added](Alexa#recently-added)
    * [Next up](Alexa#next-up)
    * [Continue playing](Alexa#continue-playing)
    * [Item modification](Alexa#item-modification)
    * [Help with commands](Alexa#help)
4. [Change Emby connect account](Alexa#change-your-emby-connect-account)
5. [Frequently asked questions](Alexa#FAQs)

### What is Alexa?  
Amazon Alexa is a cloud-based voice service, so it is always getting smarter. Ask Alexa to play music, hear the news, check weather, control your smart home, and more.
 
The Emby Skill enables users to get information about and control playback of their media library on any Emby compatible device. Once you have succesfully linked your Emby account to Alexa, you can start playing your favorite movies, TV shows on your devices with your voice.

## Get started  
The first step is to add [Emby with Alexa](Alexa#emby-with-amazon-alexa) to your Amazon account. Once this is done, you will need [Emby Connect](Emby-Connect) to link your Emby account to Alexa. Emby with Alexa also requires [Emby premiere](https://emby.media/premiere.html). 

Alexa requests are sent from outside your network. You will need to ensure your Emby server is accessible remotely. 

#### Why is Emby connect required?
Emby connect is used to provide your server information to Alexa over a secure connection.

#### Amazon Alexa account linking
In the Amazon Alexa app or the [Amazon Alexa web app](http://alexa.amazon.com/spa/index.html), navigate to the following:  
`Skills > Your Skills > Emby > Link Account`

![Skills screenshot](https://emby.media/community/uploads/inline/4388/58fd8d3a8680b_Instructions_small.jpg)
#### My server is not available to be selected, what do I do?
If you don't have an Emby account, follow the steps [here](Emby-Connect), otherwise:
1. In your server dashboard, Users > Select the Emby user with Emby connect (green cloud icon)
2. Remove the username or email from the Emby connect field, hit save.
3. Re-add the information to recreate the Emby connect link.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Training Alexa
Alexa may have difficulty understanding the word Emby at first. There are ways to improve this situation.
#### English US only
If Alexa is set to English US, you have access to voice training. Using this, Alexa will start understanding you instead of guessing what you said. In the Amazon Alexa app or the [Amazon Alexa web app](http://alexa.amazon.com/spa/index.html), navigate to the following:

`Settings > Under Accounts > Voice training`

#### Every languages
The Amazon Alexa app offers feedback cards for skills. This allows Alexa to self-correct, by marking these cards positively or negatively depending on if Alexa understood you or not. In the Amazon Alexa app or the [Amazon Alexa web app](http://alexa.amazon.com/spa/index.html), navigate to the either:

`Home > Cards regarding Emby > More > Did Alexa understand you?`  
`Settings > General > History > Did Alexa do what you wanted?`
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Commands
### How to use Alexa
* Every command needs to start with: **Alexa, tell/ask m. b. home to {insert command}.**
* Alternatively, you can start an Emby session with: **Alexa, start/begin/open m. b. home.**  
_The benefit of using an Emby session is it allows you to give multiple commands without needing to invoke Emby for as long as the session is active. Sessions are automatically terminated after 8 seconds of inactivity (when the blue ring of your Alexa device fades)._
* You can stop whatever Alexa is doing with: **Alexa, cancel/nevermind.** Alexa will also abandon your request if you don't reply within 8 seconds.
* Not all commands are compatible with every Emby apps. If you encounter an issue, post [here](https://emby.media/community/index.php?/forum/174-amazon-alexa/).  
* To direct a command to a specific player, append **on another player** or **on {player name}** to the end of your command.
* Here is the list of supported media type: episode, movie, show, season, song, album, artist, audiobook, channel, playlist.
* **Parts of commands in parenthesis given below are optional**

### Using Alexa as a player
Audio playback is supported at this time. This feature requires your server to be secured with ssl encryption. Refer to [this guide](Secure-Your-Server) if you need help. Self-signed certificates are not supported for this.

​Ask m. b. home to play music. Specify "on this player" or "on Alexa" at the end of your request to skip the player selection. Once [music playback](Alexa#media-playback) is initiated with the skill, you can use these controls (notice you don't invoke m. b. home):
* Alexa, Next
* Alexa, Previous
* Alexa, Pause
* Alexa, Resume
* Alexa, start over
* Alexa, loop (This is to repeat the currently playing item. Loop off to turn off)

#### Which player?
You can set a player as default. If a device/player name is not included at the end of your command, it will be automatically directed at your default player.
* change the player (to {player or device name})
* change my player to Living Room TV

#### Which Emby user?
By default, the skill will use the same Emby user used to link Alexa to Emby. But it can be changed with the following:
* who is the active user
* change the user (to {Emby username})
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
* pause, previous, next, play (the selected content), **stop or stop playback**
* set the volume (to {percent})
* change the audio (to {language})
* change/enable/disable subtitles
* change the subtitles (to {language})
* seek to {time} or start from the beginning
* seek to (plus/minus) {time}
* jump to chapter {number}
* go to the next/previous chapter

#### Media Playback
By default, Alexa is set to search video content when the content type is not specified. This means, for any other types, you need to include the content type to yield proper results.
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
* suggest me a ({genre}) {content type, i.e. movie}
* I don't know what ({episode}) to watch
* what's good?

#### Play random content
* play something
* play a movie (genre {Genre})
* play an episode of {series}
* play **a few** episodes
* play next up

#### Play random music
* drop the beat
* put on some music (genre {Genre})
* play songs (genre {Genre})
* play songs by {Artist}
* play songs from the album {Album}

#### Recently added
* what's new
* what's been recently added?
* what {content type, i.e. movie} is newly added

#### Next Up
* what's next
* what is up next

#### Continue playing
* what can I keep watching?
* what (show/movie/audio book) was I in the middle of?

#### Item modification
* remove {title} from my favorites
* add ({content type, i.e. movie}) {title} to my favorites
* I love the {media type, i.e. music video} {music video}
* set/mark {media type, i.e. movie} {title} as watched/unwatched

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

### Change your Emby connect account
You can easily replace the Emby connect account linked to Alexa. First, you will need to disable the Emby skill. Then, once re-enabled, go though the account linking process again.

### FAQs
- **Alexa can't find any players.**  
    Make sure your Emby player is up and running under the same Emby user Alexa is connected to.
- **My title is recognized with the wrong words?**
    That's what happens with voice control. Correct the title [here](https://goo.gl/forms/SnruVeWIBFyufxZr1). 
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>