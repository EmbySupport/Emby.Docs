---
uid: Premiere-Limits
title: Premiere Limits
longTitle: Is there a limit to Emby Premiere?
legacyUrl: /support/solutions/articles/44001173135-is-there-a-limit-to-emby-premiere
---

All of the standard Emby Premiere membership options are designed for single-household use and carry with them a limit of 30 devices supported for Emby Premiere features.  

In our experience over a number of years, this standard license is sufficient for 95%+ of our users.  If, however, you have a need to support more devices than this we do have several [extended device options](https://emby.media/premiere-ext.html) for you to choose from.

The Emby configuration dashboard will warn you if you are close to or over your device limit so the best thing to do is just wait for that to show you are close and then choose a larger option if desired.

Important points to remember:

* Very few users actually require more device support than the standard license.
* The limit applies only to Emby Premiere features so only apps that utilize those features will count towards the limit.
* The limit is a device limit NOT a concurrent connection limit.
* Each of your devices will need access to the internet and, specifically, mb3admin.com in order to validate the limit.
* The limit is tied to an Emby Premiere key, not a server so, if your key is in use on more than one server, then the limit will apply across all of them cumulatively.

## So how do I determine if the limit will be okay for me?

Look at the [Feature Matrix](Premiere-Feature-Matrix.md) and note the features you use that are NOT in the "Free" column.  Count the number of devices your users will use for just those features.  Even if this count is near the limit, we suggest you just try the normal license for a month of typical usage by your users and see if it works for you (it does for almost everyone).  Your server will show if you are close to or over the limit.

## How long does a device count towards my limit?

The system tracks device usage for about a week.  So you need to count only devices used regularly by your users when estimating the limit for you.  It is important to understand this is a device access limit NOT a concurrent connection limit.  

## How do I "knock" a device off the list?

You can't.  The system tracks this automatically.  Note, the devices you see listed in the "Devices" section of your dashboard are not your Premiere devices.  Premiere devices are tracked by key, not by server and only if they use Premiere features.

## Why can't I see which devices are counted in my limit?

Your Emby server has a "devices" tab that shows all devices that have ever connected to that server.  It is important to note that this is NOT Premiere devices as it relates to this limit. The total Premiere devices is likely much less than the ones shown in this tab.  You cannot see exactly which devices are counting towards your limit at this time.  The main reason we do not provide a way to do this at this time is security and privacy.  To allow your server to see this exact information would require us to expose a public API that provides this information.  Since we do not require you to have an account with us in order to use Premiere, there is no way for us to secure this API in a way that we are comfortable enough with to expose it.  We are working on ways we may be able to do this in the future.

## Does my server (or servers) count as a device?

No.  Only apps that use a Premiere-only feature count.


## Can I "stack" licenses to get more devices?
No. The licenses are only for the number of devices they indicate.  The 50 device upgrade is for 50 devices exactly, not 50 additional devices. 


## Can I buy more than one Premiere key?
Yes, but you must use a different email address (which means different PayPal account if using that payment method) for each key.  Since we don't require you to have an account, the email address is all we have to identify you and your key by so you cannot have two on the same email.
