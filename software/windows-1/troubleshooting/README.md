---
description: Solutions to problems on Windows.
---

# Troubleshooting

## Error 80072efe

### Solution 1

Connectivity issue of some sort with Windows Update

From [http://answers.microsoft.com/en-us/protect/forum/mse-protect\_updating/error-code-0x80072efe/c23b0915-832f-4b11-9194-68362668d62d?auth=1](http://answers.microsoft.com/en-us/protect/forum/mse-protect_updating/error-code-0x80072efe/c23b0915-832f-4b11-9194-68362668d62d?auth=1)

### Solution 2

Wrong date.

**Source**: [http://answers.microsoft.com/en-us/protect/forum/mse-protect\_updating/error-code-0x80072efe/c23b0915-832f-4b11-9194-68362668d62d?auth=1](http://answers.microsoft.com/en-us/protect/forum/mse-protect_updating/error-code-0x80072efe/c23b0915-832f-4b11-9194-68362668d62d?auth=1)

### Solution 3

Disabling AdGuard for a couple of seconds.

## Readyboot keeps giving errors

Could this cause Windows hiccups? Because whenever weird app crashes happens, ReadyBoot gives errors in the logs.

* The protocol host process 6504 did not respond and is being forcibly

  terminated {filter host process 1156}.

* The maximum file size for session "ReadyBoot" has been reached. As a result,

  events might be lost \(not logged\) to file

  `"C:\WINDOWS\Prefetch\ReadyBoot\ReadyBoot.etl"`. The maximum files size is

  currently set to 20971520 bytes.

* Session "ReadyBoot" stopped due to the following error: 0xC0000188
* Faulting application name: dwm.exe, version: 10.0.10547.0, time stamp:

  0x55f616ec \(dwm.exe is the desktop window management\).

### Solution 1

An old thread and problem, but one that has been annoying me, and probably a few others. The solution to the error: "Session "ReadyBoot" stopped due to the following error: 0xC0000188" is simple, and it needs no discussion of Prefetch, ReadyBoost, or whether you are using an SSD \(as I am\). The problem, in my case, was that Readyboot needed more than the default 20MB size of the ReadyBoot.etl file to complete, By increasing the ReadyBoot.etl file size to 128MB I was able to see that it required 27MB to complete. I left it at 128MB as that isn't too much space to waste, and it allows for growth. Now that ReadyBoot is completing the above error has gone away. The hint was the warning in the Event Viewer prior to the above error. Specifically; "The maximum file size for session "ReadyBoot" has been reached. As a result, events might be lost \(not logged\) to file `"C:\Windows\Prefetch\ReadyBoot\ReadyBoot.etl"`. The maximum files size is currently set to 20971520 bytes." I just didn't know how to increase the file size before now. 

So here is the solution, based on a post by "Year" in this post: [http://forums.guru3d.com/showthread.php?t=318837](http://forums.guru3d.com/showthread.php?t=318837) 

Windows 7 set the ReadyBoot.etl file to 20MB and in the event logger this size often is maxed during boot \(aka not enough\), increasing it can really help. I do not recommend a value above 256mb, the best size imo is 128mb.

How to tweak it:

1. Search, Performance Monitor
2. on your left side, expand DATA COLLECTORS SETS
3. Click on STARTUP EVENT TRACES
4. on your right side you'll find a list, double click READYBOOT
5. click on the STOP CONDITION tab and set the size you want
6. press OK , close everything, reboot

To check if it worked, look in the Event Viewer to see the error didn't occur on the last reboot. \(If oyu have been rebooting a bit, note the time of the fix, and look for errors after that time. Also, look in `"C:\Windows\Prefetch\ReadyBoot"` \(or the appropriate directory for your installation\) and note the size of the ReadyBoot.etl file. It will probably be more than 20MB, as mine was.

**Source**: [https://social.technet.microsoft.com/Forums/windows/en-US/d74859fb-f1c1-434f-b084-fd26da581c6e/session-readyboot-stopped-due-to-the-following-error-0xc0000188?forum=w7itprogeneral](https://social.technet.microsoft.com/Forums/windows/en-US/d74859fb-f1c1-434f-b084-fd26da581c6e/session-readyboot-stopped-due-to-the-following-error-0xc0000188?forum=w7itprogeneral)

### Solution 2 \(Official MS solution\)

You are getting message that The maximum file size for session "ReadyBoot" has been reached. I have to let you know that ReadyBoot.etl log that tracks all file activity at boot time. Since all file activities done at boot time \(even system updates and spyware scans\) accumulates in this file, it may fill with obsolete information. The fix is to set the ReadyBoot.etl into Circular logging mode, so that only the most recent file access activity is tracked. To do so:

1. Click start, click control panel
2. Click administrative tools, performance monitor 
3. Expand left side tree entry for Data Collection Sets 
4. Highlight Startup Event Trace Sessions 
5. Open the ReadyBoot line \(click it\) 
6. Select the File tab 
7. Select the circular option 
8. Click apply and ok and restart the computer.

Superfetch service improves the performance and hence it is suggested to set its startup as automatic. Changing the registry value would increase the max size and it will reach the limit again and then again he may change the registry value.

**Source**: [http://answers.microsoft.com/en-us/windows/forum/windows\_7-performance/readyboot-and-superfetch/85d3f5f9-081c-49f3-affa-e9ad2aef2e03?auth=1](http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/readyboot-and-superfetch/85d3f5f9-081c-49f3-affa-e9ad2aef2e03?auth=1)

