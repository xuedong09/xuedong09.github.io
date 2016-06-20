---
layout: post
title:  "virtualmachine"
date:   2016-06-20 09:30:15 +0800
categories: jekyll update
---

## vbox

### disable host and guest timesync

    1.Disable the time sync of your virtual machine:

    1.1 Disable Host to Guest Timesync

    VBoxManage setextradata <YOUR_VM_NAME> "VBoxInternal/Devices/VMMDev/0/Config/GetHostTimeDisabled" 1

    VBoxManage setextradata <YOUR_VM_NAME> "VBoxInternal/TM/TSCTiedToExecution" 1
    To revert back:

    VBoxManage setextradata <YOUR_VM_NAME> "VBoxInternal/Devices/VMMDev/0/Config/GetHostTimeDisabled" 0
    1.2 Disable GuestAddition Timesync

    Use the regedit.exe to modify the registry.

    Find this branch: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\VBoxService

    Change the value in ImagePath from

    system32\VBoxService.exe
    to

    system32\VBoxService.exe --disable-timesync
    Restart your VM or restart the service "VirtualBox Guest Additions Service".

    2.Disable the time sync of Windows.

    Check the time settings. Disable internet time sync.

## vmvare 

### use terminal find vmvare file like vm_name.vmx

    tools.syncTime = "0"
    time.synchronize.continue = "0"
    time.synchronize.restore = "0"
    time.synchronize.resume.disk = "0"
    time.synchronize.shrink = "0"
    time.synchronize.tools.startup = "0"
    time.synchronize.tools.enable = "0"
    time.synchronize.resume.host = "0"
    

### vmvare fusion

    tools.syncTime = "FALSE"
    time.synchronize.continue = "FALSE"
    time.synchronize.restore = "FALSE"
    time.synchronize.resume.disk = "FALSE"
    time.synchronize.shrink = "FALSE"
    time.synchronize.tools.startup = "FALSE"
    time.synchronize.tools.enable = "FALSE"
    time.synchronize.resume.host = "FALSE"



