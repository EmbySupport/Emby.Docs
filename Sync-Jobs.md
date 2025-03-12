---
uid: Sync-Jobs
title: Download Jobs
legacyUrl: /support/solutions/articles/44001162175-sync-jobs
---

Download jobs can be for an individual media file download or a whole TV season or show and also possible to download a complete library. Download jobs also include those created for the [Folder Sync](Folder-Sync.md) feature.

Download jobs are created through the **Download** button within the Emby Apps that support downloads and also within context menu **Download to...** button which is available for media libraries contents. The **Download to...** button is also available in the [Emby Web client](Web-Client.md) app to initiate downloads to other apps and devices for the user account. For the various options available, see the [Download Options](Sync.md) article.


## Downloads Job Settings

When creating sync jobs, you'll be able to configure various settings for the job. The settings that are available will differ depending on the content being synced. See [Download Options](Sync.md) for details. The following lists the various options available.

Available settings are:

**Quality**

The desired quality level of the synced content. Higher produces better video quality but will require more storage space on the mobile device. The "Original" option can be used to force the process to utilize the original file, but this may result in the file not being playable on the device.

**Profile**

On some Emby client apps, an option is provided to select a pre-set download profile, as well as the option of having a custom profile.

**Unwatched Videos Only**

Only unwatched videos will be downloaded or copied, and videos will be removed from the device as they are watched. This option does not apply to [Folder Sync](Folder-Sync.md) download jobs.

**Automatically Download New Content**

New content added to the folder or category will be automatically synced to the device.

**Item Limit**

The maximum number of items that will be downloaded to the device at any given time.

## Subtitles

All available text-based subtitles are included with download jobs, allowing you to enjoy subtitle selection even when offline.

## Managing Download Jobs

Individual users can manage their own download jobs on each device. First select Downloads within the App Settings.

![](images/server/downloadjobs1.png)

Then open the **Manage Downloads** tab. This will list the download jobs for that user and device giving the status for each and through 
the dot menu button, there is an option to edit the download job or delete the download.

![](images/server/downloadjobs5.png)

Choosing **Edit** allows the user to amend the download job options.

![](images/server/downloadjobs4.png)


## Cancelling Download Jobs

To cancel a download job, simply click the dot menu next to a job and then select the **Remove Download** option. This will delete the download job as well as all files that have been copied as part of this job.

![](images/server/downloadjobs7.png)

Alternatively it's also possible to cancel individual items within a job by opening the download job edit screen and clicking the dot menu next to a download job item.

![](images/server/downloadjobs9.png)

## Administrative Management

Administrators can manage all download jobs for all users and devices by opening the server dashboard and navigating to **Downloads** within the **Devices** section of settings.

From here they'll be able to manage all jobs, job settings and job items and edit or remove downloads:

![](images/server/downloadjobs6.png)


The conversions and downloads tasks show up in the Emby Server **Scheduled Tasks** settings screen as **Convert Media** and **Transfer Media**.

![](images/server/scheduledtasks4.png)
