---
uid: QNAP-SSL-Certificate-Renewal
title: QNAP SSL Certificate Renewal
---

For Emby Servers running on **[QNAP QTS](https://www.qnap.com/en-uk/operating-system/qts)** and **[QNAP QuTS hero](https://www.qnap.com/en-uk/operating-system/quts-hero)** that have configured automatic SSL certificate renewals in QNAP, this article details a method for updating the SSL PFX certificate file used by Emby Server when Secure Connections are enabled for Emby Server as outlined in [Using Secure https Connections](Secure-Your-Server.md#using-secure-https-connections).

A shell script `QNAPEmbyCertRenew.sh` is provided that can be customized and scheduled to run daily, to check if the QNAP NAS has updated its SSL Certificate. If that is detected, the Emby Server SSL certificate pfx file would be replaced with one based on the renewed QNAP SSL certificate, with a password as specified in the script.


## Key Points

* The script can be customized to work on **QuTS hero** or **QTS** with default being **QTS**
* It allows for specifying a fixed path for the QNAP NAS certificate (QTS) or no path specified and the filesystem is searched for the latest certificate (QuTS hero)
* Emby Server is notified and updated with the new certificate (and its password) when a new QNAP Certificate is detected
* The creation of the Emby SSL certificate pfx file and the emby server update happens only once after each QNAP certificate renewal
* Emby Server would automatically restart when idle time is detected after the update to switch to the new certificate
* There is an option to disable the auto update of Emby Server
* The Emby Server pfx certificate files have unique names based on the UTC date & time of the QNAP certificate renewal and emby server pfx file update
* Old Emby Server pfx certificate files that were created with the same filename syntax and are over 6 months old are automatically purged
* The script is preset to use `/share/Emby-SSL-Certificate` for the Emby Server pfx files and the script log file.
* A log file is used to record actions by the script. The log filename is `cert-2-pfx-check.log`
* The script is preset to use local port `8096` for the Emby Server.
* The script is preset to check the QNAP SSL certificate in this file `/etc/config/QcloudSSLCertificate/cert/cert`. This should be correct for QTS. For QuTS hero the line should be commented out and a filesystem search would be used to locate the latest QNAP certificate.


## Requirements

* A share folder for holding the Emby Server certificate pfx file and the script and its log file: defaulted to `/share/Emby-SSL-Certificate`.
* An Emby API Key to use for notifying Emby Server of the updated SSL certificate pfx file.
* SSH connection to the QNAP NAS to setup the script. Refer to [QNAP: How Do I Access My QNAP NAS Using ssh](https://www.qnap.com/en/how-to/faq/article/how-do-i-access-my-qnap-nas-using-ssh).
* Tools such as **[PuTTY](https://putty.org/index.html)** for Windows to access the NAS through ssh.
* If using windows to edit the script, ensuring end of line characters are correct for linux - by using tool such as **[dos2unix](https://sourceforge.net/projects/dos2unix/)**.
* Using tools such as **[Notepad++](https://notepad-plus-plus.org/)** to view end of line characters.
* Familiarity with **crontab** file contents for scheduling the running of the script - see [QNAP: How to- Add Jobs to crontab to schedule a job](https://www.qnap.com/en/how-to/faq/article/how-to-add-jobs-to-crontab-to-schedule-a-job).
* Familiarity with using Linux text editors such as **[vi](https://www.redhat.com/en/blog/introduction-vi-editor)** for editing the `/etc/config/crontab` file. 


## Script File - QNAPEmbyCertRenew.sh

```
#!/bin/sh

# QNAPEmbyCertRenew.sh - version created 30 May 2026

# Script is based on one provided by dieffe70 https://emby.media/community/topic/113284-guide-ssl-qnap-certificate-and-emby-manual-and-automatic

now="$(date)"

# Password for exported PFX
PFX_PASSWORD="Replace-This-With-Your-PFX-Password"

# PFX Output file Directory - change the path for your specific /share path
PFX_DIR="/share/Emby-SSL-Certificate"

# Ensure directory ends with /
PFX_DIR="${PFX_DIR%/}/"

# The output certificate file generated will have a filename extension of ".pfx"
# The actual filename will be the PFX_FILE_PREFIX followed by the QNAP cert file UTC date/timestamp and the UTC date/time the pfx file generated
# and ending with the .pfx extension
PFX_FILE_PREFIX="embycert"

# Log file
PFX_LOG="${PFX_DIR}cert-2-pfx-check.log"

# This will ensure that the new QNAP certificate is only picked once
STATE_FILE="${PFX_DIR}.last_processed_time"

# Set this option to "NO" if you do not wish Emby Server to be notified of a change to the certificate
# Any change would only become active on restart of the Emby Server. 
# The default in this script is to notify Emby Server of any channge to the certificate
# Emby Server will pick the path and password and will automatically schedule a restart when the server is detected to be idle
AUTO_EMBY_UPDATE="YES"

# The option to notify Emby Server requires having an api key for use for the update
# See Emby Server Settings / Advanced / Api keys for generating an api key to use
# Enclose the api key between the quote characters on the following line
EMBY_API_KEY="Replace-This-With-Your-API-Key-For-EmbyServer"

EMBY_IP="127.0.0.1"

# Edit the following line if using non standard local port
EMBY_PORT="8096"

# Either specifiy a path for the cert file (QTS) or leave empty (QuTS hero) to search filesystem for it

# Comment out one of these 2 lines by prefixing it with a # as per other comments - defaulted to QTS
# The first is needed for QuTS hero - so you comment out the second
# The second is needed for QTS - so you comment out the first or leave as per default
QNAP_CERT_PATH=""
QNAP_CERT_PATH="/etc/config/QcloudSSLCertificate/cert/cert"

if [ -z "$QNAP_CERT_PATH" ]; then
	# For QuTS hero path may change so search filesystem for latest QNAP cert file
	echo "$now - Starting search of filesystem for the latest cert file" >> "$PFX_LOG"
	CRT_FILE=$(find /mnt -type f -name "cert" 2>/dev/null \
		| while read -r file; do
			stat -c "%Y %n" "$file"
		  done \
		| sort -nr \
		| head -n 1 \
		| cut -d' ' -f2-)

	if [ -z "$CRT_FILE" ]; then
		echo "$now - No certificate file found." >> "$PFX_LOG"
		exit 1
	fi
else
	# For QTS we pick the cert file as per the specified path
	echo "$now - Picking QNAP certificate from this file path $QNAP_CERT_PATH" >> "$PFX_LOG"
	CRT_FILE="$QNAP_CERT_PATH"

	if [ ! -f "$CRT_FILE" ]; then
		echo "$now - Specified cert file $CRT_FILE not found" >> "$PFX_LOG"
		exit 1
	fi
fi

CERT_DIR=$(dirname "$CRT_FILE")
KEY_FILE="$CERT_DIR/key"

echo "$now - CERT_DIR: $CERT_DIR" >> "$PFX_LOG"
echo "$now - CRT_FILE: $CRT_FILE" >> "$PFX_LOG"
echo "$now - KEY_FILE: $KEY_FILE" >> "$PFX_LOG"

if [ ! -f "$KEY_FILE" ]; then
	echo "$now - Private key not found: $KEY_FILE" >> "$PFX_LOG"
	exit 1
fi

# Get current file mtime (epoch seconds)
CURRENT_MTIME=$(stat -c %Y "$CRT_FILE" 2>/dev/null)

# If state file exists, read last processed time
if [ -f "$STATE_FILE" ]; then
	LAST_MTIME=$(cat "$STATE_FILE")
else
	LAST_MTIME=0
fi

# Only process if file is newer than last processed
if [ "$CURRENT_MTIME" -gt "$LAST_MTIME" ]; then

	echo "$now - Certificate has changed (mtime $CURRENT_MTIME > last processed $LAST_MTIME)" >> "$PFX_LOG"
	echo "$now - Using certificate directory: $CERT_DIR" >> "$PFX_LOG"
	echo "$now - Certificate: $CRT_FILE" >> "$PFX_LOG"
	echo "$now - Private Key: $KEY_FILE" >> "$PFX_LOG"

	# Convert epoch mtime to UTC yyyy-mm-dd_hh.mm.ss
	CURRENT_MTIME_UTC=$(date -u -d "@$CURRENT_MTIME" +"%Y-%m-%dT%H.%M.%SZ")
	CURRENT_TIME_UTC=$(date -u +"%Y-%m-%dT%H.%M.%SZ")

	# Build pfx filename
	PFX_FILE="${PFX_DIR}${PFX_FILE_PREFIX}_${CURRENT_MTIME_UTC}_${CURRENT_TIME_UTC}.pfx"

	echo "$now - Emby PFX: $PFX_FILE" >> "$PFX_LOG"
	
	# Create the PFX file
	OPENSSL_CMD="openssl pkcs12 -export \
		-out \"$PFX_FILE\" \
		-inkey \"$KEY_FILE\" \
		-in \"$CRT_FILE\" \
		-passout \"pass:$PFX_PASSWORD\""

	# uncomment next line to add extra logging if needed
	# echo "$now - Executing command $OPENSSL_CMD" >> "$PFX_LOG"
	
	eval "$OPENSSL_CMD"
	if [ $? -eq 0 ]; then
		echo "$now - PFX successfully created: $PFX_FILE" >> "$PFX_LOG"
	else
		echo "$now - PFX creation failed." >> "$PFX_LOG"
		exit 1
	fi

	# Save the processed certificate timestamp
	echo "$CURRENT_MTIME" > "$STATE_FILE"

	if [ "$AUTO_EMBY_UPDATE" = "YES" ]; then

		if [ -z "$EMBY_API_KEY" ]; then
			echo "$now - Cannot update Emby Server: no API key specified" >> "$PFX_LOG"
			exit 1
		fi

		if [ "$EMBY_IP" = "x.x.x.x" ]; then
			echo "$now - Cannot update Emby Server: server IP address not configured" >> "$PFX_LOG"
			exit 1
		fi

		PFX_DATA="{ \"CertificatePath\": \"$PFX_FILE\", \"CertificatePassword\": \"$PFX_PASSWORD\" }"
		
		EMBY_RESPONSE=$(curl \
			--write-out '%{http_code}' \
			--output /dev/null \
			--silent \
			-X POST \
			"http://$EMBY_IP:$EMBY_PORT/emby/System/Configuration/Partial" \
			-H "X-Emby-Token: $EMBY_API_KEY" \
			-H "Content-Type: text/plain" \
			--data-binary "$PFX_DATA")

		echo "$now - Emby Server Update Response: $EMBY_RESPONSE" >> "$PFX_LOG"

		if [ "$EMBY_RESPONSE" != "200" ] && [ "$EMBY_RESPONSE" != "204" ]; then
			echo "$now - Warning: Emby Server returned unexpected status code $EMBY_RESPONSE" >> "$PFX_LOG"
			exit 1
		fi
		# Purge pfx files created by this script more than 6 months ago
		PFX_PATTERN="${PFX_FILE_PREFIX}_????-??-??T??.??.??Z_????-??-??T??.??.??Z.pfx"	
		DELETE_CMD="find \"$PFX_DIR\" -type f -name \"$PFX_PATTERN\" -mtime +183"

		eval "$DELETE_CMD" | while IFS= read line
		do
			echo "$now - deleting $line" >> "$LOG_FILE"
			rm -f "$line" >> "$LOG_FILE" 2>&1
		done
		
	else
		echo "$now - Emby Server not updated - AUTO_EMBY_UPDATE option not set to YES" >> "$PFX_LOG"
		echo "$now - Emby Server Network Settings should be updated manually to specify the path as ${PFX_FILE}" >> "$PFX_LOG"
		echo "$now - Also make sure the Emby Server certificate password is set to the value specified in this script" >> "$PFX_LOG"
	fi
	
else
	echo "$now - Certificate unchanged (mtime $CURRENT_MTIME, last processed $LAST_MTIME) - skipping" >> "$PFX_LOG"
fi
```

## How to obtain an API Key for Emby Server

The script needs to have an **Api key** to allow it to communicate with the Emby Server. An **Api key** can be generated by going the Emby Server **Settings** dashboard and then in the **Advanced** section in the sidebar on the left, selecting **Api Keys** and then **+New Api Key**. After clicking on **+New Api Key**, you will be asked to assign a name to the API Key. Suggest you name it `QNAP Emby CertRenew Script` and then click **Submit**. 

The key will appear in the list of Api Keys. To be able to copy the api key to the clipboard through the **...** button on the right, you would need to be connected to the server through an https secure connection. If you are not, you would need to manually select the displayed api key and using **control and C** to copy it. Paste the key into script in the field within the quotes on the script line starting with `EMBY_API_KEY=` replacing the preset text.


## Lines to edit in the provided script

The following lists all the lines that should be edited and set.

The `PFX_PASSWORD` is the password for the Emby Server pfx certificate file that will be generated and will be set when the pfx file update is notified to Emby Server.

The `EMBY_API_KEY` will hold the api key you generated above.

One of the two `QNAP_CERT_PATH` lines should be commented out by placing a `# ` before the text.
```
PFX_PASSWORD="Replace-This-With-Your-PFX-Password"
EMBY_API_KEY="Replace-This-With-Your-an-API-Key-For-EmbyServer"
QNAP_CERT_PATH=""
QNAP_CERT_PATH="/etc/config/QcloudSSLCertificate/cert/cert"
```

For **QNAP QTS** where the certificate is expected to be in a fixed location, you would have the lines as:
```
# QNAP_CERT_PATH=""
QNAP_CERT_PATH="/etc/config/QcloudSSLCertificate/cert/cert"
```

For **QNAP QuTS hero** where the certificate location is not fixed, you would have the lines as:
```
QNAP_CERT_PATH=""
# QNAP_CERT_PATH="/etc/config/QcloudSSLCertificate/cert/cert"
```

The following gives other settings in the script that can be modified.

If you have a different share folder for holding the script and log and the pfx certificates, change the `PFX_DIR` path.

Change the `EMBY_PORT` number if your server has a non standard local port.

If you change the auto update option, then you will need to manually update the server network settings to use the new certificate file and password. See [Setup Emby Server with your domain and SSL certificate](Secure-Your-Server.md#setup-emby-server-with-your-domain-and-ssl-certificate).

```
PFX_DIR="/share/Emby-SSL-Certificate"
AUTO_EMBY_UPDATE="YES"
EMBY_PORT="8096"
```

> [!Note]
> In all the instructions below, it is assumed that the script will be in folder `/share/Emby-SSL-Certificate/`. Modify the steps shown below if you chose a different location for the script and/or PFX_DIR.


## Copy the script file to the NAS

Having completed all the edits to the script file, and with access from a PC to the share where you will have the script and Emby certificate pfx files on the NAS, copy the `QNAPEmbyCertRenew.sh` script to that share folder on the QNAP NAS. It is suggested you use the same directory for the Emby SSL certificate pfx files. 

Assuming the path on the NAS is `/share/Emby-SSL-Certificate`, copy the edited `QNAPEmbyCertRenew.sh` to this directory. Next you will need to check and correct the end of line characters, if necessary.


## How to use Notepad++ to check for end of line character

If using Windows to create and edit the script, you may end up with windows **CR** / **LF** at end of lines. On Linux it needs to be just **LF**.

You can check with **[Notepad++](https://notepad-plus-plus.org/)** to see if you need to use **[dos2unix](https://sourceforge.net/projects/dos2unix/)** to replace the **CR LF** with **LF**.

In **Notepad++**, with the script file open, select **View** >> **Show Symbol** >> **Show All Characters**.

If all lines end with **LF** then no action is needed. 

If all or some lines end with **CR LF**, you will need to use **dos2unix** to update the file. Either way, there is no harm in doing it anyway.

This is an example of how you would use **dos2unix** on windows. 

In this example, assume that the [dos2unix tools](https://sourceforge.net/projects/dos2unix/) were downloaded into the **Downloads** folder as `dos2unix-7.5.5-win64.zip`, being the file for the current version at time of writing this article.

Unzip the files. The `dos2unix.exe` binary would be within the `dos2unix-7.5.5-win64\bin\` folder. 

We will assume that the script has been copied to the NAS and the path is, as example, `\\NAS\Emby-SSL-Certificate\QNAPEmbyCertRenew.sh` where "NAS" is the hostname for the QNAP NAS or the local IP Address.

Ensure all the changes to the script have been made and saved and the editor is closed.

Open a windows **cmd.exe** session and type command similar to this - replace `NAS` with the NAS hostname or IP Address. Also have the correct directory name for the unzipped dos2unix tool, e.g.:

```
"%HOMEPATH%\Downloads\dos2unix-7.5.5-win64\bin\dos2unix.exe"  "\\NAS\Emby-SSL-Certificate\QNAPEmbyCertRenew.sh"
```
This will display a message that the file has been converted to Unix format.

After this, you can double check with Notepad++ that the CR LFs have been replaced with LFs at end of each line.


## Set Execute permissions for the script

With ssh enabled on the QNAP NAS - see [QNAP: How Do I Access My QNAP NAS Using ssh](https://www.qnap.com/en/how-to/faq/article/how-do-i-access-my-qnap-nas-using-ssh), use **[PuTTY](https://putty.org/index.html)** to establish a shell ssh connection to the QNAP NAS.

Login with the QNAP admin account.

Add execute permission to the script file

```
chmod +x /share/Emby-SSL-Certificate/QNAPEmbyCertRenew.sh
```

You can use `ls -ail /share/Emby-SSL-Certificate/` to check the permissions for the file.


## Do a manual test to run the script

Do this using the ssh PuTTY session. 

Note that the first time you run the script, it will update Emby Server with a new certificate pfx even if the QNAP SSL certificate has not changed. So be prepared for the server restarting sometime after running the script is executed for the test. The restart would happen when the Emby Server detects idle state.

> [!Note]
> It has been seen that having DLNA Server enabled may impact the detection of idle state for the auto restart.


Execute the script by typing in this command
```
/bin/sh  /share/Emby-SSL-Certificate/QNAPEmbyCertRenew.sh
```

Now check the log file. If the folder is accessible on a PC, do that using the PC viewing the file `\\NAS\Emby-SSL-Certificate\cert-2-pfx-check.log` with a text editor. Replace `NAS` with the NAS IP address or host name.

Or you can do that on the NAS in the ssh session, by typing the following:

```
tail -n 20 /share/Emby-SSL-Certificate/cert-2-pfx-check.log
```

If a pfx file was created and emby server notified, then proceed to next section of automating the running of this script.


## Schedule the script to run daily

With the QNAP renewing the certificate weeks before expiry, it should be sufficient to run the script once each day. But you can run it more than once by customizing the crontab line.

The steps outlined below will schedule the script to run once daily at 1 am.

It is assumed that you are familiar with using a linux text editor such as **[vi](https://www.redhat.com/en/blog/introduction-vi-editor)** and know how to insert a line and save the edit and exit the editor.

Connect to the QNAP using PuTTy as before and login using the admin account.

We will add the following line to the end of the `/etc/config/crontab` file:

```
0 1 * * * /bin/sh  /share/Emby-SSL-Certificate/QNAPEmbyCertRenew.sh
```

Use the editor to edit `/etc/config/crontab` and add this line as the last line, e.g.

```
vi /etc/config/crontab
```

Save the changes and exit the editor.

Now you must get crontab to pick the changed file. Type this command line:

```
crontab /etc/config/crontab && /etc/init.d/crond.sh restart
```

You can check that the crontab line has now been added by executing this command
```
crontab -l
```
(this is lowercase L)

The following day, inspect the script log file `/share/Emby-SSL-Certificate/cert-2-pfx-check.log` to check that the script did run at 1 am. 
