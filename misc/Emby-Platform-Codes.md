---
uid: Emby-Platform-Codes
title: Emby Platform Codes
---


# Emby Platform Codes

## About

### What it is

An Emby Platform Code is an encoded piece of information about a user's hardware and software system configuration, represented as a simple string of numbers and uppercase letters.  
These codes are shown in Emby apps and are printed in logfiles. Users can take those codes and copy/paste them into an online form which generates a visual representation of their system specs which they can then add as signature to their forum account.

### Motivation

There exists a long tradition in community forums where users are indicating their system specs - hardware and/or software - in their signatures. Often used as a kind of show-off, but that is not the only use case.  
When users are reaching out for support through the forums, it is rarely clear from the first moment on, about which kind of setup their request is about. It almost always requires to specifically ask for that or for providing logfiles from which the information can be seen. While each user knows exactly about their specific issue and their setup, this is often a struggle on our side: we cannot memorize each case we are responding to and finding the information from posted logfiles each turn again is tedious, time consuming and often just skipped therefore, potentially even causing responses that might not be as good as they could be.  
With the new Emby Linux app, the impact is growing even exponentially: without knowing a user's setup right from the start, there is often no point to even think about and to reply to a request as most issues are highly system-dependant.


### Emby Linux Beta

We are introducing the Platform Code system alongside the public beta test of the new Emby Linux app. It is intended to extend this to other apps and platforms in the future.

Generally, there are no intentions to require users for creating and adding forum signatures based on Platform Code, but there is one exception:

> [!WARNING]  
> For the Linux Beta, users are REQUIRED to have a platform-code signature when posting in the forums. Posts from users without a platformcode signature will not be responded to.


## Setting up the Forums Signature

### Find the Code

- Go to settings: On the home view, click on the gear icon at the right top
- In the navigation menu, choose "About"
This is usually the topmost item. If you are admin of the Emby Server, you might see the server dashboard first and the section with the About entry needs to be expanded first
- On the About page find the entry named **Platform Code**
- Select the code and copy to the clipboard

### Generating the Signature

- Go to:  https://emby.media/support/Platform-Code-Builder.html
- Paste the code and click **Generate**
- Click **Copy to Clipboard**

### Adding the Signature

- Log in to the [Emby Forums](https://emby.media/community)
- click your user menu at the right top
- Choose **Account Settings**
- From the left tab buttons, click **Signature**
- Clear all content  
  Press CTRL-A (select all) and then DEL or backspace
- Paste the copied signature
- Click "Save"

