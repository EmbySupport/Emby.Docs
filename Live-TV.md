---
uid: Live-TV
title: Live TV Setup
legacyUrl: /support/solutions/articles/44001160415-live-tv-setup
---

## Introduction

Emby provides a flexible and very powerful Live TV and DVR solution.  With Emby’s TV you will be able to stream Live or Recorded TV content to any device you have with an Emby client or web browser.

You can use Emby to eliminate the need for cable STBs (Set Top Boxes) or you can eliminate your cable provider entirely by cutting the cord and switching to OTA (Over the Air) broadcasts for local channels.

Emby provides free guide data (US, UK & Canada) right out of the box at no additional cost.

## Overview of Setup

Setup of Live TV can be broken down into a few steps:
* Configure your TV Tuner(s) or M3U based IPTV sources
* Add TV Guide Data Source(s)
* Match your Channel Lineup to Guide Data (Channel Mapping)

## Configure Your TV Tuner

Out of the box, Emby Server currently supports the following TV Tuners:

- [HDHomerun Network Tuner](xref:HDHomeRun-Setup) (Models available for both OTA and Cable)
- Hauppauge TV Tuners (on Emby Server for Windows - Requires Win TV 8.5 or greater to be installed)
- @M3U-Tuners  
M3U files (or urls). See examples of m3u files at http://xmtvplayer.com/build-m3u-file

Support for additional tuners can be added by installing a [Live TV Plugin](Live-TV-Plugins).

In most cases, Emby Server will automatically discover your HDHomerun on your network with no configuration required. You can manually add a tuner as well.  Simply open the server dashboard, navigate to **Live TV**, then click **Add** underneath tuner devices.

## Add a TV Guide Data Source

Out of the box, Emby Server currently supports the following TV Guide data sources:

* [Emby Guide Data](Emby-Guide-Data)  
  (United States, Canada and United Kingdom)
* [Schedules Direct](Schedules-Direct)  
  (Do not use on new setups. Will stop working June 1st, 2021)
* [Xml TV](Xml-Tv)

Support for additional sources can be added by installing a [Live TV Plugin](Live-TV-Plugins).

## Match your Channel Lineup to Guide Data
The final step of setting up Live TV is matching the tuner's stations to the Guide Data you have setup.

* [Live TV Channel Mapping](Live-TV-Channel-Mapping)

## DVR Settings (optional)

You can optionally change a few options used for DVR purposes.  These options include:
* Amount of days of Guide Data loaded
* Default recording pathes
* Default Pre and Post recording padding times.  This allows you set recording to start X minutes early and finish Y minutes late.

* [DVR Settings](DVR-Settings)

## Emby Live TV & DVR is Ready to Use.
Congratulations, your Emby Server should now be configured properly and ready to use for Live TV and DVR.