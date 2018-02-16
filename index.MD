---
title: Facundo Montero
published: true
---

# Welcome to my personal site!

This is the place where I'll post some of my most important projects and any other kind of experiments I do.

## TVHeadend FFMPEG conversion script

Sometimes, TVHeadend might become a true headache when it comes to setting it up for IPTV. For example, one of the most common problems that you might face, are general decoding bugs, unstability and huge problems while trying to scan a list (mainly m3u lists).

Browsing the internet about this issue, I ended in a thread of a forum that finally had a solution. Even though this solution could sound too "heavy" for a homemade system, it actually works!

I'm talking about [this](https://tvheadend.org/boards/5/topics/22969?r=22972#message-22972) post.

Well, enough intro, lets do it!

- Copy the URL of your remote IPTV channels list to the clipboard.
- Download the script to your device.

`wget https://raw.githubusercontent.com/FacuM/shellscripts/master/tvheadend/workarounds/convertoffmpeg.sh -qO ~/convertoffmpeg.sh`

or

`curl -q https://raw.githubusercontent.com/FacuM/shellscripts/master/tvheadend/workarounds/convertoffmpeg.sh > ~/convertoffmpeg.sh`

- Once done, open a terminal and type as follows.

### Method 1

###### (if you are going to use a remote list)

`bash ~/convertoffmpeg.sh http://example.com/yourlist.m3u`

### Method 2

###### (if you are going to use a local list)

`bash ~/convertoffmpeg.sh -f /path/to/your/list.m3u`

This will leave a list.m3u file in the working dir from where you ran the script.

---

Once the script is done, simply go to your TVHeadend web interface, go to **Configuration**, **DVB Inputs**, **Networks** and, in the taskbar, hit **Add**. In **Type**, choose **IPTV Automatic Network**.

Now, fill as follows:

- **Network name:** anything you want to name it.
- **Maximum # input streams:** set to your device's threads amount. **IMPORTANT!** *If you don't set it, your kernel will likely crash cause of being unable to process such amount of OOM triggering.*
- **URL:** set to *file:///path/to/the/list/processed/by/the/script.m3u*
- **Accept zero value for TSID:** mark it.
- **Maximum timeout (seconds):** increase to 30 seconds, just in case.

Done, hit **Create**. Now...

- Click or tap the network you just created, and hit **Force scan**. 

The column **Scan queue** will show you the remaining scans and auto-update itself as necessary. Once it reaches **0 (zero)**.

- Once it's done, switch to the tab **Services**.
- Hit **Map services** and choose **Map all services**.
- In the dialog, tick everything excepting from **Merge same name** *(unless you want to)*.
- Click or tap **Map services**.
- When the bar fills, go back to **Configuration**.
- Go to the tab **Channel / EPG**.

**That's all!** You've successfully configured your TVHeadend instance!