# environment-windows-kernel
Research environment for the windows kernel

## Synopsis

The project is set of script and tools that help to start researching the windows kernel

## Motivation

Curiosity dive to system internals, os inner workings and kernel driver security

## Prerequisites
What things you need

```
Host: Linux
 
VMware Workstation 15.0
ISO: Windows 10 - Home,x64, 10.0.17134 Build 17134
ISO: Windows 7 - Professional, x86, sp1 677056
WinDBG
Sysinternals Suite
```

### Downloading tools

A step by step series of examples that tell you have to get a development env running


VMware Workstation
```
https://my.vmware.com/en/web/vmware/info/slug/desktop_end_user_computing/vmware_workstation_pro/15_0
```

Windows ISO's
```
http://windowsiso.net/
```

WinDbg
```
https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk
```

![windbg_download](/assets/windbg_download.png)

Sysinternals Suite
```
https://docs.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite
```

![sysinternals_download](/assets/sysinternals_download.png)

IDA-Pro
```
https://www.hex-rays.com/products/ida/support/download.shtml
```

Check 'Configuring tools' to configure the tools 

### Configuring tools

Create VM Instances & install windows

![windows_vms](/assets/windows_vms.png)

Install WinDBG on Win10

![windbg_window](/assets/windbg_window.png)

Configure VM Instances Serial Port
```
a.  Fill in the parameters for Win10:
        socket: "/tmp/win_link"
        from: Server
        to: A Virtual Machine
b.  Fill in the parameters for Win7:
        socket: "/tmp/win_link"
        from: Client
        to: A Virtual Machine
```

![win10x64](/assets/win10x64_edit.png)

![win10_settings](/assets/win10_settings.png)

![win7x86](/assets/win7x86_edit.png)

![win7_settings](/assets/win7_settings.png)

Configure WinDBG in Win10
```
a.  Open WinDBG
    Ctrl+K -> Kernel Debugging
    Choose COM
b.  Fill in the parameters
        Baudrate: 115200
        port: com1
        pipe: not checked
        reconnect: not checked
        resetes: 0
```

![kernel_debugging_setup](/assets/kernel_debugging_setup.png)

![windbg_waiting_to_reconnect](/assets/windbg_waiting_to_reconnect.png)

Configure debugging boot in Win7
```
a.  Open CMD with administartor permissions
b.  Configure boot in bcdedit:
        bcdedit /dbgsettings serial debugport:1 baudrate:115200
```

![win7_cmd_admin](/assets/win7_cmd_admin.png)

![win7_bcdedit](/assets/win7_bcdedit.png)

Establish connection
```
a.  Restart Win7
b.  Boot and choose to boot with debugger option enabled
c.  Check WinDBG 
```

![windows_boot_debugger](/assets/windows_boot_debugger.png)

![win10_windbg_established](/assets/win10_windbg_established.png)

Debug & Breakpoint

![win10_windbg_debugging](/assets/win10_windbg_debugging.png)

Great, ready to go!

### Debugging

Show all processes

![windbg_process](/assets/windbg_process.png)